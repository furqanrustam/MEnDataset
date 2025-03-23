# MEnDataset


https://www.kaggle.com/datasets/furqanrustam118/men-dataset/

# Phase 1: Data Collection

We construct a comprehensive dataset encompassing benign and malicious traffic from both traditional (non-IoT) and IoT network environments. To achieve this, we employ a two-part strategy.

**Part 1: DDoShield-IoT Testbed**
We utilize the DDoShield-IoT testbed 1, which integrates Docker containers with NS-3 network simulations. This testbed simulates realistic network conditions by running real binaries within Docker containers over an emulated network topology, enabling the generation of authentic network traffic.

- Benign Traditional Traffic: FTP, HTTP, RTMP streaming

* Malicious IoT Traffic: Generated using Mirai malware binaries

**Part 2: External Dataset Integration**
Since DDoShield-IoT does not support benign IoT traffic or malicious traditional traffic, we integrate validated external PCAP datasets:

- Benign IoT Traffic: MQTT-IoT-IDS2020 dataset

* Malicious Traditional Traffic: CIC DDoS 2019 dataset

**Dataset Merging and Labeling**
To merge all traffic sources, we employ a Python script running inside a Docker container node (configured in promiscuous mode) within the DDoShield-IoT simulation. This script captures:

- Live traffic from DDoShield-IoT

* Randomly sampled packets from external PCAPs

+ All packets, regardless of their origin, are processed uniformly.

**Traffic Labeling**
- Traffic is labeled using known ground truths:

* DDoShield-IoT Traffic: Labeled based on simulation settings

+ External Datasets: Include validated labels from literature

To ensure comparability across traffic types, all packets undergo identical feature extraction procedures (detailed in Phase 2: Feature Extraction). This creates a uniform and unbiased dataset representing realistic M-En (Multi-Environment Network) conditions.

