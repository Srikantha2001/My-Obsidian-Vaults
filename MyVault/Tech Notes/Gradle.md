
## Installation

- For Linux : use <mark style="background: #D2B3FFA6;">SDKMan</mark>
- For windows, download the gradle zip and extract it to a folder. then add path to env

## Tasks

- Tasks are individual components that can be executed using gradle.
- There are many predefined tasks and new custom tasks can also be added.
	![[Pasted image 20240608233734.png]]
- New Custom tasks are defined in *build.gradle.kts* file
	```Kotlin
	tasks.register("sampleTask") {  
	    description = "Defined a sample task that just print hello :)"  
	    doLast {  
	        println("Hello Gradle from sample task doFirst")  
	    }  
	}
	```
	
### Task Dependencies

- Some tasks maybe dependent on another task. so when `gradle build <task_name>` is called then it first executes all the dependent tasks before executing the task.
	![[Pasted image 20240609000632.png]]
	
- For the above task dependency, the <mark style="background: #FFB86CA6;">DSL</mark> code (Kotlin) is as below
```Kotlin
// TASK 1

tasks.register("task-1") {
    doFirst {
        println("doFirst of Task 1")
    }
    doLast {
        println("doLast of Task 1")
    }
}

// TASK 2

tasks.register("task-2") {
    dependsOn("task-1")
    doFirst {
        println("doFirst of Task 2")
    }
    doLast {
        println("doLast of Task 2")
    }
}

// TASK 3

tasks.register("task-3") {
    dependsOn("task-1")
    doFirst {
        println("doFirst of Task 3")
    }
    doLast {
        println("doLast of Task 3")
    }
}

// TASK 4

tasks.register("task-4") {
    dependsOn("task-3","task-5")
    doFirst {
        println("doFirst of Task 4")
    }
    doLast {
        println("doLast of Task 4")
    }
}

// TASK 5

tasks.register("task-5") {
    doFirst {
        println("doFirst of Task 5")
    }
    doLast {
        println("doLast of Task 5")
    }
}
```

- when above tasks is executed, the following result is obtained
![[Pasted image 20240609001844.png]]  ![[Pasted image 20240609001902.png]]

## Plugins 

- Gradle Plugins are just like maven plugin, that provides predefined tasks for execution
- there are 2 types of plugins :
	- well-known plugins (Core Plugins) Ex: Java
	- Community Plugins : Ex: Liquibase
- For Community Plugins, we should mention the version and full name in id.
- Sample code
```Kotlin
plugins {  
    id("java")  
    id("org.liquibase.gradle").version("2.2.2")  
}
```
- For gradle-plugin information : https://plugins.gradle.org/ 
## Gradle Commands

- For executing a task , 
```Shell
	gradle <task_name>
```
- For building the project
```Shell
	gradle -i build # -i provide extra information about build and what tasks are executed
```
