# Depreciated

This project has been depreciated in favor of [MelonSmasher/VeeamChatNotifications](https://github.com/MelonSmasher/VeeamChatNotifications) which supports Slack, Mattermost, Teams, and Discord.

# Veeam Backup and Restore Notification for Slack

Sends notifications from Veeam Backup & Restore to Slack

![Chat Example](https://raw.githubusercontent.com/TheSageColleges/VeeamSlackNotifications/master/asset/img/screens/sh-2.png)


If you use Mattermost check this out:

* [Veeam Mattermost Notifications](https://github.com/TheSageColleges/MattermostVeeamNotifications)

---

## Setup

Make a scripts directory: `C:\VeeamScripts`

```powershell
# To make the directory run the following command in PowerShell
New-Item C:\VeeamScripts PowerShell -type directory
```

#### Get code

Then clone this repository:

```shell
cd C:\VeeamScripts
git clone https://github.com/TheSageColleges/VeeamSlackNotifications.git
cd VeeamSlackNotifications
git checkout v1-stable
```

Or without git:

Download release, there may be later releases take a look and replace the version number with newer release numbers.
Unzip the archive and make sure the folder is called: `VeeamSlackNotifications`
```powershell
Invoke-WebRequest -Uri https://github.com/TheSageColleges/VeeamSlackNotifications/archive/v1.0.zip -OutFile C:\VeeamScripts\VeeamSlackNotifications-v1.0.zip
```

Configure the project:

```shell
# Make a new config file
cp C:\VeeamScripts\VeeamSlackNotifications\config\vsn.example.json C:\VeeamScripts\VeeamSlackNotifications\config\vsn.json
# Edit your config file. You must replace the webhook field with your own slack url.
notepad.exe C:\VeeamScripts\VeeamSlackNotifications\config\vsn.json
```

Finally open Veeam and configure your jobs. Edit them and click on the <img src="https://raw.githubusercontent.com/TheSageColleges/VeeamSlackNotifications/master/asset/img/screens/sh-3.png" height="20"> button.

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
