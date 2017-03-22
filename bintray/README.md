## in root projext

>classpath 'com.novoda:bintray-release:0.4.0'//lastetest version see https://github.com/novoda/bintray-release

    allprojects {
      tasks.withType(Javadoc) {
          options{
              encoding "UTF-8"
              charSet 'UTF-8'
              links "http://docs.oracle.com/javase/7/docs/api"
          }
      }
    }
add 

    ext {
      userOrg = 'xcht1209'
      groupId = 'com.vinctor'
      publishVersion = '0.0.1'
      website = 'https://github.com/Vinctor/xxxxxxx'x
      licences = ['Apache-2.0']
    }



## in the library which will up to bintray
apply plugin: 'bintray-release'

    publish {
        artifactId = 'xxxxx'x
        userOrg = rootProject.userOrg
        groupId = rootProject.groupId
        publishVersion = rootProject.publishVersion
        desc = rootProject.description
        website = rootProject.website
        licences = rootProject.licences
    }

//if have the issue about lint

    lintOptions {
        checkReleaseBuilds false
        abortOnError false
    }
add the above code in the ```android``` of the app moudle 

## build
//with solving the issue ' Permission denied'
>chmod +x gradlew

//run
>./gradlew clean build bintrayUpload -PbintrayUser=xcht1209 -PbintrayKey=xxxxxxxxxxxxxxxxx -PdryRun=false
