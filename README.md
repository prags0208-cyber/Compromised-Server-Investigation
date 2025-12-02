# 🕵️‍♀️ Compromised Server Investigation  
### **Option A – Digital Forensics Project**

This project investigates a **compromised server** using industry-standard **disk, memory, and network forensic techniques**.  
Using tools like **Autopsy**, **Volatility**, **Wireshark**, and **Plaso/log2timeline**, the analysis reconstructs the attacker’s behavior, persistence mechanisms, and data exfiltration attempts.

---

## 🔍 Objective  

The investigation aimed to:  
- Identify **deleted files**, **hidden data**, and **unauthorized system modifications**.  
- Analyze **memory dumps** to uncover malicious processes and persistence artifacts.  
- Examine **network captures (PCAPs)** for suspicious communication patterns.  
- Generate a **timeline** of attacker activity across multiple forensic sources.  
- Recommend **security hardening** steps to prevent similar compromises.

---

## 🧰 Tools & Environment  

| Tool | Purpose |
|------|---------|
| **Autopsy** | Disk image analysis, deleted files discovery, partition & metadata inspection |
| **Volatility** | Memory forensics, process inspection, registry and code injection detection |
| **Wireshark** | Network traffic analysis (HTTP anomalies, IRC traffic, DNS lookups) |
| **Plaso / log2timeline** | Automated timeline creation from logs, artifacts, and disk images |
| **Ubuntu 22.04 VM** | Controlled forensic analysis environment |

---


## 📁 Folder Structure

```
Analysis/
│
├── Disk Forensics - Autopsy/
│   Contains Autopsy exports, registry hives, browser history, and PDF reports.
│
├── Memory Forensics - Volatility/
│   Volatility output files (pslist, pstree, cmdscan, runkeys, malfind, etc.) and Scripts used for execution.
│
├── Network Analysis - Wireshark/
│   Screenshots and packet analysis related to HTTP, PCAP, and IRC traffic.
│
├── Timeline/
│   Plaso/log2timeline output split into multiple parts for upload.
│
├── Evidence/
│   PCAP files and data used for disk and memory forensic analysis.
│
└── Reports/
    Final forensic report and supporting documents.
```

---

## 🧠 Methodology  

### **1️⃣ Disk Forensics – Autopsy**
- Loaded `charlie-2009-12-11.E01` into **Autopsy**.  
- Identified:  
  - Deleted files  
  - Suspicious executables  
  - Abnormal system configurations  
- Extracted:  
  - Registry hives  
  - Startup entries  
  - Potential persistence artifacts  

---

### **2️⃣ Memory Forensics – Volatility**
Executed key plugins including:  
- `pslist`, `pstree` → enumerate running processes  
- `netscan` → active network connections  
- `cmdscan`, `consoles` → attacker command history  
- `malfind` → injected code / suspicious memory regions  

Findings showed **malicious processes**, **shell activity**, and **probable injection points**.

---

### **3️⃣ Network Forensics – Wireshark**
Analyzed `.cap` files to detect:  
- Unusual outbound HTTP communications  
- IRC-based command & control traffic  
- Suspicious DNS resolutions  
- Signs of **data exfiltration**  

---

### **4️⃣ Timeline Analysis – Plaso / log2timeline**

#### Create the timeline:
```bash
sudo log2timeline.py charlie_timeline.plaso ~/Forensic_Project/Evidence/charlie-2009-12-11.E01
```

#### Export CSV report:
```bash
sudo psort.py -o L2tcsv charlie_timeline.plaso -w charlie_timeline.csv
```

#### Split timeline files for GitHub:
Large files were split for storage and version control under `/Timeline`.

---

## 🔄 Reconstructing Split Files  

To rebuild the full timeline artifact:

```bash
cd Timeline
cat charlie_timeline_unlocked_part_* > charlie_timeline_unlocked.plaso.gz
gunzip charlie_timeline_unlocked.plaso.gz
```

This produces the original **.plaso** timeline database.

---

## 📊 Key Findings  

- Evidence of **persistence mechanisms**, including altered startup entries.  
- Discovery of **malicious scripts** and deleted artifacts.  
- **IRC and HTTP C2-like traffic** indicating remote attacker control.  
- Timeline revealed:  
  - Initial intrusion  
  - File creation, modification, and deletion  
  - Attacker cleanup attempts  

---

## 🛡️ Recommendations  

- Restrict and audit **user privileges**.  
- Disable unused accounts and enforce strong authentication.  
- Deploy **HIDS/EDR** solutions on critical servers.  
- Implement **file integrity monitoring** on system partitions.  
- Maintain **centralized logging**, regular snapshots, and cryptographic hashing.  
- Harden network perimeter with strict outbound traffic policies.

---

## 👩‍💻 Author  

**Pragathi Kolla**  
*University at Albany – Digital Forensics*  
📧 **pkolla@albany.edu**  
🔗 GitHub: **https://github.com/prags0208-cyber**

---

## 📚 References  

- **Volatility Foundation** – Memory Forensics Framework  
- **Plaso / log2timeline** – Timeline Analysis Tool  
- **Autopsy** – Digital Forensics Platform  
- **Wireshark** – Network Protocol Analyzer  
