# MINI-RHCSA EXAM

Below are questions phrased in the way that they may appear on the RHCSA exam. You can complete these tasks in any order, BUT BE WARNED! Some steps require previous steps to have been completed first!

1. Ensure that all new users have an empty file named `shazbot.txt` in their home directory.

0. Create the following users: homer, marge, lisa, bart, maggie
    - Set homer's password as “duff”
    - Make homer's password expire after 12 days
    - Save the names of ALL users in this system to /home/centos/usernames.txt

0. Change the configuration for maggie so that all files created by maggie have this permission automatically: `-r-xr-xr-x` †

0. Save the names of all files that contain a number in the /etc directory to a file in /home/centos named "numberz.txt"

0. Copy /var/log/messages into your /home/centos/ directory
   - Create a symbolic link titled "logz" pointing to "messages"

0. Put the /home/centos/ directory inside of a compressed archive.
   - Unzip the archive's contents into marge's home directory.

0. Make two groups named `springfield` and `shelbyville`
    - homer and bart should be members of `springfield`, marge and lisa should be members of `shelbyville`.
    - Make a directory named home/centos/springfield. Members of `springfield` should be able to read and write files in this directory, but members of `shelbyville` can only read files.
    - Make a directory named home/centos/shelbyville. Members of `shelbyville` should be able to read and write files in this directory, but members of `springfield` can only read files.

0. Create a new directory: /home/centos/handsoff/
    - Change ownership of this directory where the user is `homer` and the group is `springfield`.
    - Make it so that the only users that can delete files in this directory are either `homer` or the owner of the `springfield` group.

0. Run the sleep 9999 command but START it as a background job.

0. Create a new local repository named `challenge`. Find out what package contains `seinfo` and add it to this repository.
    - Save the output of `yum repolist` to /home/centos/repoproof.txt.

0. Using at, make the command logger `linux is easy!` occur 2 minutes from now.

0. Using cron, set things up so that a backup of /home/maggie/ is made daily and stored in root's home directory.

0. Set up logrotate to keep files for 21 days and also to save the last 6 log files.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

† (it's not actually possible to create files with execute permission by default!)
