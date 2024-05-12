# Solution

## Steps followed

- Make sure the machines are connected to the same network. Use `ifconfig` to validate IP addresses.
- As we need to access `User1` in `Machine1`, make sure the user exists in the said machine. If not enter the following command:

  - `sudo adduser user1` (in Machine1)
- Now in the `Starting Machine`, check if there are any SSH keys already generated using `cd ~/.ssh`. These files are generally named `idrsa` and `idrsa.pub` where the former is a private key and the latter is a public key.
- If not, use the command: `ssh-keygen` (in Starting Machine) and follow the necessary steps. You are also prompted to create a Passphrase, which is basically a password to protect your private key.

    ![alt text](/Images/keygen.png)
    *Image: SSH Key generation*
- Now as we need Machine1 to be listening at a specified port, we can change the default 22 port to 3222 by:
  - `sudo nano /etc/ssh/sshd_config`
  - Change the default 22 port to `3222`

      ![alt text](/Images/port.png)
        *Image: SSH Configuration*
- After the creation of an SSH Key, it is necessary for the public key to be present in the machine you are trying to access in order to login password-free. In our situation, the public key from Starting Machine should be added to Machine1.

  - Use `ssh-copy-id -p <port> <user_name>@ip/domain` to copy your public IP to the machine you are trying to access. In our case, `ssh-copy-id -p 3222
  - If this does not work, it is also possible to manually copy your public key and paste it in `~/.ssh` in a file named `authorized_keys` which can be created using `nano authorized_keys`. Make sure the permissions to `authorized_keys` is `600` and the users and groups is `User1` itself.
          ![alt text](/Images/authkey.png) *Image: Creation of authorized_files*

    Note: All of this should be done on `Machine1`

- Now, the `Starting Machine` can try accessing `Machine1` as follows:
  - `ssh -p 3222 user1@<ip_of_machine1>`

These steps should grant you access to Machine1 from the Starting Machine. Remember, this process is just for the connection of the first two machines.
