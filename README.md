# Day-65-100-Days-challenge-in-cybersecurity-
## 📅 Day 65: File Upload Vulnerability & Secure Storage

Today's focus was on the mechanics of **File Upload Vulnerabilities** and the multi-layered defense-in-depth strategies required to mitigate them.

### 🔍 Vulnerability Overview
When an application accepts user-uploaded files without rigorous server-side validation, it opens a door for **Remote Code Execution (RCE)**. Attackers bypass simple client-side checks to upload web shells (`.php`, `.asp`), gaining a command-line interface to the host.

### 🛡️ Mitigation & Deep Defense
I focused on four critical prevention pillars:

1. **Content-Based Validation**: 
   - Moving past extension-based filtering.
   - Implementing **Magic Byte** checks (e.g., verifying `FF D8 FF` for JPEGs).
2. **Execution Disablement**: 
   - Configuring server directories (via `.htaccess` or Nginx config) to treat all files as **static data**, preventing the server-side engine from executing scripts.
3. **Randomized Renaming**: 
   - Preventing **IDOR** and path traversal by renaming `user_file.jpg` to a cryptographically secure random string.
4. **Path Isolation**: 
   - Moving files out of the web root and into dedicated storage buckets (e.g., AWS S3) to decouple data from application logic.

> **Key Learning:** In security, untrusted input is the root of all evil. Treat every file as a potential payload.
