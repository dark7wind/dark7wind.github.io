# What is cron and crontab
__Cron__: The software utility cron is a time-based job scheduler in Unix-like
computer operating systems. Users that set up and maintain software environments
use cron to schedule jobs (commands or shell scripts) to run periodically at
fixed times, dates, or intervals. It typically automates system maintenance or
administration—though its general-purpose nature makes it useful for things like
downloading files from the Internet and downloading email at regular intervals.

__Crontab__: The actions of cron are driven by a crontab (cron table) file, a
configuration file that specifies shell commands to run periodically on a given
schedule. The crontab files are stored where the lists of jobs and other
instructions to the cron daemon are kept. Users can have their own individual
crontab files and often there is a system-wide crontab file (usually in /etc or
a subdirectory of /etc) that only system administrators can edit.



# Automatic running the Python script
__Operating system__: Ubuntu 18.04.3 LTS

__Preparation__: Check the Python script *e.g. test.py*
```python
#!/usr/bin/env/python
print('cron_test')
file = open('/home/username/test/cron_test.txt','w')
file.write('Hello World')
file.close()
```
note: use the full path. It takes me a lot of time in the begining to debug this
problem

__Step1: configure crontab file__<br>
Type `crontab -e` in the terminal. I use nano to edit. Other editors like \
vim can also be used \
```console
username@mypc:~$ crontab -e
```

__Step2: write the cron command__ <br>
Format: $PYTHONPATH $FILEPATH
```
* * * * /usr/bin/python /home/xiaowei/test/hello2.py
```
note:
* `/usr/bin/python` is the default Python. It can also be replaced by the path
e.g. `/home/username/anaconda3/envs/envname/bin/python` to use the Python in
other environments like Anaconda.
* A useful website helps to edit the cron schedule: https://crontab.guru/

__Step3: check if it works__
If it’s not running, you’ll get an error in the file `var/mail/$USERNAME`.
```console
username@mypc:~$ cd /var/mail
username@mypc:/var/mail$ nano $USERNAME
```

### Reference
1. https://en.wikipedia.org/wiki/Cron
2. https://www.youtube.com/watch?v=kL5rmcxwgSs
3. https://medium.com/@gavinwiener/how-to-schedule-a-python-script-cron-job-dea6cbf69f4e
4. https://www.adminschoice.com/crontab-quick-reference
