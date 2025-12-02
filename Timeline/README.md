# 🕒 Timeline Analysis (Plaso / log2timeline)

This folder contains the output generated during the timeline analysis phase of the **Compromised Server Investigation** project.

Because Plaso timelines can be very large, the full `.plaso` file was **split into multiple parts** for GitHub upload. Instructions for recombining the timeline are included below.

---

## 📘 About the Timeline

The timeline was created using:

- **log2timeline.py** – to extract timestamped events from the disk image  
- **psort.py** – to convert the timeline into CSV format  

The unified timeline correlates:

- File system activity  
- Process execution  
- Registry modifications  
- Browser events  
- Network-related timestamps  

This allows the entire intrusion to be reconstructed chronologically.

---

## 📦 Files in This Folder

You will find:

- `charlie_timeline_unlocked_part_aa`
- `charlie_timeline_unlocked_part_ab`
- `charlie_timeline_unlocked_part_ac`
- *(…additional split parts)*  
- **Split .plaso segments** uploaded due to GitHub size limits  
- **CSV outputs** (if applicable)

These files together represent the complete Plaso output.

---

## 🔧 How to Reassemble the Timeline

Because GitHub does not allow files larger than 100 MB, the `.plaso` timeline was uploaded in multiple chunks.

To reconstruct the full timeline:

```bash
cd Timeline

cat charlie_timeline_unlocked_part_* > charlie_timeline_unlocked.plaso.gz

gunzip charlie_timeline_unlocked.plaso.gz
```

After running these commands, you will get:

```
charlie_timeline_unlocked.plaso
```

This is the full Plaso timeline database.

---

## 📂 Folder Structure

```
Timeline/
│── charlie_timeline_unlocked_part_aa
│── charlie_timeline_unlocked_part_ab
│── charlie_timeline_unlocked_part_ac
│── ...
│── README.md   # You are reading this file
```

---

## 🎯 Purpose

This timeline is used to:

- Rebuild the attack sequence  
- Align disk, memory, and network activities  
- Identify when key events occurred  
- Support final reporting and conclusions  

The timeline is one of the most important components of the forensic investigation because it reveals **when**, **how**, and **in what order** the intrusion unfolded.
