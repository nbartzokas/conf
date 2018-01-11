## OS X log rotation

This is a framework-agnostic, OSX-only way to rotate log files.

##### Setup

- Edit `com.COMPANY.APP.rotate.plist `
	- replace `/LOCATION/OF/rotate` with the abolute path to the `rotate` script
	- replace `/LOCATION/OF/syslog.conf` with the abolute path to `syslog.conf`

- Edit `syslog.conf`, replacing `/LOCATION/OF/logfile.log` with the abolute path to the log file to rotate
