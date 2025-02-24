# Installing the node

The `exrpd` binary is the primary software component for running XRPL EVM nodes. By installing and configuring `exrpd`, you will be able to join the network, synchronize with the blockchain, and participate in consensus (if you are a validator). The following steps will guide you through the installation process.

## Installation Methods

There are multiple ways to install the `exrpd` binary on your system. Choose the method that best suits your requirements and expertise.

Below is a complete documentation for installing the node by downloading raw binaries:

Below is the updated installation documentation with the requested changes. It now specifies that you should download the binary from the repository's latest release and includes guidance (using Readocly-style tags) so you can choose the appropriate binary for your machine.

---

## Method 1: Downloading Raw Binaries

This method involves downloading precompiled binaries from the repository's latest release and running them on your system. It’s quick to set up and requires minimal prerequisites.

### Pre-requisites

- **None:** Just ensure your system meets the hardware requirements.

### Steps

1. **Download the Latest Binaries:**  
   Visit the [official repository's releases page](https://github.com/xrplevm/node/releases) and download the binary that corresponds to your operating system and architecture. You can use `wget` (or `curl` for Windows) to download the file directly from the command line.

   {% tabs %}
   {% tab label="Linux" %}
   **For Linux Users:**

   - **AMD64:**  
     ```bash
     wget https://github.com/xrplevm/node/releases/download/v6.0.0/node_6.0.0_Linux_amd64.tar.gz
     ```
   - **ARM64:**  
     ```bash
     wget https://github.com/xrplevm/node/releases/download/v6.0.0/node_6.0.0_Linux_arm64.tar.gz
     ```
   {% /tab %}

   {% tab label="macOS" %}
   **For macOS Users:**

   - **Intel (x86_64):**  
     ```bash
     wget https://github.com/xrplevm/node/releases/download/v6.0.0/node_6.0.0_Darwin_amd64.tar.gz
     ```
   - **Apple Silicon (ARM64):**  
     ```bash
     wget https://github.com/xrplevm/node/releases/download/v6.0.0/node_6.0.0_Darwin_arm64.tar.gz
     ```
   {% /tab %}
   
   {% tab label="Windows" %}
   **For Windows Users:**

   Windows doesn't include `wget` by default. Instead, you can use `curl` (available in Windows 10 and later) to download the file:
   
   - **Download using curl:**  
     Open PowerShell and run:
     ```powershell
     curl -LO https://github.com/xrplevm/node/releases/download/v6.0.0/node_6.0.0_Windows_amd64.zip
     ```
   {% /tab %}
   {% /tabs %}

2. **Extract the Binaries:**  
   Once downloaded, extract the file using the appropriate command for your platform. For example, on Linux:
   ```bash
   tar -xzf node_6.0.0_Linux_amd64.tar.gz
   ```
   This will extract the files into a directory.

3. **Move the Binaries:**  
   Move the extracted files (especially the `exrpd` binary) to your preferred directory. For instance, to place it in `/usr/local/bin` (which is typically in your PATH), run:
   ```bash
   sudo mv /root/bin/exrpd /usr/local/bin/
   ```

4. **Make the Binary Executable:**  
   Ensure the binary has executable permissions:
   ```bash
   chmod +x /usr/local/bin/exrpd
   ```
      - The **exrpd binary** is now located in `/usr/local/bin/exrpd` (if you followed the installation steps).
   - When you run `exrpd` from the terminal, your system finds it in `/usr/local/bin`.

   You can verify its location by running:
   ```bash
   which exrpd
   ```

   Additionally, once you start your node, configuration files (if created) will be placed in your home directory under `~/.exrpd`.

5. **Verify the Installation:**  
   Check that the binary is accessible and working by running:
   ```bash
   exrpd version
   ```
   You should see version information (e.g., `v6.0.0`).

6. **Configure and Run Your Node (Optional):**  
   Once the binary is installed, follow the [node configuration instructions](./join-the-xrplevm.md)


Using this method, you can quickly set up your node by downloading the latest release from the repository, and the Machine Selector tags will help you choose the correct binary for your operating system and architecture.

---

Below is the updated documentation for Methods 2 and 3, now including machine-specific tabs and additional details for Docker regarding optional API/RPC port exposure. For more details on configuration options, please refer to the [Node Configuration Options](../resources/configuration-reference.md) documentation.

---

## Method 2: Building from Source

This method involves cloning the source code repository and building the binaries from source. It is ideal for developers who want to customize the node.

### Pre-requisites

- `go v1.23.4`, `make` and `gcc` installed.

#### Install Dependencies for Building from Source

{% tabs %}
{% tab label="Linux" %}
Install **make** and **gcc**:
```bash
sudo apt-get update
sudo apt-get install build-essential
```
Install **Go v1.23.4**:
```bash
sudo rm -rf /usr/local/go
wget https://go.dev/dl/go1.23.4.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.23.4.linux-amd64.tar.gz
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.profile
source ~/.profile
go version
```
{% /tab %}
{% tab label="macOS" %}
Install Xcode Command Line Tools (includes **make** and **gcc**):
```bash
xcode-select --install
```
Install **Go v1.23.4** using Homebrew:
```bash
brew uninstall go
brew install go@1.23.4
```
Ensure the correct Go binary is in your PATH:
```bash
export PATH="/usr/local/opt/go@1.23.4/bin:$PATH"
go version
```
{% /tab %}
{% tab label="Windows" %}
**Note:** Building from source on Windows directly can be challenging due to the lack of native support for `make` and `gcc`. It is recommended to use [Windows Subsystem for Linux (WSL)](https://docs.microsoft.com/en-us/windows/wsl/install) and then follow the Linux instructions.
{% /tab %}
{% /tabs %}

### Steps to Build the Node

1. **Clone the repository:**
   ```bash
   git clone https://github.com/xrplevm/node.git
   ```
2. **Navigate to the project directory:**
   ```bash
   cd node
   ```
3. **Build the project:**
   ```bash
   make build
   ```
4. **Locate the Binaries:**  
   The compiled binaries will be available in the `build` directory.

---

## Method 3: Using Docker

A containerized approach ensures that the node runs in a consistent environment, avoiding dependency issues. This method is highly recommended if you prefer a ready-to-run environment.

### Pre-requisites

- [Docker 19+ installed](https://docs.docker.com/engine/install/).

### Steps to Run the Node via Docker

{% tabs %}
{% tab label="Linux" %}
1. **Pull the Docker image:**
   ```bash
   docker pull peersyst/exrp:latest
   ```
2. **Run the Docker container:**  
   This command mounts your configuration directory and maps the necessary ports. You can optionally expose additional ports for API and RPC endpoints (see [Node Configuration Options](../resources/configuration-reference.md)):
   ```bash
   docker run -d --name xrplevm-node \
     -v /home/xrplevmuser/.exrpd:/root/.exrpd \
     -p 26656:26656 -p 26657:26657 \
     -p 8545:8545 -p 8546:8546 \
     -e DAEMON_NAME=exrpd \
     -e DAEMON_HOME=/root/.exrpd \
     peersyst/exrp-cosmovisor:latest
   ```
{% /tab %}
{% tab label="macOS" %}
1. **Pull the Docker image:**
   ```bash
   docker pull peersyst/exrp:latest
   ```
2. **Run the Docker container:**  
   Replace `<your-username>` with your macOS username. This command mounts your configuration directory and maps the necessary ports. Optionally, expose additional ports as needed:
   ```bash
   docker run -d --name xrplevm-node \
     -v /Users/<your-username>/.exrpd:/root/.exrpd \
     -p 26656:26656 -p 26657:26657 \
     -p 8545:8545 -p 8546:8546 \
     -e DAEMON_NAME=exrpd \
     -e DAEMON_HOME=/root/.exrpd \
     peersyst/exrp-cosmovisor:latest
   ```
{% /tab %}
{% tab label="Windows" %}
1. **Pull the Docker image** (using Docker Desktop):
   ```powershell
   docker pull peersyst/exrp:latest
   ```
2. **Run the Docker container:**  
   Replace `<your-username>` with your Windows username. This command mounts your configuration directory and maps the necessary ports. Optionally, expose additional ports for API and RPC endpoints:
   ```powershell
   docker run -d --name xrplevm-node `
     -v C:\Users\<your-username>\.exrpd:/root/.exrpd `
     -p 26656:26656 -p 26657:26657 `
     -p 8545:8545 -p 8546:8546 `
     -e DAEMON_NAME=exrpd `
     -e DAEMON_HOME=/root/.exrpd `
     peersyst/exrp-cosmovisor:latest
   ```
{% /tab %}
{% /tabs %}

> **Note:** On Docker, you can optionally expose additional ports for API and RPC endpoints (e.g., Cosmos gRPC, Cosmos RPC, Tendermint RPC, Ethereum JSON-RPC/WS). For further details on configuring these endpoints, see the [Node Configuration Options](../resources/configuration-reference.md) documentation.

Finally, to verify that your container is running, execute:

```bash
docker ps -a
```
You should see something like this:
```bash
CONTAINER ID   IMAGE                             COMMAND        CREATED         STATUS                     PORTS     NAMES
931778c24bdc   peersyst/exrp-cosmovisor:latest   "cosmovisor"   2 minutes ago   Exited (0) 2 minutes ago             xrplevm-node

```

---