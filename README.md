# Ransomware-Detection-Agent
#Week 5

24-9-2025

Paper 1:  CINN-UTLC: A Computationally Intelligent Neural Network-Based Unsupervised  Transfer.



How does the attack happen:

Initial entry: clicking a link or opening an infected file or by phishing or exploiting vulnerability in a program.

 Running the software inside the device: ransomware begins to run, sometimes from a regular file, sometimes without a file using system tools

Runtime behavior: it begins to process many files quickly, opening, modifying, and writing, and uses encryption features (putting file data in an encrypted format). It may change system settings to prevent file recovery.

Encryption and ransom: it locks files and demands money in exchange for the decryption key. In some cases, it steals data before encryption and threatens to publish it.

Early signs that may indicate that an attack may happen:

Sudden increase in “random” files (entropy) – a sign of encryption.

The program calls lots of encryption functions in a short time

Rapid changes to many files’ names or extensions.

Attempts to disable backups and system restores.

Creating a mutex (lock) within the system to ensure it runs only once

If we noticed more than one of these signs, that may indicate that the system is being attacked by a Ransomware.


How do they usually defend 

They mix multiple methods like Static Analysis where they examine the file itself (its design, headers, and scripts), and Dynamic Analysis where they run the file in isolated environment and monitor it behavior, which functions it calls, and which files it changes, and AI where they use neural networks to teach the system to distinguish between malicious and real, as well as automatic clustering methods to detect new families of Ransomware.



Model used: 

CINN-UTLC	

C (CNN): A part that deals with the static content of the file itself, it captures the static patterns inside the file, the entropy.

L (LTSM): A part that deals with behavior during execution, it processes the sequence of system calls.

UT (Unsupervised Transfer): It uses a method that allows the model to learn from old or different data even if they do not have labels. This can help the model to discover new families of Ransomware without them being previously labeled.

LC (Learning + Clustering): It groups the samples into new clusters to identify similar families or raises an alert if it happens.

They basically combined file scanning, behavior monitoring, techniques for handling new data, and automatic collection to detect old or new ransomware without relying on a ready-made signature.

Statics:

Detection Rate: 98% approx.

False Positive Rate (FPR): 1-2.5% approx.


AUC (a general measure of discrimination quality): 0.92-0.94 meaning the model is excellent at distinguishing between malicious and non-malicious.

Novel families detection: 92-94% approx. which means that the model would be able to detect 92-94% of new types of Ransomwares, which is excellent because that is the goal of the Transfer + Clustering.

However, it is more difficult in reality, these numbers usually drop because the study works on specific data.

Suggestions:

Multi-stage System: On-device lightweight rules monitor simple signals, if suspicious, send the sample to the cloud or sandbox for deeper analysis to reduce false warnings and reduce the load.

Merge network and device signals: If the system sees cryptographic activity + suspicious outbound communications, send a threat warning.

Feedback from a SOC (Security Operation Center) analyst: Each alarm is tagged (true\false) so the system can continuously learn from it.

Diversify training data: Test the system on different training data to reduce bias.



	Paper 2: A novel technique for ransomware detection using image based dynamic features and transfer learning to address dataset limitations

-        Ransomware technique:
The attack starts simple. Ransomware hits a host. It runs, either as files or without them. Then it does a ton of reading, modifying, and writing on files. Uses encryption to lock everything up. Makes data useless. After that, it demands money. Often right after stealing stuff or threatening to leak it. Delivery ways from the paper's data. Phishing mostly. Exploit kits too. Compromised RDP sessions. Malware loaders like TrickBot or Emotet. RaaS affiliates dropping it. Families in the study use those. LockBit, Conti, REvil, Ryuk, you know the ones. Run-time details the paper tracks. Process creation and injection. File system changes. Registry tweaks. Network stuff, DNS and HTTP. Mutex creation. Deleting shadow copies and backups. Anti-VM tricks, anti-analysis moves. All that shows up in sandbox reports. Typical stages.
-        System changes when an attack occurs:
From the paper's dynamic features. You see these popping up quick. Multiple in a row. That means high suspicion. Pretty much what the authors used for behaviors. New files dropping fast. Lots of file mods. Feature is file_created. Counts those dropped ones. Big bursts of API calls for crypto stuff. Encryption patterns jumping out. Rapid renames, extension changes. Deleting shadow copies. Disabling backups. Registry writes for persistence. Or blocking recovery. Suspicious network outbound. DNS, HTTP requests tying to file crypto. Mutexes showing up. Anti-analysis flags, anti-VM ones.
-        Ransomware defence:
Dynamic analysis with sandboxing. Run suspect samples in a controlled spot. Cuckoo sandbox here. Capture those runtimes JSON reports on behavior, then behavior to image pipeline, plus transfer learning, authors take structured runtime features about 100 of them, turn into 2D images, a 10 by 10 grids, and use pretrained CNNs to spot ransomware versus benign, skips heavy manual feature work and, helps detection even with small data sets.
-        Features:
Best one is 99.96% accuracy on color images. 99.9% on grayscale.

