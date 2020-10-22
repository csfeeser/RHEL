# MINI-RHCSA EXAM SOLUTION

Below are questions phrased in the way that they may appear on the RHCSA exam. You can complete these tasks in any order, BUT BE WARNED! Some steps require previous steps to have been completed first!

1. Ensure that all new users have an empty file named `shazbot.txt` in their home directory.

    `touch shazbot.txt /etc/skel/`
    
0. Create the following users: homer, marge, lisa, bart, maggie
    - Set homer's password as “duff”
    - Make homer's password expire after 12 days
    - Save the names of ALL users in this system to /home/centos/usernames.txt

    `useradd homer`

    `useradd marge`

    `useradd bart`

    `useradd maggie`

    `passwd homer`

    `passwd --maximum=12 homer`

    `cut -d : -f 1 /etc/passwd > /home/centos/usernames.txt`

0. Change the configuration for maggie so that all files created by maggie have this permission automatically: `rw-rw-rw-`
    
    `sudo echo "umask 000" >> /home/maggie/.bash_profile`
    
0. Save the names of all files that contain a number in the /etc directory to a file in /home/centos named "numberz.txt"

    `ls /etc/*[0-9]* > /home/centos/numberz.txt`

0. Copy /var/log/messages into your /home/centos/ directory
   - Create a symbolic link titled "logz" pointing to "messages"

    `cp /var/log/messages /home/centos/`
    
    `cd /home/centos/`
    
    `ln -s messages logz`

0. Put the /home/centos/ directory inside of a compressed archive.
   - Unzip the archive's contents into marge's home directory.

    `tar cvf challenge.tar /home/centos/`
    
    `cp challenge.tar /home/marge/`
    
    `cd /home/marge`
    
    `tar xvf challenge.tar`
    
0. Make two groups named `springfield` and `shelbyville`
    - homer and bart should be members of `springfield`, marge and lisa should be members of `shelbyville`.
    - Make a directory named home/centos/springfield. Members of `springfield` should be able to read and write files in this directory, but members of `shelbyville` can only read files.
    - Make a directory named home/centos/shelbyville. Members of `shelbyville` should be able to read and write files in this directory, but members of `springfield` can only read files.

    `groupadd springfield`

    `groupadd shelbyville`

    `usermod -aG springfield homer`

    `usermod -aG springfield bart`

    `usermod -aG shelbyville marge`

    `usermod -aG shelbyville lisa`

    `mkdir /home/centos/springfield`

    `mkdir /home/centos/shelbyville`

    `chown :springfield /home/centos/springfield/`

    `chown :shelbyville /home/centos/shelbyville/`

    `chmod 664 /home/centos/springfield/`

    `chmod 664 /home/centos/shelbyville/`

    If you went the extra mile with ACLS...

    `setfacl -R -m g:shelbyville:r /home/centos/springfield`

    `setfacl -m d:g:shelbyville:r /home/centos/springfield`

    `setfacl -R -m g:springfield:r /home/centos/shelbyville`

    `setfacl -m d:g:springfield:r /home/centos/shelbyville`
 
0. Create a new directory: /home/centos/handsoff/
    - Change ownership of this directory where the user is `homer` and the group is `springfield`.
    - Make it so that the only users that can delete files in this directory are either `homer` or the owner of the `springfield` group.

    `mkdir /home/centos/handsoff/`
    
    `chown homer:springfield /home/centos/handsoff`
    
    `chmod +t /home/centos/handsoff/`
    
0. Run the sleep 9999 command but START it as a background job.

    `sleep 9999 &`
    
0. Create a new local repository named `challenge`. Find out what package contains `seinfo` and add it to this repository.
    - Save the output of `yum repolist` to /home/centos/repoproof.txt.

    `mkdir /home/centos/challenge/`

    `cd /home/centos/challenge/`

    `yum provides */sepolicy`

    `yumdownloader python3-policycoreutils-2.9-9.el8.noarch`

    `createrepo /home/centos/challenge`

    `vim /etc/yum.repos.d/challenge.repo`

    ```
    [challengerepo]
    name=challenges cannot stop me!
    baseurl=file:/home/centos/challenge
    gpgcheck=0
    ```
    
    `yum repolist > /home/centos/repoproof.txt`
    
0. Using at, make the command logger `linux is easy!` occur 2 minutes from now.

    `at now + 2 minutes`
    
    `logger linux is easy!`
    
0. Using cron, set things up so that a backup of /home/maggie/ is made daily and stored in root's home directory.

    `crontab -e`
    
    ```
    30 2 * * * tar cvf /home/maggie/ /etc
    ```
    
0. Set up logrotate to keep files for 21 days and also to save the last 6 log files.

    Line 3: `weekly` change to `monthly`

    Line 6: `rotate 4` change to `rotate 6`
