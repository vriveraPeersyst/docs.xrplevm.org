# Installing the node

The `exrpd` binary is the primary software component for running XRPL EVM nodes. By installing and configuring `exrpd`, you will be able to join the network, synchronize with the blockchain, and participate in consensus (if you are a validator). The following steps will guide you through the installation process.

## Installation Methods

There are multiple ways to install the `exrpd` binary on your system. Choose the method that best suits your requirements and expertise.

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
     wget https://github.com/xrplevm/node/releases/download/v7.0.0/node_7.0.0_Linux_amd64.tar.gz
     ```
   - **ARM64:**  
     ```bash
     wget https://github.com/xrplevm/node/releases/download/v7.0.0/node_7.0.0_Linux_arm64.tar.gz
     ```
   {% /tab %}

   {% tab label="macOS" %}
   **For macOS Users:**

   - **Intel (x86_64):**  
     ```bash
     wget https://github.com/xrplevm/node/releases/download/v7.0.0/node_7.0.0_Darwin_amd64.tar.gz
     ```
   - **Apple Silicon (ARM64):**  
     ```bash
     wget https://github.com/xrplevm/node/releases/download/v7.0.0/node_7.0.0_Darwin_arm64.tar.gz
     ```
   {% /tab %}
   
   {% tab label="Windows" %}
   **For Windows Users:**

   Windows doesn't include `wget` by default. Instead, you can use `curl` (available in Windows 10 and later) to download the file:
   
   - **Download using curl:**  
     Open PowerShell and run:
     ```powershell
     curl -LO https://github.com/xrplevm/node/releases/download/v7.0.0/node_7.0.0_Windows_amd64.zip
     ```
   {% /tab %}
   {% /tabs %}

2. **Extract the Binaries:**  
   Once downloaded, extract the file using the appropriate command for your platform. For example, on Linux:
   ```bash
   tar -xzf node_7.0.0_Linux_amd64.tar.gz
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
   You should see version information (e.g., `v7.0.0`).

6. **Configure and Run Your Node (Optional):**  
   Once the binary is installed, follow the [node configuration instructions](./join-the-xrplevm.md)


Using this method, you can quickly set up your node by downloading the latest release from the [repository](https://github.com/xrplevm/node/releases).

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
Here’s the updated **Method 3: Using Docker** guide—tested on Linux, macOS & Windows—with **v6.0.0** and the correct `--entrypoint` override so that `exrpd start` actually runs:

---
## Method 3: Using Docker

A containerized approach ensures a consistent environment and avoids host-dependency issues. With version **v6.0.0**, you only need **two** Docker commands:

---

### Prerequisites

* Docker 19+ installed on your host.
* Run as root (or via sudo) so that `/root/.exrpd` is writable.

---

### 1. Interactive setup (one-time)

Launch a shell in the container, mounting your host’s config directory. Inside, run **all** of the “Join the XRPL EVM” commands (chain-ID, keygen, init, genesis download, seed configuration, etc.) as per the Testnet (or Devnet) guide—then exit when done.

```bash
docker run -it --name xrplevm-setup \
  -v /root/.exrpd:/root/.exrpd \
  peersyst/exrp:v6.0.0 \
  /bin/sh
```

*(Inside that shell, complete the join-the-xrplevm steps from the docs, then `exit`.)*

---

### 2. Detached, auto-restarting run

Now start your fully-configured node in the background. The `--entrypoint` override ensures that `exrpd start` actually runs:

```bash
docker run -d \
  --restart unless-stopped \
  --name xrplevm-node \
  -v /root/.exrpd:/root/.exrpd \
  --entrypoint exrpd \
  peersyst/exrp:v6.0.0 \
  start
```

---

### Verification

```bash
docker ps | grep xrplevm-node
docker logs -f xrplevm-node
```

You should see your node’s Tendermint/exrpd startup logs and syncing progress.

### Upgrade the node

To upgrade your running XRPL EVM node from v6.0.0 to v7.0.0 in Docker, you just need to pull the new image, stop & remove the old container, and re-run it with the same volume mount. Here’s a concise step‐by‐step:

1. **Pull the v7.0.0 image**

   ```bash
   docker pull peersyst/exrp:v7.0.0
   ```

2. **Stop and remove your old container**

   ```bash
   docker stop xrplevm-node
   docker rm xrplevm-node
   ```

3. **Run the container with the new tag**

   ```bash
   docker run -d \
     --restart unless-stopped \
     --name xrplevm-node \
     -v /root/.exrpd:/root/.exrpd \
     --entrypoint exrpd \
     peersyst/exrp:v7.0.0 \
     start
   ```

   * You’re re-using the same `/root/.exrpd` data directory, so your ledger state stays intact.
   * The `--entrypoint exrpd … start` invocation is exactly the same as before, just pointing to the new image.

4. **Verify it’s running and has upgraded**

   ```bash
   docker logs -f --tail 50 xrplevm-node
   ```

   You should no longer see the `UPGRADE "v7.0.0" NEEDED at height` error and your node will proceed to sync/replay under the new binary.

---

### If you’re using Docker Compose

If you prefer `docker-compose.yml`, just change the image tag and do a `docker-compose up -d`:

```yaml
version: '3.8'
services:
  xrplevm-node:
    image: peersyst/exrp:v7.0.0
    container_name: xrplevm-node
    entrypoint: ["exrpd", "start"]
    restart: unless-stopped
    volumes:
      - /root/.exrpd:/root/.exrpd
```

Then:

```bash
docker-compose pull xrplevm-node
docker-compose up -d xrplevm-node
```

That’s it—your node will now run v7.0.0 and continue syncing from height 547100 onward.

Do the same with v8.0.0 and future versions.

