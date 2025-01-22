# Setting up a dev container for Rust

* Primary author: [Nandan Mogili](https://github.com/nandanmogili)

# Setting Up a Basic Rust Project from Scratch

Welcome to this comprehensive guide on setting up a basic Rust project from scratch. Whether you're new to Rust or looking to refresh your skills, this tutorial will walk you through the essential steps to get your Rust environment up and running.

## 📋 Prerequisites

Before diving into the setup, ensure you have the following installed on your machine:

- **[Rust](https://www.rust-lang.org/tools/install)**: The programming language we'll be using.
- **[Visual Studio Code (VS Code)](https://code.visualstudio.com/)**: A versatile code editor.
- **[Git](https://git-scm.com/downloads)**: Version control system (optional but recommended).

> **Note:** This tutorial assumes you're using a Unix-like operating system (Linux or macOS). Windows users can follow similar steps using tools like [PowerShell](https://docs.microsoft.com/en-us/powershell/) or [WSL](https://docs.microsoft.com/en-us/windows/wsl/install).

## 🚀 Step 1: Install Rust

Rust provides an official installer called `rustup` that manages Rust versions and associated tools.

1. **Run the Installer:**

   Open your terminal and execute the following command:

   ```bash
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
