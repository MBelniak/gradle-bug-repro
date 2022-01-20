# gradle-bug-repro
Reproduction of the case, where DependencyReportTask does not list all dependencies.

Steps:
1. Remove org.codehaus.groovy/groovy-dateutil from your .gradle/caches/modules-2/files-2.1.
2. Run in console:
```
git clone git@github.com:MBelniak/gradle-bug-repro.git && \
cd gradle-bug-repro/buildSrc && \
../gradlew build -i | grep groovy-dateutil
```
You will see the output like:
`Downloading https://plugins.gradle.org/m2/org/codehaus/groovy/groovy-dateutil/3.0.9/groovy-dateutil-3.0.9.jar to /home/mbelniak/.gradle/.tmp/gradle_download6149274211781746870bin`
```
../gradlew allDeps | grep groovy-dateutil
```
No output - report does not say anything about groovy-dateutil, even though it's needed for compiling the groovy file.
