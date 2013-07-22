## Two Toasters Android Coding Style Guidelines

#### Checkstyle

Install and setup the Checkstyle Eclipse plugins.
	
Update site: <http://eclipse-cs.sourceforge.net/update/>
	
- Install both plugings from the update site
- Copy checkstyle.xml file to root of your project
- Activate Checkstyle during new project setup
	1. Right click project > Properties then choose Checkstyle from left side
	2. Enable "Checkstyle active for this project"
	3. Enable "Use simple configuration"
	4. Switch to "Local Check Configuration" tab
	5. Add a New local configuration
		- Set type: project relative configuration
		- Set name: "checkstyle xml file"
		- Set location: root of project
	6. Fix unresolved items
		- Click additional properties button
		- Click find unresolved properties button
		- Declare "checkstyle.cache.file" as "bin/cachefile"
	7. Switch to "Main" tab
	8. Set the configuration to use to the "checkstyle xml file" local config
	9. Exclude files outside the source directories & from packages "gen"

#### Save Actions

Enable save actions in the global workspace preferences.

1. Eclipse > Preferences
2. Java > Editor > Save Actions
3. Enable "Perform selected actions on save"
4. Enable "Organize imports"
5. Enable "Additional actions"
6. Configure additional actions
7. Enable the following:
	- Remove trailing whitespace
	- Remove unused imports
	- Remove unnecessary casts
	- Add missing annotations
		- Add missing overrides
		- Add missing deprecated

#### Eclipse Text Editor

In the global workspace preferences, there are a few settings to check.

1. Eclipse > Preferences
2. General > Editors > Text Editors
3. Set "Displayed tab width" to 4
4. Enable "Insert spaces for tabs"

#### Eclipse Formatter

You can create a formatter profile based on your checkstyle settings.

1. Right click your project name > Checkstyle > Create Formatter profile
2. Choose workspace or project settings > Java > Code Style > Formatter
3. Set the "Active Profile" to the profile for your project (e.g. eclipse-cs JazzyListView)