-        Limitations and suggestions:
Limitations:
Dataset small still. Even with careful picks. Might miss real-world diversity in ransomware behaviors. Stuck on one sandbox, Cuckoo. Limits how general it is.
Suggestions:
Expand the dataset. More families. More benign types. More samples overall. Cuts overfitting. Boosts generalizability and use multiple analysis platforms.

References: 

Paper Name: CINN-UTLC: A Computationally Intelligent Neural Network-Based Unsupervised Transfer.
Year: 2025.
Access the paper here.

Paper Name: A novel technique for ransomware detection using image based dynamic features and transfer learning to address dataset limitations
Year: 2025
Access the paper here.






















#Week6 (Studying Ransomware detection in IoT)


Paper Name
Model
Dataset
Results
System
L-IDS: A Multi-Layered Approach to Ransomware Detection in IoT 

2024
Enter paper here.
L-IDS (Lightweight Intrusion Detection System)
Collected from multiple resources
Accuracy: 86.1%
Precision: 81.1%
Recall: 94.2%
F1 Score: 87.1
Linux (Raspberry Pi OS / Debian 11).



An intelligent ransomware based cyberthreat detection model using multi-head attention-based recurrent neural networks with optimization algorithm in IoT environment

2025
Enter paper here.
MHARNN-EGTOCRD (Multi-head Attention-Based Recurrent Neural Network with Enhanced Gorilla Troops Optimization for Cybersecurity Ransomware Detection).
Published and Ready-to-Use dataset
Accuracy: 98.53%
Sensitivity: 98.53%
Specificity: 98.53%
Not mentioned, mainly focused on (simulation + modeling).
Early prediction of ransomware API calls behaviour based on GRU-TCN in healthcare IoT



2023
Enter paper here.
EPS-Ran (Early Prediction Scheme of Ransomware behaviour)
11,700 file (PE format) 
5850 were Ransomware
5850 were benign
MAE = 0.3438
MSE = 0.5648
RMSE = 0.6342
It is characterized by its ability to predict early
Hardware: Intel Core i9-10800K + NVIDIA RTX 3090.
Software:
Ubuntu Server 18.04 (host).
Ubuntu 20.04 VM.
Windows 7 nested VM ( ransomware sandbox).






	
Limitations:

Although the three models demonstrated strong results in detecting ransomware attacks in IoT environments, there are several limitations to consider. The L-IDS (2024) paper suffers from lower accuracy compared to deep learning models. Furthermore, the dataset used is small (only 1,555 samples), and the reliance on signatures and entropy may fail against sophisticated attacks using evasion techniques. The MHARNN-EGTOCRD (2025) paper, while achieving high accuracy (98.53%), has a very small dataset (only 840 Kaggle records), which is not representative of the real world. Furthermore, the study did not test the model on actual IoT devices and did not discuss resource limitations (scalability).  The EPS-Ran (2023) paper is powerful in early prediction of ransomware behavior, but it relied on a complex sandbox environment (Ubuntu + Windows VM) that may not reflect actual IoT environments. Furthermore, the model consumes high resources (powerful GPUs) and is limited to the healthcare sector.



Suggestions:

Future development opportunities include expanding the dataset and diversifying its sources to include new attacks and zero-day ransomware, integrating deep learning techniques with lightweight methods suitable for resource-constrained IoT devices, and testing models in real, large-scale environments rather than just simulations. It is also important to improve the speed of models and reduce their resource consumption (lightweight models) while exploring distributed solutions such as edge computing for real-time detection.


Differences Between Developing Ransomware Detection Agents on PC and IoT:

PC:

Primary Goal: Protecting data (encrypting files, databases, operating systems).

Resources: Powerful (CPU, RAM, GPU) allows for the use of heavy and complex algorithms.

Standardization: Limited and well-known operating systems (Windows, Linux, macOS) → Easier to design targeted solutions.

Common Methods: Sandboxing, Deep Learning Models, In-depth File and Network Analysis.

Challenges:

Zero-day attacks (new, unsigned).

Polymorphic ransomware (constantly changing to bypass signatures).

Large data volumes that require continuous monitoring.


IoT:

Primary Goal: Protecting the functionality of devices (cameras, medical devices, sensors, smart cars), not just the data.

Resources: Very limited (low memory, weak processors, battery).

 Diversity: Thousands of device and system types (no single standard) → Difficulty in creating a one-size-fits-all solution.

Limitations: You cannot install traditional security systems like those found on PCs.

Appropriate approaches:

Lightweight detection models (such as L-IDS).

Edge computing to detect the device or nearby network instead of sending all data to the server.

