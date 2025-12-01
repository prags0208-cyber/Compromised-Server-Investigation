##############################################################
# 1. Update system packages
##############################################################
sudo apt update

##############################################################
# 2. Install Python2 and Git (required for Volatility 2)
##############################################################
sudo apt install -y python2 git

##############################################################
# 3. Clone Volatility 2 from the official GitHub repo
##############################################################
git clone https://github.com/volatilityfoundation/volatility.git ~/volatility2

##############################################################
# 4. Move into the Volatility directory
##############################################################
cd ~/volatility2

##############################################################
# 5. Verify Volatility installation
##############################################################
python2 vol.py --info | head

##############################################################
# 6. Run imageinfo to detect OS profile
##############################################################
python2 vol.py -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage imageinfo

# Suggested profile: WinXPSP3x86

##############################################################
# 7. Process listing (pslist)
##############################################################
python2 vol.py \
 -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
 --profile=WinXPSP3x86 \
 pslist \
 > ~/Forensic_Project/Analysis/pslist.txt

##############################################################
# 8. Process tree (pstree)
##############################################################
python2 vol.py \
 -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
 --profile=WinXPSP3x86 \
 pstree \
 > ~/Forensic_Project/Analysis/pstree.txt

##############################################################
# 9. Network connections (connections)
##############################################################
python2 vol.py \
 -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
 --profile=WinXPSP3x86 \
 connections \
 > ~/Forensic_Project/Analysis/connections.txt

##############################################################
# 10. Sockets listing (sockets)
##############################################################
python2 vol.py \
 -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
 --profile=WinXPSP3x86 \
 sockets \
 > ~/Forensic_Project/Analysis/sockets.txt

##############################################################
# 11. File handles (filescan)
##############################################################
python2 vol.py \
 -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
 --profile=WinXPSP3x86 \
 filescan \
 > ~/Forensic_Project/Analysis/filescan.txt

##############################################################
# 12. Command history (cmdscan)
##############################################################
python2 vol.py \
 -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
 --profile=WinXPSP3x86 \
 cmdscan \
 > ~/Forensic_Project/Analysis/cmdscan.txt

##############################################################
# 13. Startup registry keys (Run keys)
##############################################################
python2 vol.py \
 -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
 --profile=WinXPSP3x86 \
 printkey -K "Software\\Microsoft\\Windows\\CurrentVersion\\Run" \
 > ~/Forensic_Project/Analysis/runkeys.txt

##############################################################
# 14. Detect injected/malicious code (malfind)
##############################################################
python2 vol.py \
 -f ~/Forensic_Project/Evidence/charlie-2009-12-11.mddramimage \
 --profile=WinXPSP3x86 \
 malfind \
 > ~/Forensic_Project/Analysis/malfind.txt

# NOTE: Volatility recommends installing distorm3 for best malfind results.
