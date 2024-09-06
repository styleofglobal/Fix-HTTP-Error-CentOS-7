# Fix-HTTP-Error-CentOS-7
Fix HTTP Error 404 Not Found Trying Other Mirror CentOS 7

Table of Contents
HTTP Error 404 Not Found Trying Other Mirror CentOS 7

Sometimes, you get the following errors when trying to refresh the update repositories on CentOS 7.


You got it because CentOS 7 is at the end of its support. To temporarily resolve this error for installation. You can change the mirrors as follows in the repo files for use.

1. SSH to your Linux server using an administrative account.

2. Run the following commands to search and replace the mirrors:
``sudo sed -i s/mirror.centos.org/vault.centos.org/g /etc/yum.repos.d/*.repo``

``sudo sed -i s/^#.*baseurl=http/baseurl=http/g /etc/yum.repos.d/*.repo``

``sudo sed -i s/^mirrorlist=http/#mirrorlist=http/g /etc/yum.repos.d/*.repo``

``sudo -- bash -c 'echo "sslverify=false" >> /etc/yum.conf'``

The commands explanation:

    Command 1: This command finds and replaces all occurrences of mirror.centos.org with vault.centos.org in all .repo files in the /etc/yum.repos.d/ directory.
    This can help access old CentOS repositories when major mirrors are unavailable.
    Command 2: This command finds and removes the # sign at the beginning of lines containing baseurl=http in all .repo files in the /etc/yum.repos.d/ directory.
    This enables baseurl usage instead of disabling it.
    Command 3: This command adds a # sign to the beginning of lines containing mirrorlist=http in all .repo files in the /etc/yum.repos.d/ directory.
    This disables the use of mirrorlist.
    Command 4: This command adds the line sslverify=false to the end of the /etc/yum.conf file.
    This turns off SSL checking when using yum, which can help overcome problems related to SSL certificates

3. Once done, please perform yum update or yum install to check the results.


https://bonguides.com/fix-http-error-404-not-found-trying-other-mirror-centos-7/?feed_id=1094&_unique_id=6697806adee10
