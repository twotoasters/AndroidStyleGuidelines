## Two Toasters Android Coding Style Guidelines

#### Checkstyle

The Checkstyle code styling plugin is available for both Eclipse and Android Studio IDEs.

##### Eclipse

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

##### Android Studio

Install and setup the Checkstyle-IDEA plugin.

Plugin url: <http://plugins.jetbrains.com/plugin/1065>

- Download and install the latest version of the plugin
	1. Download the plugin to disk
	2. Open Android Studio and go to preferences
	3. IDE Settings > Plugins > Install plugin from disk (select file you downloaded)
	4. Once plugin is installed, it will ask you to restart studio

- Copy checkstyle.xml file to root of your project
- Create a symlink to the checkstyle.xml from the project root that contains the file

        mkdir -p config/checkstyle  
        ln -s ../../checkstyle.xml config/checkstyle/checkstyle.xml

- Activate Checkstyle in Android Studio IDE during new project setup
	1. Open Studio and go back to Preferences
	2. Go to Project Settings > Inspections and then search for Checkstyle
	3. Change the real time scan to severity type Error
	4. Go to Project Settings > Checkstyle
	5. Add a new configuration file
	6. Name it "checkstyle.xml"
	7. Select the checkstyle.xml file in root of the project
	8. Press the Next button
	9. Enter "bin/cachefile" as the property for "checkstyle.cache.file"
	10. Choose OK and activate the new config
	11. Hit apply and then OK
- Activate Checkstyle in Gradle build file: `build.gradle`
	1. Apply checkstyle plugin

            buildscript
                repositories {
                    mavenCentral()
                }
            }
          
            apply plugin: checkstyle

	2. Add checkstyle task

            task checkstyle(type: Checkstyle) {
                source 'src'
                include '**/*.java'
                exclude '**/gen/**'
    
                // empty classpath
                classpath = files()
            }

	3. Insert checkstyle task build step  

			preBuild.dependsOn('checkstyle')

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
