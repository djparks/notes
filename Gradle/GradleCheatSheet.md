# Gradle Cheatsheet

## Body

defaultTasks 'doStartProcess', 'doStep2'

//task doStartProcess (dependsOn: ['doStep2', 'doStep3']) {
task doStartProcess (dependsOn: 'doStep2') {
    doLast {
        logger.info "$name - Now starting the process - OK!"
    }
}

task doStep2 {}

## Arguments:

`-i`  == Prints logger messages
`-PcommandLineProjectProp=commandLineProjectValue` == Sets Property and its Value

## Plugins

plugins {
    id 'java'
    id 'project-report'
}

task: htmlDependencyReport