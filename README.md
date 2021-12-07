# Cisco-DNA-Backup-Cleanup
Cisco DNA server side cleanup script.

Needed:
- Linux server for backup
- BASH

## 1. License

"Cisco-DNA-Backup-Cleanup" is a free application that can be used to cycle backups of Cisco DNA on the server side.

Copyright (C) 2021 Tom Slenter

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program. If not, see <http://www.gnu.org/licenses/>.

For more information contact the author:

Name author: Tom Slenter

E-mail: info@remotesyslog.com

## Usage:
Clone the git and change the variables to the correct path

1) git clone https://github.com/tslenter/Cisco-DNA-Backup-Cleanup
2) cd Cisco-DNA-Backup-Cleanup
3) chmod +x cleanup
4) ==== EDIT VARIABLES OF THE "cleanup" FILE ====
5) Add log rotation for the debug file:
Example:
#DNAC Rotation
/home/dnac/scripts/cleanup_debug.log{ <<<--- adjust path
  rotate 52
  maxsize 100M
  weekly
  missingok
  notifempty
  postrotate
  endscript
}
6) Add script to cron (crontab -e):
0 */12 * * * /home/dnac/scripts/cleanup

## Variables to edit and explanation:

DEBUG="/home/dnac/scripts/cleanup_debug.log" #Debug log location and filename
BACKUP_LOC="/home/dnac"                      #Location of the backup
FIND_LOC="/usr/bin/find"                     #Location of the "find" binary
TR_LOC="/usr/bin/tr"                         #Location of the "tr" binary
BACKUP_DAYS="+65"                            #Enter amount of days. Don't forget to add the +
