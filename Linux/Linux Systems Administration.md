# Linux Systems Administration


##Step 1: Ensure/Double Check Permissions on Sensitive Files

![](/Linux/Images/AB-1-create-user.png)


1. Permissions on `/etc/shadow` should allow only `root` read and write access.


![](/Linux/Images/LSA1.1-access.png)


- Command to inspect permissions :
ls -l /etc/shadow

- Command to set permissions (if needed):
sudo chmod 600 /etc/shadow


2. Permissions on `/etc/gshadow` should allow only `root` read and write access.

![](/Linux/Images/LSA1.2-write-access.png)

- Command to inspect permissions:
ls -l /etc/gshadow

- Command to set permissions (if needed):
sudo chmod 600 /etc/gshadow


3. Permissions on `/etc/group` should allow `root` read and write access, and allow everyone else read access only.   

![](/Linux/Images/LSA-1.3-group-access.png)

- Command to inspect permissions:
ls -l /etc/group


- Command to set permissions (if needed):
sudo chmod 644 /etc/group


4. Permissions on `/etc/passwd` should allow `root` read and write access, and allow everyone else read access only.

![](/Linux/Images/LSA-1.4-root-access.png)


- Command to inspect permissions:
ls -l /etc/passwd


- Command to set permissions (if needed):
sudo chmod 644 /etc/passwd


##Step 2: Create User Accounts


1. Add user accounts for `sam`, `joe`, `amy`, `sara`, and `admin`.

![](/Linux/Images/LSA-2.1-sam.png)
![](/Linux/Images/LSA-2.1-amy.png)
![](/Linux/Images/LSA-2.1-admin.png)


- Command to add each user account (include all five users):
sudo adduser sam
sudo adduser joe
sudo adduser amy
sudo adduser sara
sudo adduser admin (enter password)


2. Ensure that only the `admin` has general sudo access.   

![](/Linux/Images/LSA-2.2-access.png)

- Command to add `admin` to the `sudo` group:
sudo usermod -aG sudo admin


![](/Linux/Images/LSA-2.2-sudo-admin.png)

##Step 3: Create User Group and Collaborative Folder

1. Add an `engineers` group to the system.

  ![](/Linux/Images/LSA-3.1-engineers.png)

- Command to add group:
sudo addgroup engineers


2. Add users `sam`, `joe`, `amy`, and `sara` to the managed group.

  ![](/Linux/Images/LSA-3.2-users.png)


- Command to add users to `engineers` group (include all four users):
sudo usermod -aG engineers sam
sudo usermod -aG engineers joe
sudo usermod -aG engineers amy
sudo usermod -aG engineers sara


To see your groups type getent group   

  ![](/Linux/Images/LSA-3.2-getent-group.png)

Confirming users are in the engineers group

  ![](/Linux/Images/LSA-3.2-engineers-group.png)


3. Create a shared folder for this group at `/home/engineers`.

  ![](/Linux/Images/LSA-3.3-mkdir-engineers.png)

- Command to create the shared folder:
sudo mkdir engineers


4. Change ownership on the new engineers' shared folder to the `engineers` group.

- Command to change ownership of engineer's shared folder to engineer group:
sudo chown -R :engineers /home/engineers
sudo chown root /home/engineers

  ![](/Linux/Images/LSA-3.4-chown.png)

 sudo chgrp -R engineers /home/engineers (also works)


### Step 4: Lynis Auditing


1. Command to install Lynis:
sudo apt install lynis


2. Command to see documentation and instructions:
sudo lynis –help
man lynis


3. Command to run an audit:
lynis audit <system name>   to write the script into the log


sudo lynis audit system  to run the audit


  ![](/Linux/Images/LSA-4.3-sudo-lynis-audit.png)  


4. Provide a report from the Lynis output on what can be done to harden the system.


    - Screenshot of report output:


  ![](/Linux/Images/LSA-4.4-output.png)  

  ![](/Linux/Images/LSA-4.4-output-2.png)  

##Bonus


1. Command to install chkrootkit:
sudo apt install chkrootkit


  ![](/Linux/Images/LSA-Bonus-chkrootkit.png)  

2. Command to see documentation and instructions:
        sudo chkrootkit –help
        man chkrootkit


3. Command to run expert mode:
sudo /usr/sbin/chkrootkit -x   or  sudo chkrootkit -x (depending on where you are)


4. Provide a report from the chrootkit output on what can be done to harden the system.
    - Screenshot of end of sample output:

  ![](/Linux/Images/LSA-Bonus-output.png)      
