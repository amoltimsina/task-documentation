# Solution

## Steps Executed

- Ensure all machines are on the same network. Verify IP addresses using `ifconfig`.
- Confirm the existence of `User1` on `Machine1`. If absent, create the user with:
  
  ```bash
  sudo adduser user1
  ```

- Check for existing SSH keys on the `Starting Machine` with `cd ~/.ssh`. Typical keys are `id_rsa` (private) and `id_rsa.pub` (public).
- Generate SSH keys if absent by running `ssh-keygen` on the `Starting Machine`. Follow the prompts, including passphrase creation for added security.

  ![SSH Key generation](/images/keygen.png)
  
- Modify `Machine1`'s SSH configuration to listen on port 3222 instead of the default 22:
  
  ```bash
  sudo nano /etc/ssh/sshd_config
  ```
  
  Change the default port to `3222`.
  
  ![SSH Configuration](/images/port.png)

- To enable password-less login, add the public key from the `Starting Machine` to `Machine1`:

  ```bash
  ssh-copy-id -p <port> <user_name>@ip/domain
  ```

  If unsuccessful, manually copy the public key and paste it into `~/.ssh/authorized_keys` on `Machine1`. Set permissions to `600` and ensure ownership by `User1`.

  ![Creation of authorized_files](/images/authkey.png)

- Test the connection from the `Starting Machine` to `Machine1`:

  ```bash
  ssh -p 3222 user1@<ip_of_machine1>
  ```

These steps establish a password-less SSH connection from the `Starting Machine` to `Machine1`. Ensure `User1` has appropriate permissions and access.