Early prediction to prevent device failure.

Challenges: Balancing model accuracy with resource consumption, and ensuring real-time response.



























#Week7 Dataset Researching In Both PC and IoT

Datasets In PC:

Name and Date
Types of attacks
Features
Studies that used this dataset
Ransomware detection dataset.
2022

Access here.
Ransomware attacks (file-encrypting malware targeting Windows executables). Behavioral/system indicators from Windows environment (file creation/modification/access patterns).
Variety of types: numerical, categorial, boolean and metadata taken from several files in the system (not PE headers).
Comparative Analysis of Supervised Machine
Learning Models for Ransomware Detection.


Four supervised machine learning models (RF, SVM, CNN, LSTM) were compared using a dataset containing static and dynamic features. The Random Forest (RF) model demonstrated the best performance, achieving 99.49% accuracy and proving to be the most effective for ransomware detection.

Access here.


Datasets In IoT:

Name and Date
Types of attacks
Features
Studies that used this dataset
Ransomware PE Header Feature Dataset (Mendeley).
4 June 2024

-This dataset is directed to PC but there is a study that used it for detection in IoT-

Access here.
Windows-based ransomware, 25 families.



1024 numerical values representing the first 1024 bytes of the executable file header (PE header), used to train Al models to detect ransomware."

1134 Goodware
1023 Ransomware
A comparative study of deep learning-based ransomware detection for
industrial IoT.

Features were extracted using Opcodes and N-grams to train and compare 5 deep learning models. The CNN model achieved the best performance with 96.98% accuracy and a 96.98% F1-score.

Access here.
Ransomware detection dataset.
2022

Access here.
Ransomware attacks (file-encrypting malware targeting

Windows executables). Behavioral/system indicators from Windows environment (file creation/modification/access patterns).
Variety of types: numerical, categorial, boolean and metadata taken from several files in the system (not PE headers).

Size, ExportSize, DebugSize, Entropy, Imports/Exports, Byte distribution/Opcodes, BitcoinAddresses.
An intelligent ransomware based
cyberthreat detection model
using multi head attention-based
recurrent neural networks with
optimization algorithm in IoT
environment.

The paper introduces the MHARNN-EGTOCRD model for ransomware detection. The methodology involves using the Dung Beetle Optimization (DBO) algorithm for feature selection, followed by a Multi-head Attention-based LSTM (MHA-LSTM) for the core detection process. The model's parameters are fine-tuned using Enhanced Gorilla Troops Optimization (EGTO). When tested on a public dataset, the model achieved a peak accuracy of 98.53%.

Access here.

































#Week8 Dataset Researching In IoT

TON_IoT Dataset Report for AI-based Cybersecurity Applications
Access here.

1. General Information
•Dataset Name: TON_IoT Datasets
•Developed by: UNSW Canberra at the Australian Defence Force Academy (ADFA)
•Domain: Cybersecurity, Artificial Intelligence (AI), Internet of Things (IoT), Industrial IoT (IIoT)
•Purpose: To evaluate the effectiveness of machine learning (ML) and deep learning (DL) algorithms in detecting and analyzing cybersecurity threats
•License: Free for academic use; commercial use requires permission from the author (Dr. Nour Moustafa)
________________________________________

2. Data Collection Method
•Data was collected using a realistic, large-scale testbed environment that simulates Industry 4.0 networks.
•The testbed includes:
oReal and virtual IoT/IIoT devices
oMultiple operating systems: Windows 7, Windows 10, Ubuntu 14, Ubuntu 18, Kali Linux
oMulti-layer network: IoT → Fog/Edge → Cloud
•Four main data sources were captured:
1.IoT/IIoT Telemetry Data (e.g., Modbus, weather sensors)
2.Network Traffic Data (using tools like Zeek/Bro and Wireshark)
3.Windows Logs (via Performance Monitor Tool)
4.Linux System Logs (via tools like atop, netsniff-ng)
________________________________________

3. Simulation Details
•A wide range of cyber-attacks were simulated using real tools and platforms within the testbed.
•Attacks were launched from Kali Linux machines using IPs 192.168.159.30 – 192.168.159.39
•Attack targets included:
oWeb applications (e.g., Node-RED)
oIoT Gateways
oMQTT protocol services
oLinux and Windows machines
oCloud and Edge computing services
•Both normal and malicious activities were collected in parallel to ensure realistic dataset representation.

________________________________________

4. IoT Focus
•The dataset heavily emphasizes IoT and IIoT environments
•Includes telemetry data from over 10 different IoT/IIoT sensors (e.g., Modbus, temperature, humidity, weather)
•Simulates realistic communication and behavior in Industry 4.0 systems
•Tools used: Node-RED, Node-RED Modbus modules
________________________________________

5. Ransomware and Other Cyber Attacks
•Ransomware attacks are explicitly included in the dataset.
•The dataset also features a wide variety of other attack types, including:

