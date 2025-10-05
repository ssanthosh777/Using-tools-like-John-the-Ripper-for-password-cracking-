# Using-tools-like-John-the-Ripper-for-password-cracking
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
unshadow /etc/passwd /etc/shadow > myhashes.txt
```
- For a ZIP file:
```
zip2john secret.zip > ziphash.txt
```
### Step 3: Run John the Ripper
- Dictionary Attack:
```
john --wordlist=/usr/share/wordlists/rockyou.txt myhashes.txt
```
- Brute Force (Incremental Mode):
```
john --incremental myhashes.txt
```
### Step 4: Show Cracked Passwords
```
john --show myhashes.txt
```
## PROGRAM:
1. **Hash Extraction** – Obtain password hashes from system files or encrypted archives.
2. **Attack Mode Selection** – Choose between dictionary, brute force, or hybrid.
3. **Cracking Phase** – John the Ripper runs through candidate passwords.
4. **Password Recovery** – Successfully cracked passwords are displayed.

## OUTPUT:
Cracked Passwords from Hash File
<img width="1718" height="920" alt="Screenshot_2025-10-02_08_06_12" src="https://github.com/user-attachments/assets/3dd82be6-3a0d-4343-bf6f-fbdb066a97c0" />

<img width="1718" height="920" alt="Screenshot_2025-10-02_08_07_33" src="https://github.com/user-attachments/assets/cfa72e29-01f6-4fbc-93fb-a8890b9857cb" />

<img width="1280" height="649" alt="Screenshot_2025-10-02_09_10_28" src="https://github.com/user-attachments/assets/32b02173-3e67-4ae1-9708-f20c27d23ebf" />


<img width="1718" height="920" alt="Screenshot_2025-10-02_09_14_11" src="https://github.com/user-attachments/assets/445e9033-da06-4d2c-ab7a-152199ef7efd" />


<img width="1076" height="919" alt="Screenshot_2025-10-02_09_19_31" src="https://github.com/user-attachments/assets/c1bd5ecd-6403-4fb3-8aed-1d6954fecd19" />


## RESULT:
The password hashes were successfully cracked using John the Ripper.

