# Workstation config playbook
Why: Because laptop failures follow me around. 
What: Ansible for Fedora workstation (30 as of this writing)
How: Ansible

- From a fresh install
```
sudo dnf install ansible -y
```
- Enable passwordless sudo
  - `sudo visudo` and edit to ensure the line is present
  ```
  %wheel  ALL=(ALL) NOPASSWD: ALL
  ```
  - copy your user public key to /root/.ssh/authorized_keys

## Current Capbilities 
Install the apps. 

## Notes
- Using `snap` requires a session logout/login. 
- Disable secureboot :( 