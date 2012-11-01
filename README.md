Usage
-----
Add the following to your build.gradle file and replace the coberturaPluginVersion variable with the version of the plugin you wish to use

    buildscript {
        apply from: 'https://github.com/valkolovos/gradle_cobertura/raw/master/repo/gradle_cobertura/gradle_cobertura/${coberturaPluginVersion}/coberturainit.gradle'
    }

Compatibility
-------------

    +----------------+--------------+
    |Gradle Version  |Plugin version|
    +----------------+--------------+
    |1.1             |1.2.1         |
    +----------------+--------------+
    |1.0-milestone-9 |1.2           |
    +----------------+--------------+
    |1.0-milestone-8 |1.1           |
    +----------------+--------------+
    |1.0-milestone-7 |1.0           |
    +----------------+--------------+
    |1.0-milestone-6 |1.0-rc4       |
    +----------------+--------------+
    |All older revs  |1.0-rc4       |
    +----------------+--------------+

This will add the 'cobertura' task to your project which instruments your code, executes your tests and outputs to build/reports/cobertura.

Building
--------
To build from source:

    ./gradlew uploadArchives

This will create a local jar which you can reference in your builds like this:

    buildscript {
        repositories {
            add(new org.apache.ivy.plugins.resolver.FileSystemResolver()) {
                name = 'local_cobertura' // or whatever you want to put here
                addArtifactPattern '${ cobertura project directory }/repo/[organization]/[module]/[revision]/[artifact]-[revision].[ext]' // replace 'cobertura project directory' with real directory
                addIvyPattern '${ cobertura project directory }/repo/[organization]/[module]/[revision]/ivy.xml'
            }
        }
        dependencies {
            classpath 'gradle_cobertura:gradle_cobertura:1.0-rc4'
        }
    }

