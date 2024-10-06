# ElasticSearch Installation

## Step 1: Update System Packages
Open a terminal and update your package index:

```bash
sudo apt update
sudo apt upgrade
```

## Step 2: Install Java (Elasticsearch requires Java)
Elasticsearch requires Java. Install OpenJDK 11 by running:

```bash
sudo apt install openjdk-11-jdk
```

Verify the installation:

```bash
java -version
```

It should output something like openjdk version "11.x.x".


## Step 3: Add the Elasticsearch APT Repository
1. Import the Elasticsearch public GPG key:
```bash
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```

2. Add the Elasticsearch repository:

```bash
sudo sh -c 'echo "deb https://artifacts.elastic.co/packages/8.x/apt stable main" > /etc/apt/sources.list.d/elastic-8.x.list'
```

## Step 4: Install Elasticsearch
Now install Elasticsearch:

```bash
sudo apt update
sudo apt install elasticsearch
```
# Step 5: Configure Elasticsearch
Elasticsearch is installed but not yet running. You need to configure it before starting.

1. Open the Elasticsearch configuration file:

```bash
sudo nano /etc/elasticsearch/elasticsearch.yml
```

2. Here are a few important configuration options you can adjust:

    - Cluster name: Set the name of the cluster.
    - Node name: Set the node's name.
    - Network: By default, Elasticsearch listens on localhost. To make it accessible from other devices, change:

    ```bash
    network.host: 0.0.0.0
    ```
    - Port: Default is 9200. Change if needed.

3. Save and close the file.

## Step 6: Start and Enable Elasticsearch

Start the Elasticsearch service:
```bash
sudo systemctl start elasticsearch
```

Enable Elasticsearch to start automatically on boot:
```bash
sudo systemctl enable elasticsearch
```

## Step 7: Verify Elasticsearch is Running
Check the status:
```bash
sudo systemctl status elasticsearch
```
