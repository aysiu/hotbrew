# hotbrew
hotbrew looks to keep particular brew-installed apps up to date using brew, run as the user (not root). It uses the Munki "managed updates" principle of not installing an app if it's not installed but keeping an app up-to-date (at least to the desired minimum version) if it is installed.
## hotbrew parts
### script
The script is a fairly simple self-contained script in `/usr/local/hotbrew/hotbrew`. For the purposes of initial testing, I've used `#!/usr/bin/python3`, but you may not have that installed, or you may prefer your own relocatable Python. Adjust as you see fit.
### launch agent
There is a launch agent that will run hotbrew once a day. Feel free to tweak the launch agent's `StartCalendarInterval`
### logs
hotbrew will log to `~/Library/Logs/hotbrew.log`
### config file
The config file should live in `/Library/hotbrew/managed_updates.plist`. You can see an example of it in `managed_updates_EXAMPLE.plist` right next to this README file. Obviously, you'd modify it to suit your needs and then deploy it using Chef, Munki, or some other configuration management tool.
## making a package
Use [munkipkg](https://github.com/munki/munki-pkg) to build the project. If you prefer a point-and-click custom package maker, check out [Packages](http://s.sudre.free.fr/Software/Packages/about.html), but you'll have to do some manual reconstruction of the payload and project.
## support?
There is no support for this project at this time. Right now, it's honestly proof-of-concept, but maybe people will find it useful.