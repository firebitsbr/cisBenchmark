#cisBenchmark
Script to implement recommendations of CIS CentOS Linux 7 Benchmark Guide by Tom O'Flynn:
This script automates the recommendations of the CIS CentOS Linux 7 Benchmark PDF (see https://www.cisecurity.org/benchmark/centos_linux/). It is desinged to be run on a fresh minimal install.
While the script will probably work on most of the latest RedHat variants (and possible other Linux releases) it has only ben tested on a minimum install of CentOS 7 (CentOS release 7.6.1810 (Core) to be exact) with the following separate partitions:
/tmp
/var/
/var/tmp
/var/log
/var/log/audit
/home
The author makes no claims to originality as all the settings are directly taken from the above mentioned guide. Furthermore, much of the bash code has been written after consultation with online sources (particularly https://stackoverflow.com). Finally, similar scripts are no doubt available elsewhere so anyone interested in this work is encouraged to investigate other options. The author created this script partly because it is a good learning experience but more so because he felt more comfortable working with code of his own creation. In the event of there being a programming error it can be easier to troubleshoot code you have written yourself than somebody else's work.
At present there are a number of folders containing files which are consulted by the code. These will be tidied up in futre but at present they consist of the following folders:
1. backupFiles - before any system files are modified they are backed up to this folder. Files are given the name <originalName>.<date/time> where <date/time> takes the form of dd-mm-yy:hour:minute:second and represents the time at which the script was run. 
2. inputFiles - this folder contains files which are read by the code when running commands. For example the yumInstall/yumRemove files list packages to be installed or removed by the yum command. These files can be modified in advance of running the code.
3. network - this folder contains files which list modules from ip (versions 4 and 6) which are enabled/disabled by the code. These files can be modified in advance of running the code.
4. newFiles - when this script was originally written system files which needed to be modified were directly altered by the code. At a later stage the author felt it might be better to simply prepare some files in advance and overwrite the originals. As mentioned in point 1 above all original files can be found in the backupFiles folder with a date and time stamp appended to their names. 
5. outputFiles - as the code runs information about modifications made are saved to a file in this folder. The filename is info.<date/time> where <date/time> takes the same format as given in point 1 above. It is envisaged that other outputFiles will be produced by future versions of the code (see "Future Work" below).

Future Work:
1. At present standard error and most of standard out are redirected to /dev/null. Upon reflection this has been deemed a bad decision so future releases will redirect them to separate log files to be saved in the outputFiles folder
2. The script was written in the author's limited spare time over an extended period of time. This has resulted in an inconsistent style. For example in some cases system files are modified directly while in others they are simply overwritten. At some stage when time permits the author intends to rewrite the script in a more consistent style.
3. At present the code only implements recommendations of the CIS Benchmark PDF. This is obviously not the sole source of information so it may be good practice to mine other sources for security recommendations.
4. At present there are a number of settings not automated by the code. These will hopefully be included in furture. The info.<date/time> file saved in outputFiles contains information about these settings but they are reproduced here:
(a) Automatic updates are not configured and need to be set up manually
(b) Time synchronisation is not configured and needs to be set up manually
(c) The script does not check that password change dates are in the past
(d) Wireless interfaces are not inspected
(e) Neither ntp nor chrony are installed
