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

<img width="1105" height="285" alt="437144346-38402af4-39db-4a51-9518-573ca310c30a" src="https://github.com/user-attachments/assets/14310d1d-0168-4429-940a-0b052167033c" />

Create Disk
<img width="1086" height="512" alt="437144438-8739f746-485b-4f73-a5af-31280b3cffa9" src="https://github.com/user-attachments/assets/a82a5510-7348-4a2c-8ad0-b3f4e22dbf6f" />

mmls
mmls disk.dd


fls
fls -f fat -o 0 disk.dd

<img width="543" height="252" alt="437144695-570ead96-1fd9-4834-ac98-42530ac39c43" src="https://github.com/user-attachments/assets/d223fdc0-7736-4507-829b-517c76b3ce61" />

<img width="1027" height="645" alt="437144740-86d2a644-2f80-4428-85ec-2efc03e16702" src="https://github.com/user-attachments/assets/a6c83524-ea86-42c7-b877-1b8562b4d8a8" />

<img width="579" height="244" alt="437144795-5dd5ec7d-f9f8-4475-a018-a4bef8cb4382" src="https://github.com/user-attachments/assets/475c75ed-27f7-4ea8-9547-5f53fafcbaf3" />

<img width="510" height="383" alt="437144827-83a87658-c58b-4a01-b492-91f5f57bfa86" src="https://github.com/user-attachments/assets/38c5dc19-fff5-4770-8345-ece5125ac649" />


## RESULT:
The analysis was performed successfully using Sleuth Kit, and the disk structure was understood in detail.
