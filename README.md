# Using-tools-like-John-the-Ripper-for-password-cracking
## NAME: SANTHOSH S
## REG.NO: 212224100052
## AIM:
To crack password hashes using John the Ripper in Kali Linux.
## REQUIREMENTS:
- **Operating System:** Kali Linux / Ubuntu / Windows (with JtR binaries)
- **Tools:**
    - John the Ripper (Community/Pro version)
    - Hash generating tools (e.g., openssl, unshadow)
- **Test Data:**
    - /etc/shadow file (Linux hashed passwords)
    - Custom password-protected file (ZIP, RAR, etc.)
## ARCHITECTURE DIAGRAM:
```mermaid
flowchart TD
    A[Password Protected File / Hash] --> B[John the Ripper]
    B --> C[Select Attack Mode: Dictionary or Brute Force]
    C --> D[Load Wordlist / Charset Rules]
    D --> E[Password Cracking Process]
    E --> F[Recovered Passwords]
```
## DESIGN STEPS:
### Step 1: Install John the Ripper
```bash
sudo apt update
sudo apt install john -y
```

### Step 2: Prepare Hash File
- Extract hashes (Linux example):
```
unshadow /etc/passwd /etc/shadow > hash.txt
```
- For a ZIP file:
```
zip2john santhosh.txt.zip > hash.txt
```
### Step 3: Run John the Ripper
- Dictionary Attack:
```
john --wordlist=zip_wordlist.txt hash.txt

```
### Step 4: Show Cracked Passwords
```
john --show hash.txt
```
## PROGRAM:
1. **Hash Extraction** – Obtain password hashes from system files or encrypted archives.
2. **Attack Mode Selection** – Choose between dictionary, brute force, or hybrid.
3. **Cracking Phase** – John the Ripper runs through candidate passwords.
4. **Password Recovery** – Successfully cracked passwords are displayed.

## OUTPUT:
Cracked Passwords from Hash File
<img width="581" height="346" alt="1" src="https://github.com/user-attachments/assets/d2b85cde-e24b-46ee-b551-23156419df6c" />

<img width="712" height="624" alt="2" src="https://github.com/user-attachments/assets/06a173c0-3c3f-4b42-9057-009cfcac0295" />

<img width="772" height="460" alt="3" src="https://github.com/user-attachments/assets/06bf7c53-b63f-4e7c-91c0-199c80070345" />

<img width="957" height="1199" alt="4" src="https://github.com/user-attachments/assets/0f3edd2f-3a47-405c-95b0-193ae730a3c3" />

<img width="652" height="336" alt="5" src="https://github.com/user-attachments/assets/f2e9297e-79a2-4aff-b0d3-e4a6391278a9" />

## RESULT:
The password hashes were successfully cracked using John the Ripper.

