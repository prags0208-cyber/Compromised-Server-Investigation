# 🧠 Memory Forensics – Volatility Analysis

This folder contains Volatility 2 commands and output artifacts used to analyze the memory dump of the compromised system.

---

## 🔧 Installation & Setup

```bash
sudo apt update
sudo apt install -y python2 git
git clone https://github.com/volatilityfoundation/volatility.git ~/volatility2
```

---

## 📘 Identify Memory Image Profile

```bash
python2 vol.py -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage imageinfo
```

---

## 📝 Volatility Commands Used

### 1. Process List (pslist)
```bash
python2 vol.py -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
--profile=WinXPSP3x86 pslist \
> ~/Forensic_Project/Analysis/pslist.txt
```

### 2. Process Tree (pstree)
```bash
python2 vol.py -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
--profile=WinXPSP3x86 pstree \
> ~/Forensic_Project/Analysis/pstree.txt
```

### 3. Network Connections
```bash
python2 vol.py --profile=WinXPSP3x86 -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
connections \
> ~/Forensic_Project/Analysis/connections.txt
```

### 4. Sockets
```bash
python2 vol.py --profile=WinXPSP3x86 -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
sockets \
> ~/Forensic_Project/Analysis/sockets.txt
```

### 5. File Scan
```bash
python2 vol.py --profile=WinXPSP3x86 -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
filescan \
> ~/Forensic_Project/Analysis/filescan.txt
```

### 6. Command History (cmdscan)
```bash
python2 vol.py --profile=WinXPSP3x86 -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
cmdscan \
> ~/Forensic_Project/Analysis/cmdscan.txt
```

### 7. Registry Run Keys
```bash
python2 vol.py --profile=WinXPSP3x86 -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
printkey -K "Software\\Microsoft\\Windows\\CurrentVersion\\Run" \
> ~/Forensic_Project/Analysis/runkeys.txt
```

### 8. Malicious Code Detection (malfind)
```bash
python2 vol.py --profile=WinXPSP3x86 -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
malfind \
> ~/Forensic_Project/Analysis/malfind.txt
```

> **Note:** Install `distorm3` for best malfind results.

---

## 📷 Recommended Screenshots for Report
- `imageinfo` output  
- `pslist` highlight suspicious processes  
- `pstree` parent-child anomalies  
- `connections` showing suspicious IPs  
- `malfind` showing injected code  

---

