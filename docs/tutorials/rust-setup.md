# Setting up a Dev Container for Rust

* Primary author: [Nandan Mogili](https://github.com/nandanmogili)


Welcome to this tutorial on setting up a basic Rust project from scratch. Whether you're new to Rust or looking to refresh your setup process, this guide will walk you through each step to get your development environment up and running efficiently.

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [1. Git Repository Setup](#1-git-repository-setup)
4. [2. Dev Container Setup](#2-dev-container-setup)
5. [3. Initialize a Rust Project](#3-initialize-a-rust-project)
6. [4. Add a Hello World Example](#4-add-a-hello-world-example)
7. [5. Compile and Run](#5-compile-and-run)
8. [Conclusion](#conclusion)

---

## Introduction

Rust is a systems programming language known for its performance, reliability, and memory safety. Setting up a Rust project involves configuring your development environment, initializing a new project, and writing your first program. This tutorial covers the essential steps to help you get started quickly.

## Prerequisites

Before diving into the setup, ensure you have the following installed on your machine:

- **Git**: Version control system.
- **Visual Studio Code (VS Code)**: A popular code editor.
- **Docker**: For setting up development containers.
- **Rust**: The Rust programming language and Cargo package manager.

If you haven't installed these tools yet, please refer to their official installation guides:

- [Git Installation](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [VS Code Installation](https://code.visualstudio.com/docs/setup/setup-overview)
- [Docker Installation](https://docs.docker.com/get-docker/)
- [Rust Installation](https://www.rust-lang.org/tools/install)

---

## 1. Git Repository Setup

Setting up a Git repository allows you to track changes, collaborate with others, and maintain version control for your project.

### Steps:

1. **Create a New Directory for Your Project:**

    ```bash
    mkdir rust-hello-world
    cd rust-hello-world
    ```

2. **Initialize Git Repository:**

    ```bash
    git init
    ```

3. **Create a `.gitignore` File:**

    It's good practice to exclude certain files and directories from version control. Create a `.gitignore` file with the following content:

    ```gitignore
    # Rust/Cargo
    /target
    **/*.rs.bk

    # IDEs
    .vscode/
    *.code-workspace

    # OS Files
    .DS_Store
    ```

    ```bash
    echo "/target\n**/*.rs.bk\n.vscode/\n*.code-workspace\n.DS_Store" > .gitignore
    ```

4. **Commit Initial Setup:**

    ```bash
    git add .
    git commit -m "Initial Git repository setup with .gitignore"
    ```

---

## 2. Dev Container Setup

Using a development container ensures a consistent development environment across different machines, making collaboration smoother.

### Steps:

1. **Install the Remote - Containers Extension in VS Code:**

    - Open VS Code.
    - Go to the Extensions view (`Ctrl+Shift+X` or `Cmd+Shift+X`).
    - Search for "Remote - Containers" and install it.

2. **Create a `.devcontainer` Directory:**

    ```bash
    mkdir .devcontainer
    cd .devcontainer
    ```

3. **Create a `devcontainer.json` File:**

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

    ```bash
    cat > devcontainer.json <<EOL
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
    EOL
    ```

4. **Reopen the Project in the Dev Container:**

    - Press `F1` in VS Code.
    - Type `Remote-Containers: Reopen in Container` and select it.
    - Wait for the container to build and open.

---

## 3. Initialize a Rust Project

With your environment set up, it's time to initialize a new Rust project using Cargo, Rust's package manager and build system.

### Steps:

1. **Initialize a New Cargo Project:**

    ```bash
    cargo new hello_world
    cd hello_world
    ```

    This command creates a new directory `hello_world` with the basic structure of a Rust project.

2. **Explore the Project Structure:**

    - `Cargo.toml`: Configuration file for your project.
    - `src/main.rs`: The main source file.

3. **Commit the Initialized Project:**

    ```bash
    git add .
    git commit -m "Initialize new Rust project with Cargo"
    ```

---

## 4. Add a Hello World Example

Let's create a simple "Hello, World!" program to verify that everything is set up correctly.

### Steps:

1. **Open `src/main.rs` in VS Code:**

    ```rust
    fn main() {
        println!("Hello, World!");
    }
    ```

    Replace the existing content with the above code if it's not already there.

2. **Format the Code (Optional):**

    Rust provides a tool called `rustfmt` to format your code consistently.

    ```bash
    cargo fmt
    ```

3. **Lint the Code (Optional):**

    Use `clippy` to catch common mistakes and improve your code.

    ```bash
    cargo clippy
    ```

4. **Commit the Hello World Example:**

    ```bash
    git add src/main.rs
    git commit -m "Add Hello, World! example"
    ```

---

## 5. Compile and Run

Now, let's compile and run your Rust program to see it in action.

### Steps:

1. **Compile the Project:**

    ```bash
    cargo build
    ```

    This command compiles your project and generates an executable in the `target/debug` directory.

2. **Run the Project:**

    ```bash
    cargo run
    ```

    **Expected Output:**

    ```
    Compiling hello_world v0.1.0 (/path/to/your/project/hello_world)
     Finished dev [unoptimized + debuginfo] target(s) in 2.34s
      Running `target/debug/hello_world`
    Hello, World!
    ```

3. **Verify the Output:**

    You should see the message `Hello, World!` printed in your terminal, confirming that your Rust project is set up correctly.

---

## Conclusion

Congratulations! You've successfully set up a basic Rust project from scratch. Here's a quick recap of what you've accomplished:

- **Git Repository Setup:** Initialized version control to manage your project's history.
- **Dev Container Setup:** Configured a consistent development environment using Docker and VS Code.
- **Initialize a Rust Project:** Created a new Rust project using Cargo.
- **Add a Hello World Example:** Wrote a simple Rust program to verify your setup.
- **Compile and Run:** Built and executed your Rust program successfully.

With this foundation, you're now ready to delve deeper into Rust programming. Explore more complex projects, integrate additional libraries, and continue building your skills. Happy coding!

---

> **Tip:** As you advance, consider exploring Rust's powerful features such as ownership, lifetimes, and concurrency to harness the full potential of the language.

