## SSH Hardening and Security Best Practces

### Step 1: Disable Root Login (Prevent Direct Access)

🔹  The root account is a common target for brute force attacks. 🔹 I have edited the SSH configuration file:

```
sudo nano /etc/ssh/sshd_config
```
✅ Set:
```
PermitRootLogin no
```
🔹 Now, attackers can't log in directly as root—forcing them to use a regular user.

### Step 2: Change Default SSH Port

🔹 Attackers often scan for port 22 (default SSH port). 🔹I have changed the port in sshd_config:

Port 2222

🔹 Restart SSH to apply changes:
```
sudo systemctl restart sshd
```
✅ Now, automated scans looking for port 22 won’t find his server.

### Step 3: Use SSH Key Authentication (No Passwords!)

🔹  Password-based authentication is weak—keys provide stronger security. 🔹I will Generate SSH keys on the client machine:

```
ssh-keygen -t rsa -b 4096
```
2️⃣ Copy the key to the server:

```
ssh-copy-id user@server-ip
```
✅ Now, only authorized users with SSH keys can log in—brute force attacks won’t work.

### Step 4: Limit Login Attempts & Block Failed Attempts

🔹  Bots try thousands of passwords— I'll blocks repeated failed login attempts. 

🔹 ✅ In sshd_config, sets:

MaxAuthTries 3
✅ Uses fail2ban to block brute-force attacks:

```
sudo apt install fail2ban
sudo systemctl enable fail2ban
```
🔹 Now, attackers are locked out after multiple failures.

### Step 5: Allow Only Specific Users

🔹  Only authorized personnel should have SSH access.

✅ In sshd_config, added:

AllowUsers harshi devops_admin
✅ Only harshi and my team can connect!

### 🚀 DevOps Interview Questions & Answers on SSH Hardening

1️⃣ Why is disabling root login important? 

✔ Prevents direct root-level access to the server, reducing attack vectors.

2️⃣ How does SSH key authentication improve security? 

✔ Eliminates weak passwords—only users with valid SSH keys can authenticate.

3️⃣ Why should you change the default SSH port? 

✔ Prevents automated scans targeting common port 22, reducing attack risks.

4️⃣ How does fail2ban enhance SSH security? 

✔ Blocks repeated failed login attempts, mitigating brute-force attacks.

5️⃣ How would you allow only DevOps team members to log in via SSH? 

✔ Use the AllowUsers directive in /etc/ssh/sshd_config.
