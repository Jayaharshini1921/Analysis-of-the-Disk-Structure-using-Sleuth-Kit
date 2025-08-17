# Analysis-of-the-Disk-Structure-using-Sleuth-Kit
## AIM:
To analyze the disk structure of a given disk image using Sleuth Kit tools in Kali Linux.

## REQUIREMENTS
- **Operating System**: Windows 10/11 or Kali Linux
- **Tools**:  
  - [The Sleuth Kit for Windows](https://sleuthkit.org/)  
  - Optional GUI: [Autopsy Forensic Browser](https://www.autopsy.com/)
- **Test Data**: Disk image file (`disk.dd`, `disk.img`, `.E01`)

## ARCHITECTURE DIAGRAM
```mermaid
flowchart TD
    A[Disk Image / Physical Disk] --> B[mmls - Partition Analysis]
    B --> C[fsstat - File System Metadata]
    C --> D[fls - File Listing]
    D --> E[icat - File Recovery]
    E --> F[Recovered Data / Metadata Report]
```
## DESIGN STEPS:
### Step 1:
- Obtain or create a disk image file (e.g., disk.dd) to analyze.
- Open the terminal in Kali Linux.

### Step 2:
Use Sleuth Kit tools like:
 - mmls → Examine the partition layout.
 - fsstat → View file system details.
 - fls → Get file listing.
 - icat → Recover files using inode numbers.
### Step 3:
Interpret the output to understand:
 - Partition table layout
 - File system metadata (block size, creation time, etc.)
 - Deleted and allocated files
 - Inode-based file recovery

## PROGRAM:
Sleuth Kit Disk Analysis Commands
### Partition Analysis
```bash
mmls disk.dd
```
### File System Metadata
```bash
fsstat -o 2048 disk.dd
```
### File Listing
```bash
fls -o 2048 disk.dd
```
### File Recovery
```bash
icat -o 2048 disk.dd 4 > recovered_file.txt
```
- Recovers the file associated with inode 4.
## SAMPLE WORKFLOW (Windows)
```bash
# Step 1: View partitions
mmls.exe C:\forensics\disk.dd

# Step 2: View file system details
fsstat.exe -o 2048 C:\forensics\disk.dd

# Step 3: List files
fls.exe -r -o 2048 C:\forensics\disk.dd

# Step 4: Recover a file
icat.exe -o 2048 C:\forensics\disk.dd 6 > C:\forensics\image.jpg
```
## OUTPUT:
Disk Structure Analysis Results
<img width="1105" height="285" alt="437144346-38402af4-39db-4a51-9518-573ca310c30a" src="https://github.com/user-attachments/assets/caab4d3d-494d-47c6-bd2a-ff97dfe1c97a" />

Create Disk
<img width="1086" height="512" alt="437144438-8739f746-485b-4f73-a5af-31280b3cffa9" src="https://github.com/user-attachments/assets/3bcfa69e-5603-4622-867f-724d6ecf2b08" />

mmls
mmls disk.dd

fls
fls -f fat -o 0 disk.dd


<img width="543" height="252" alt="437144695-570ead96-1fd9-4834-ac98-42530ac39c43" src="https://github.com/user-attachments/assets/91c302c6-2067-483e-9c18-0ddea14ab014" />

<img width="1027" height="645" alt="437144740-86d2a644-2f80-4428-85ec-2efc03e16702" src="https://github.com/user-attachments/assets/355ff94b-eecd-475d-8fcb-4ec53ef0c66d" />

<img width="579" height="244" alt="437144795-5dd5ec7d-f9f8-4475-a018-a4bef8cb4382" src="https://github.com/user-attachments/assets/9759f39b-68bb-41c6-9e0c-b070f4256bb2" />

<img width="510" height="383" alt="437144827-83a87658-c58b-4a01-b492-91f5f57bfa86" src="https://github.com/user-attachments/assets/c24e554a-f099-45dc-a900-260f13342db1" />

## RESULT:
The analysis was performed successfully using Sleuth Kit, and the disk structure was understood in detail.
