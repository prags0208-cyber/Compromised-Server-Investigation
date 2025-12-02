# 📁 Evidence Folder

This folder contains the evidence used for the **Compromised Server Investigation** project.  
Due to GitHub's file size restrictions, **large forensic data files (E01 disk image and RAM dump) cannot be uploaded here**.

Instead, the original dataset sources have been provided below.

---

## 🔗 Download Links for Full Evidence (M57 Patents Scenario)

### **1️⃣ Disk Image (E01 Format)**  
Used for Autopsy disk forensics.  
Download link:  
https://digitalcorpora.org/corp/nps/scenarios/2009-m57-patents/charlie-2009-12-11.E01

### **2️⃣ Memory Dump (RAM Image)**  
Used for Volatility memory forensics.  
Download link:  
https://digitalcorpora.s3.amazonaws.com/corpora/scenarios/2009-m57-patents/ram/charlie-2009-12-11.mddramimage.zip

---

## 📦 Evidence Included in This Repository

GitHub allows only files smaller than 100 MB.  
Therefore, **only lightweight evidence files** used in network forensics and analysis are included here:

- **SkypeIRC.cap** – IRC chat traffic  
- **http.cap** – HTTP request/response data  
- **ipv4frags.pcap** – Fragmented ICMP/IP packets  
- **Data For Memory and Disk/** – Folder structure included only for reference  

---

## 📂 Folder Structure

```
Evidence/
│── SkypeIRC.cap                 # IRC packet capture
│── http.cap                     # HTTP traffic capture
│── ipv4frags.pcap               # IPv4 fragmented packet capture
│── Data For Memory and Disk/    # Placeholder folder for large evidence
└── README.md                    # You are reading this file
```

---

## 🎯 Purpose

This folder preserves all **accessible** forensic evidence and provides download links for the larger files required for:

- Disk Forensics (Autopsy)
- Memory Forensics (Volatility)
- Network Analysis (Wireshark)
- Timeline Creation (Plaso)

By keeping the full dataset externally available and providing the smaller PCAPs here, the repository remains lightweight while maintaining **full reproducibility** of the investigation.
