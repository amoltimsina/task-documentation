# Roadblock 
## Major Issue

We encountered a significant roadblock stemming from a basic oversight on my part. When creating the `authorized_keys` file on Machine1, I mistakenly used `sudo nano authorized_keys`, resulting in the file being created with root ownership and group. Consequently, attempts to access it from the Starting Machine resulted in a "permission denied" error. We initially focused on setting appropriate permissions (`600` for `authorized_keys` and `700` for the `~/.ssh` directory) but overlooked the user and group ownership.

## Solution

After discussing with Saket Dai, we identified the oversight and rectified it by using the following command to change the user and group ownership of the `authorized_keys` file:

```bash
sudo chown user1:user1 authorized_keys
