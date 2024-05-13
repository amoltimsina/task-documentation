# Roadblock 
## Major Issue
<<<<<<< HEAD
 We encountered with a roadblock which was a silly rookie mistake of mine. When creating an `authorized_key` file in `Machine1` I was apparently using `sudo nano authorized_key` which due to the use of `sudo` created the file under owner and group `root`. This created a problem of "permission denied" when trying to access from the `Starting Machine`. We overlooked the group and owner and focused more on the permission side, which we had assigned `600` for `authorized_keys` and `700` for the directory `~/.ssh`. 

## Solution
After a meeting with Saket Dai we came to realize our silly mistake and used the following command to change the user and group of the `authorized_keys` file.

    sudo chown user1:user1 authorized_keys

After this, the problem was resolved and a connection was put through.
=======

We encountered a significant roadblock stemming from a basic oversight on my part. When creating the `authorized_keys` file on Machine1, I mistakenly used `sudo nano authorized_keys`, resulting in the file being created with root ownership and group. Consequently, attempts to access it from the Starting Machine resulted in a "permission denied" error. We initially focused on setting appropriate permissions (`600` for `authorized_keys` and `700` for the `~/.ssh` directory) but overlooked the user and group ownership.

## Solution

After discussing with Saket Dai, we identified the oversight and rectified it by using the following command to change the user and group ownership of the `authorized_keys` file:

```bash
sudo chown user1:user1 authorized_keys
>>>>>>> origin/final