Attack Type				Description
Ransomware				Encrypts files or systems to demand ransom
Denial of Service (DoS)			Overloads target resources to disrupt access
Distributed DoS (DDoS)			Same as DoS, but launched from multiple sources
Password Cracking			Attempts to brute-force or guess credentials
Man-in-the-Middle (MitM)		Intercepts communication between devices
Backdoor Access				Unauthorized remote control of a system
Privilege Escalation			Gains higher access rights within a system
SQL Injection				Malicious SQL commands to manipulate databases
Reconnaissance				Scans and probes to gather intelligence
Data Exfiltration				Steals sensitive data from targeted devices
Botnet Activity				Infection and remote control of IoT devices
Malware Propagation			Spreads malicious software across the network
________________________________________

6. How the Dataset Was Created
1.Designed a realistic Industry 4.0 testbed mimicking IoT/Fog/Cloud environments
2.Integrated various hardware, VMs, sensors, protocols, and operating systems
3.Conducted cyber-attacks from Kali Linux environments
4.Collected system, network, and telemetry data in multiple raw formats
5.Processed and labeled the data with standard features and attack types for ML/DL usage
________________________________________






7. Dataset Structure (Directory Overview)
Folder Name				Contents
Raw Datasets				Unprocessed logs: .csv, .log, .pcap, .blg, .txt files from various systems
Processed Datasets			Cleaned and labeled .csv files with unified features
Train_Test_datasets			Pre-selected samples for ML model training and evaluation
Description_stats_datasets			Feature descriptions and distribution stats of normal vs. attack records
SecurityEvents_GroundTruth_datasets	Timestamps and IPs for attack events – used for labeling ground truth
________________________________________

8. Feature Types (Features Used in the Dataset)

 IoT Telemetry Features:

•Sensor reading values
•Device ID
•Timestamps
•Attack label (normal/attack)
 Windows & Linux Features:
•CPU utilization
•Memory usage
•Number of running processes
•Disk activity
•Network I/O
•Attack label

 Network Features:

•Source/Destination IPs and ports
•Protocols
•Bytes sent/received
•Session duration
•TCP flags
•Packet count
•Attack label
All features are available in the processed dataset as labeled CSV files.
________________________________________





9. Research Papers That Used TON_IoT Dataset

The dataset has been cited and validated in at least 8 peer-reviewed academic papers, including:
1.Moustafa (2021) – Sustainable Cities and Society
2.Booij et al. (2021) – IEEE Internet of Things Journal
3.Alsaedi et al. (2020) – IEEE Access
4.Moustafa et al. (2020) – TrustCom (Windows)
5.Moustafa et al. (2020) – TrustCom (Linux)
6.Moustafa (2019) – eResearch Australasia
7.Moustafa (2019) – arXiv: Fog-Cloud Security Architecture
8.Ashraf et al. (2021) – Sustainable Cities and Society (IoTBot-IDS)
These publications validate the dataset's scientific credibility and practical usability in AI-based security research.
________________________________________

























#Week9 in depth Dataset Researching


Dataset Name
TON_IoT Dataset Report for AI-based Cybersecurity Applications 
Access here.
Studies
A Distributed Intrusion Detection System using Machine Learning for IoT based on ToN-IoT Dataset. Access here.
Research Idea


The study proposed a Distributed Intrusion Detection System (IDS) for IoT environments.
Unlike previous work that relied on outdated datasets such as KDD99 or UNSW-NB15, this research used the ToN-IoT dataset, which reflects realistic IoT network traffic.
The objective was to detect a wide range of IoT attacks, including ransomware, DDoS, and password attacks, with higher accuracy.
Dataset Handling




The ToN-IoT dataset posed several challenges: severe class imbalance, missing values, categorical attributes, and irrelevant features.
These issues were addressed by:
Feature selection using Chi2 test and correlation matrix.
Balancing the dataset with the SMOTE oversampling technique.
Data cleaning, including the removal of attributes such as Flow ID to avoid overfitting.
Features Considered
The most relevant attributes were extracted from NetFlow and IoT system data: Source and  IP addresses and ports, Protocol, Bytes sent and received, Session duration, Packet counts, TCP flags, Attack label (normal vs. attack).
Methodology
Multiple machine learning algorithms were tested: Naïve Bayes, Logistic Regression, Decision Tree, k-Nearest Neighbor, Support Vector Machine, Random Forest, XGBoost, and AdaBoost.
Experiments were conducted for both binary classification (normal vs. attack) and multi-class classification (specific attack types).
Results


XGBoost achieved the best performance compared to other algorithms.
Evaluation metrics included accuracy, precision, recall, F1-score, and false positive rate.
The combination of XGBoost, feature selection, and SMOTE yielded the most balanced and effective results.


