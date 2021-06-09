# Gradle Properties Extraction Sample

A small demo of how you can extract Gradle project properties from the command line and then make use of them for scripting, CI workflows, etc

# List Gradle Project Properties

You can run the `properties` task of a Gradle project to list all of the Gradle project properties
`./gradlew properties`

# Listing A Specific Project Property

Gradle projects can have many project properties availalbe to them.

To help limit the output of the `properties` task, we can pipe the output into the grep command to search for output pertaining to a specific property.

For example, we could use the following command to list out the `version` property for a Gradle project

`./gradlew properties | grep ^version`

For a project where `version=1.2.3`, the output of the previous command would be `version: 1.2.3`


# Extracting Just The Version Name

Being able to list the specific version property is helpful, but if we want to extract just the actual version name - not the property name?  We might want this so we can use the version name for scripting purposes or for tagging a release in a CI workflow.

To further parse the output, we can use the `cut` command.

`./gradlew properties | grep ^version | cut -c 10-`

The output of this command would be `1.2.3`

We could then save this to an environment variable, pass it to a script, or use it for anything else that requires the project version.
