# Setting up a Dev Container for Rust
* Primary author: [Nandan Mogili](https://github.com/nandanmogili)
* Reviewer: [<Aaron Patel>](https://github.com/arpatell)



Welcome to this step-by-step guide on setting up a basic **Rust** project from scratch. Whether you’re a complete beginner or looking to structure your environment more efficiently, this tutorial will walk you through every essential step—from creating a Git repository to compiling and running a _Hello World_ example.

---

1. [Introduction](#introduction)  
2. [Prerequisites](#prerequisites)  
3. [Git Repository Setup](#git-repository-setup)  
4. [Dev Container Setup](#dev-container-setup)  
5. [Initialize a Rust Project](#initialize-a-rust-project)  
6. [Add a Hello World Example](#add-a-hello-world-example)  
7. [Compile and Run](#compile-and-run)  


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

Version control is essential for managing changes to your project’s codebase. Let’s start by creating a Git repository.

1. **Create a new directory:**

    ```bash
    mkdir rust-project
    cd rust-project
    ```

2. **Initialize the repository:**

    ```bash
    git init
    ```

3. **Create a `.gitignore` file:**  
   Exclude files and directories you don’t want under source control:

    ```bash
    echo "/target\n**/*.rs.bk\n.vscode\n*.code-workspace\n.DS_Store" > .gitignore
    ```

4. **Commit the setup:**

    ```bash
    git add .
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

    ```bash
    mkdir .devcontainer
    cd .devcontainer
    ```

3. **Add `devcontainer.json`:**  
   This file tells VS Code how to configure and launch your container.

    ```json
    {
      "name": "Rust Dev Container",
      "image": "rust:latest",
      "extensions": [
        "rust-lang.rust-analyzer",
        "ms-vscode.cpptools"
      ],
      "settings": {
        "terminal.integrated.shell.linux": "/bin/bash"
      },
      "postCreateCommand": "rustup component add rustfmt clippy"
    }
    ```

4. **Reopen project in container:**  
   - Press <kbd>F1</kbd> in VS Code  
   - Type `Remote-Containers: Reopen in Container`  
   - Wait for the container to build  

---

## Initialize a Rust Project

Once your container is running (or if you’re skipping the container step, on your local machine):

1. **Initialize a Cargo project:**

    ```bash
    cargo new hello_rust
    cd hello_rust
    ```

2. **Project structure overview:**  
   - **Cargo.toml** – project configuration  
   - **src/main.rs** – entry point for your Rust code  

3. **Commit the new project:**

    ```bash
    git add .
    git commit -m "Initialize Rust project using Cargo"
    ```

---

## Add a Hello World Example

Let’s create a basic _Hello World_ program to test the setup.

1. **Open `src/main.rs`:**

    ```rust
    fn main() {
        println!("Hello, World!");
    }
    ```

2. **Format and lint code (optional but recommended):**

    ```bash
    cargo fmt
    cargo clippy
    ```

3. **Commit changes:**

    ```bash
    git add src/main.rs
    git commit -m "Add Hello World example"
    ```

---

## Compile and Run

Time for the exciting part—building and running your Rust code.

1. **Compile the project:**

    ```bash
    cargo build
    ```



2. **Run the project:**

    ```bash
    cargo run
    ```

    **Expected output:**

    ```
    Compiling hello_rust v0.1.0 (/workspaces/rust-project/hello_rust)
     Finished dev [unoptimized + debuginfo] target(s) in 2.34s
      Running `target/debug/hello_rust`
    Hello, World!
    ```

3. **Verify success:**  
   You should see **Hello, World!** in your terminal.

---