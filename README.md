# 💡 Network Behavior Analysis using K-Means Clustering

This project implements an **unsupervised anomaly detection system** for network traffic using the **K-Means clustering algorithm**. The system establishes a baseline of "normal" network activity by grouping traffic flows into clusters and flags any new traffic that deviates significantly from these learned clusters as an **anomaly**.

---

## 💻 Proposed System Overview (Functional Requirements)

The system is designed to model normal network behavior and detect deviations:

1.  **Data Collection:** Collect raw network traffic logs (Source IP, Destination IP, Bytes, Packets, Duration).
2.  **Feature Engineering:** Convert raw data into **numeric feature vectors** (e.g., Total Bytes, Total Packets, Failed Connections, Unique Destinations).
3.  **Clustering (Training):** Apply **K-Means** to group the feature vectors into $K$ clusters.
4.  **Anomaly Threshold:** Calculate the **centroid** (average point) and define a **distance threshold** for each cluster. Traffic within this distance is normal.
5.  **Detection (Testing):** For new traffic, classify it:
    * **Normal:** If the traffic point falls **within** its nearest cluster's threshold distance.
    * **Anomaly:** If the traffic point falls **outside** its nearest cluster's threshold distance.

---

## 📊 Dataset Usage

The system requires network flow data, preferably in a structured format (CSV, JSON, etc.).

### **Required Features (Raw Log):**

| Feature | Description |
| :--- | :--- |
| **Source IP** | IP address initiating the connection. |
| **Destination IP** | IP address receiving the connection. |
| **Bytes** | Total number of bytes transferred. |
| **Packets** | Total number of packets transferred. |
| **Duration** | Length of the connection/flow in seconds. |

### **Engineered Features (Model Input):**

The raw logs must be processed to generate numeric features for clustering:

* **Total\_Bytes**
* **Total\_Packets**
* **Failed\_Connections** (Count of connections with abnormal termination)
* **Unique\_Destinations** (Count of distinct destination IPs contacted by a source IP)

### **Potential Datasets:**

* **CIC-IDS 2017/2018:** Modern datasets containing various types of attacks and benign traffic.
* **NSL-KDD / KDD Cup 99:** Historical datasets often used for benchmarking network intrusion detection.
* **Custom PCAP/Flow Data:** Data captured directly from a network interface (e.g., using Wireshark or tshark) and converted into flow logs.

---

## 🛠️ Technologies Usage

This project is typically implemented using a Python-based machine learning stack.

### **Programming Language:**

* **Python 3.x:** Primary language for scripting and model development.

### **Key Libraries/Frameworks:**

| Category | Technology | Purpose |
| :--- | :--- | :--- |
| **Data Handling** | **Pandas** | Reading, cleaning, and manipulating the network log data. |
| **Numerical Operations**| **NumPy** | High-performance array operations and distance calculations. |
| **Machine Learning**| **Scikit-learn (sklearn)** | Implementation of the **K-Means** clustering algorithm and feature scaling (`StandardScaler`). |
| **Visualization** | **Matplotlib / Seaborn** | Visualizing cluster distributions, centroids, and anomaly points. |

---

## 🚀 Getting Started

1.  **Clone the Repository:**
    ```bash
    git clone [Your-Repo-URL]
    cd network-behavior-analysis
    ```
2.  **Install Dependencies:**
    ```bash
    pip install pandas numpy scikit-learn matplotlib
    # Or using a dedicated requirements file:
    # pip install -r requirements.txt
    ```
3.  **Prepare Data:** Ensure your processed network data (e.g., `traffic_data.csv`) is ready for input.
4.  **Run the Analysis Script:** Execute the main script, defining the key K-Means parameters.
    ```bash
    python run_analysis.py --k [Number-of-Clusters] --threshold [Distance-Multiplier]
    ```
# 👨‍💻 Author

**E R Guruvishnukumar**
