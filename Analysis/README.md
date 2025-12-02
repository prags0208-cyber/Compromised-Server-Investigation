# 📁 Analysis Folder

This folder contains all the **forensic analysis outputs** generated during the Compromised Server Investigation project.

Due to GitHub’s file size limits, **only processed output files, screenshots, and summaries** are included here.  
Large raw analysis files (such as full Autopsy extraction folders or Plaso timelines) have been split or summarized.

---

## 🧩 Subfolders Overview

### 🔹 **Disk Forensics – Autopsy**
Located in: `Disk Forensics - Autopsy/`

Contains:
- Autopsy-generated PDF reports  
- Extracted registry artifacts  
- Browser-related artifacts  
- User profile evidence  
- Parsed metadata and file system screenshots  

This folder summarizes disk-level findings obtained from the E01 image, including deleted files, registry hives, hidden DLLs, and user activity.

---

### 🔹 **Memory Forensics – Volatility**
Located in: `Memory Forensics - Volatility/`

Contains output from Volatility plugins such as:
- `pslist`, `pstree` – Process enumeration  
- `cmdscan` – Command-line activity  
- `filescan` – Memory-resident file objects  
- `connections`, `sockets` – Network connections at capture time  
- `malfind` – Injected code & suspicious memory regions  
- `runkeys` – Persistence artifacts from registry keys  

These artifacts helped reconstruct what was running *at the exact moment* the system was compromised.

---

### 🔹 **Network Analysis – Wireshark**
Located in: `Network Analysis - Wireshark/`

Contains:
- Screenshots of analyzed HTTP, IRC, DNS, and fragmented packets  
- Packet flow diagrams  
- Protocol hierarchy summaries  
- Reconstructed conversations (HTTP stream, IRC chat logs)

All network findings correlate with the PCAPs stored in the Evidence folder.

---

### 🔹 **Timeline**
Located in: `Timeline/`

Contains:
- Split parts of the Plaso (`.plaso`) timeline  
- Instructions for recombining the timeline  
- Partial CSV outputs for reference  

Plaso was used to generate a unified event timeline linking disk, memory, and network events chronologically.

---

## 📂 Folder Structure

```
Analysis/
│
├── Disk Forensics - Autopsy/
├── Memory Forensics - Volatility/
├── Network Analysis - Wireshark/
├── Timeline/
└── README.md     # You are reading this file
```

---

## 🎯 Purpose

The **Analysis** directory contains all processed forensic outputs needed to:

- Document the investigation process  
- Verify findings from each forensic layer  
- Rebuild the attacker’s actions  
- Support the conclusions presented in the Final Report  

This structure keeps the repository clean and accessible while providing all relevant evidence for reproducibility.
