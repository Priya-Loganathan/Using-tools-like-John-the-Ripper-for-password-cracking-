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

<img width="1273" height="715" alt="Screenshot 2025-09-28 110300" src="https://github.com/user-attachments/assets/3bf448e5-737d-451a-8ae3-e5415aae6463" />

<img width="1108" height="713" alt="Screenshot 2025-09-28 110122" src="https://github.com/user-attachments/assets/545ea7b1-ca14-4751-a937-afb94195058a" />

<img width="1272" height="717" alt="Screenshot 2025-09-28 110234" src="https://github.com/user-attachments/assets/f38d2601-ed88-44f8-8f27-d40e80e76ad2" />

<img width="1275" height="710" alt="Screenshot 2025-09-28 110414" src="https://github.com/user-attachments/assets/5a19f0b4-3c07-4a45-ad6b-e35dc81889f5" />

<img width="1272" height="718" alt="Screenshot 2025-09-28 110527" src="https://github.com/user-attachments/assets/263be6a6-0c09-4d35-ad87-b3b10f64348c" />

<img width="1271" height="719" alt="Screenshot 2025-09-28 110807" src="https://github.com/user-attachments/assets/94483844-a4a4-40a9-b0c4-f7d692832ba7" />

## RESULT:
The password hashes were successfully cracked using John the Ripper.

