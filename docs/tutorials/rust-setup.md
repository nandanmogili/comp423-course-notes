# Setting up a Dev Container for Rust

* Primary author: [Nandan Mogili](https://github.com/nandanmogili)  
* Reviewer: [Aaron Patel](https://github.com/arpatell)

Welcome to this step-by-step guide on setting up a basic **Rust** project from scratch. Whether you’re a complete beginner or looking to structure your environment more efficiently, this tutorial will walk you through every essential step—from creating a Git repository to compiling and running a _Hello World_ example.

---

1. [Introduction](#introduction)  
2. [Prerequisites](#prerequisites)  
3. [Git Repository Setup](#git-repository-setup)  
4. [Dev Container Setup](#dev-container-setup)  
5. [Verify Rust Version](#verify-rust-version)  
6. [Initialize a Rust Project](#initialize-a-rust-project)  
7. [Add a Hello World Example](#add-a-hello-world-example)  
8. [Compile and Run](#compile-and-run)  

---

## Introduction

Rust is a modern systems programming language designed for speed, safety, and concurrency. By following this guide, you’ll learn how to:

- Set up a Git repo for version control  
- Configure a development container using Docker and VS Code  
- Initialize a new Rust project  
- Add and run a simple _Hello World_ program  

---

## Prerequisites

Before you begin, make sure you have the following:

1. **Git** – for version control  
2. **Visual Studio Code (VS Code)** – a code editor with Dev Container support  
3. **Docker** – to run your Dev Container  
4. **Rust** – the Rust toolchain, including Cargo  

[VS Code Installation](https://code.visualstudio.com/docs/setup/setup-overview)  
[Docker Installation](https://docs.docker.com/get-docker/)  
[Rust Installation](https://www.rust-lang.org/tools/install)

---

## Git Repository Setup

Version control is essential for managing changes to your project’s codebase. Let’s start by creating a Git repository:




1. **Create a new directory:**

    ```
    mkdir rust-project
    ```

    ```
    cd rust-project
    ```

2. **Initialize the repository:**

    ```
    git init
    ```

3. **Create a `.gitignore` file:**  
   Exclude files and directories you don’t want under source control:

    ```
    echo "/target\n**/*.rs.bk\n.vscode\n*.code-workspace\n.DS_Store" > .gitignore
    ```

4. **Commit the setup:**

    ```
    git add .
    ```

    ```
    git commit -m "Initial commit: setup Git repository with .gitignore"
    ```


---

## Dev Container Setup

A *development container* ensures a consistent environment for your project, regardless of the host machine. In VS Code, we can use the **Remote - Containers** extension to manage this.

1. **Install the Remote - Containers extension:**
   - Open VS Code  
   - Go to Extensions (View → Extensions or <kbd>Ctrl+Shift+X</kbd>/<kbd>Cmd+Shift+X</kbd>)  
   - Search for “Remote - Containers” and install it  

2. **Create a `.devcontainer` folder:**

    ```
    mkdir .devcontainer
    cd .devcontainer
    ```

3. **Add `devcontainer.json`:**  
   This file tells VS Code how to configure and launch your container. Notice we are using a *Microsoft*-provided base image.

    
    ```
    {
      "name": "Rust Dev Container",
      "image": "mcr.microsoft.com/devcontainers/rust:latest",
      "extensions": [
        "rust-lang.rust-analyzer"
      ],
      "settings": {
        "terminal.integrated.shell.linux": "/bin/bash"
      }
    }
    ```

4. **Reopen project in container:**  
   - Press <kbd>F1</kbd> or <kbd>Shift</kbd> <kbd>Command</kbd> <kbd>P</kbd> in VS Code  
   - Type `Remote-Containers: Reopen in Container`  
   - Wait for the container to build  

Once the container is up and running, you should have a consistent Rust environment inside VS Code.

---

## Initialize a Rust Project

**Verify your Rust Version**

After your Dev Container is running—or if you’re on a local machine—verify the Rust toolchain:

```
rustc --version
```

**Create a new Rust Project**

With your environment set up, it's time to create a new Rust project. We'll use Cargo, Rust's package manager and build system, to initialize the project without setting up a Git repository automatically.

```
cargo new rust-project --vcs none
```
```
cd rust-project
```

## Hello World Example 

Navigate to the **src** directory:
```
cd src
```
Open **main.rs** in your code editor and replace its contents with the following:
```
fn main() {
    println!("Hello, world!");
}
```


**Compile and Run:**

Use **cargo build** and **cargo run** to compile and run your Rust Project and you should see the expected output : Hello world!

```
cargo build
```

```
cargo run
```

Congratulations! You’ve successfully set up a Rust development environment using a Dev Container, initialized a Git repository, created a new Rust project, and run your first Rust program.