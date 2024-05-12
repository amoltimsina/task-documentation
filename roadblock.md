# Roadblock 
## Major Issue
 We encountered with a roadblock which was a silly rookie mistake of mine. When creating an `authorized_key` file in `Machine1` I was apparently using `sudo nano authorized_key` which due to the use of `sudo` created the file under owner and group `root`. This created a problem of "permission denied" when trying to access from the `Starting Machine`. We overlooked the group and owner and focused more on the permission side, which we had assigned `600` for `authorized_keys` and `700` for the directory `~/.ssh`. 

## Solution
After a meeting with Saket Dai, we came to realize our silly mistake and used the following command to change the user and group of the `authorized_keys` file.

    sudo chown user1:user1 authorized_keys

After this, the problem was resolved and a connection was put through.
