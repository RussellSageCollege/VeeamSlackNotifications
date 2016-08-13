# Veeam Backup and Restore Notification for Slack

Sends notifications from Veeam Backup & Restore to Slack

![Chat Example](https://raw.githubusercontent.com/TheSageColleges/VeeamSlackNotifications/master/asset/img/screens/sh-2.png)

---

## Setup

Make a scripts directory: `C:\VeeamScripts`

```powershell
# To make the directory run the following command in PowerShell
New-Item C:\VeeamScripts PowerShell -type directory
```

Then clone this repository:

```shell
cd C:\VeeamScripts
git clone https://github.com/TheSageColleges/VeeamSlackNotifications.git
```

Configure the project:

```shell
# Make a new config file
cp C:\VeeamScripts\VeeamSlackNotifications\config\vsn.example.json C:\VeeamScripts\VeeamSlackNotifications\config\vsn.json
# Edit your config file. You must replace the webhook field with your own slack url.
notepad.exe C:\VeeamScripts\VeeamSlackNotifications\config\vsn.json
```

Finally open Veeam and configure your jobs. Edit them and click on the![Advanced](https://raw.githubusercontent.com/TheSageColleges/VeeamSlackNotifications/master/asset/img/screens/sh-3.png =100x28) button.

Navigate to the "Scripts" tab and paste the following line the script that runs after the job is completed:

```shell
Powershell.exe -File C:\VeeamScripts\VeeamSlackNotifications\SlackNotificationBootstrap.ps1
```

![screen](https://raw.githubusercontent.com/TheSageColleges/VeeamSlackNotifications/master/asset/img/screens/sh-1.png)

---

## Example Configuration:

Below is an example configuration file.

```shell
{
	"webhook": "https://hooks.slack.com/services/....",
	"channel": "#veeam",
	"service_name": "VeeamBot",
	"icon_url": "https://raw.githubusercontent.com/TheSageColleges/VeeamSlackNotifications/master/asset/img/icon/veeam_slack.png",
	"debug_log": false
}
```
