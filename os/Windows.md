# Windows Provisioning

##### Configuration

- Settings\System\Notifications & actions\
	- turn off all notifications
- Settings\System\Power & sleep\
	- screen = never
	- sleep = never
- Settings\System\Offline maps\
	- Map Updates \ Automatically update maps = off
- Settings\System\Default apps\
	- Web browser = Google Chrome
- Settings\Devices\Bluetooth\More bluetooth options\
	- Uncheck "Alert me when a new Bluetooth device wants to connect"
	- Uncheck "Show the Bluetooth icon in the notification area"
- Settings\Devices\Autoplay\
	- Autoplay = off; take no action, take no action
- Settings\Devices\USB\
	- Notify me if there are issues connecting to USB devices = off
- Settings\Accounts\Sign-in options\
	- Require sign-in = never
- Settings\Privacy\Feedback & diagnostics\
	- Feedback frequency\Windows should ask for my feedback = never
- Settings\Update & security\Windows Update\Advanced options
	- Choose how updates are installed = Notify to schedule restart
	- Check "Defer upgrades"
- Settings\Update & security\Windows Defender\
	- Cloud based protection = off
	- Automatic sample submission = off
- Hit windows button and enter: netplwiz
	- Uncheck "Users must enter a user name and password to use this computer"

- Desktop Icon Settings
	- Uncheck everything under "Desktop Icons"

- Disable Apple Software Update
  - Click the Windows Start button in the lower-left corner and type task scheduler in the Start Search box. Open the “Task Scheduler“.
  - Expand the “Task Schedule Library” section.
  - Select the “Apple” folder.
  - Right-click “AppleSoftwareUpdate” and select “Disable” or “Delete“.

- Disable automatic updates (as shown [here](http://www.howtogeek.com/224471/how-to-prevent-windows-10-from-automatically-downloading-updates/))
  - Hit win+R, and enter "gpedit.msc"
  - Navigate to Computer Configuration\Administrative Templates\Windows Components\Windows Update
  - Locate the “Configure Automatic Updates” setting in the right pane and double-click it. Set it to “Disabled"

- Win+R, then enter "shell:startup"
  - Create shortcut to your App in that folder

- Win+R, enter "taskschd.msc" to run Task Scheduler
  - disable all unneeded

- Win+R, enter "taskschd.msc"
  - Select "Task Scheduler Library"
  - In menu bar, click Action\New Folder...; name it AMNH-NWC
  - Select "AMNH-NWC"
  - In menu bar, click Action\Create Basic Task...
	  - Name: Restart, next
	  - Trigger: Daily, next
	  - Start: Midnight, next
	  - Action: Start a program, next
	  - Program: "shutdown /r", next, yes
	  - Finish

- On first run of an app that accesses the internet or starts a server, Windows Security Alert pops up, check all and click "Allow Access"

- From system tray, open Boot Camp Control Panel
	- on Power tab, check "Restart automatically after a power failure"

- (once touch is plugged in) Start \ "Pen and Touch" \ "Show visual feedback when touching the screen"; enable/disable as desired
- (once touch is plugged in) Start \ "Pen and Touch" \ "Press and Hold Settings" \ Enable... = false

- Win + "regedit"
  - In `[HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\ImmersiveShell]`
  - Add this value `SignInMode = 1` (means by default signin will "Go to the desktop" instead of tablet mode)

- Install KNAS Restarter; configure with:
	- monitor interval of 3 seconds

- Scheduled Startup is handled through BIOS
	- Most Motherboards have a Power Management Tab with "Power by RTC" option
		- Asus Z-170/Z-270: Advanced Mode > Advanced > APM > Boot on RTC
