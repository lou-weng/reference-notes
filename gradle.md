# Gradle

### Gradle Principles
* a task is an object
  * a task has a list of activities
* a Gradle build is...a program

### Gradle Tasks
* compile the java
* run tests
* copy static resources
* format test results
* build a JAR

### Gradle Commands

### Example Multi-Project Build
```
root
├── build.gradle
├── settings.gradle
├── src
│   └── main
│       └── java
│           └── org
│               └── hello
│                   └── Hello.java
├── content
│   ├── main
│   │   └── java
│   │       └── org
│   │           └── bye
│   │               └── Bye.java
│   └── test
│       └── java
│           └── org
│               └── bye
│                   └── ByeTest.java
└── codec
    ├── main
    │   └── java
    │       └── org
    │           └── salut
    │               └── Salut.java
    └── test
        └── java
            └── org
                └── salut
                    └── SalutTest.java
```

### Example Simple Build
```
root
└── src
    └── main
        └── java
            └── org
                └── hello
                    └── Hello.java

```

###### Run a task
> gradle [-q] \<taskname>
q means quiet

###### Build a project
> gradle build

###### Display all tasks
> gradle tasks

### Example build.gradle
```
task hello
task world
task helloworld

// include multiple dependencies
helloworld {
    dependsOn = [world, hello]
}

world {

    // dependency on a previous task
    dependsOn << hello

    doLast {
        println "World"
    }
}


// a task object
hello {

    // task API
    doLast {

        // task action
        println "Hello"
    }
}
```

### Example 2 build.gradle
```
apply plugin: 'java'

repositories {
    mavenCentral()
}

dependencies {
    compile 'commons-codec:commons-codec:1.6'
}

task doTask(type: JavaExec) {
    main = 'org.hello.Hello'
    classpath = sourceSets.main.runtimeClasspath
}
```

### Example 3 build.gradle 
```
// high-level command for entire project
allprojects {
    apply plugin: 'java'

    repositories {
        mavenCentral()
    }
}

// high-level dependencies
dependencies {
    compile project(':codec')
    compile project(':content')
}

project(':codec') {
    dependencies {
        testCompile 'junit:junit:4.9'
    }
}

project(':codec') {
    dependencies {
        compile 'commons-codec:commons-codec:1.6'
    }
}

task wrapper(type: Wrapper) {
    gradleVersion = '1.0'
}
```