Create a new file name as :-  sudo vim apply_policies.sh
Make the script executable:   chmod +x apply_policies.sh
Run the script with sudo:     sudo ./apply_policies.sh



README - Password Authentication Issue (Summary)
Issue
After running a shell script to enforce password policies, login failed with the error:
"Sorry, password authentication didn’t work."

Cause
Improper edits to /etc/pam.d/common-auth and /etc/security/pwquality.conf.

Use of deprecated pam_tally2 module, causing authentication failures.

Solution (Summary)
Reboot and open the GRUB menu (press Shift or Esc at boot).

Boot into Recovery Mode and drop to root shell.

Remount filesystem:

mount -o remount,rw /
Restore backup files:


cp /etc/pam.d/common-auth.bak /etc/pam.d/common-auth
cp /etc/krb5.conf.bak /etc/krb5.conf
(Optional) Fix /etc/security/pwquality.conf if needed.

nano /etc/security/pwquality.conf
Remove or correct any lines manually (such as minlen=12 and minclass=3)

save amd exit: 
ctrl + o
enter
ctrl + X

Reboot the system:
reboot


Lesson
Always backup PAM files before changing.

Test security scripts carefully to avoid system lockout.
