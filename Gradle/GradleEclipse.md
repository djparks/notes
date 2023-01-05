# Setting up Gradle in Eclipse

minGradleRequirements

task ('hello').doLast {
  println "Hello World"
}

Window -> Show View -> Other -> Gradle -> Gradle Tasks
Right Click Project -> configure -> Add Gradle Nature
Create new Run configuration: Gradle Task; new 

Eclipse Buildship

Gradle Error Marker
The supplied phased action failed with an exception

## Lifecycle Phases

1. Initializtion
2. Configuration
3. Execution

## Eclipse 
Arguments/Parameters: in run configuration on *Arguments tab*, Program Arguments
Gradle Tasks: List under *Gradle Tasks* tab.
