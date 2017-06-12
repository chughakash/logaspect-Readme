# Logging in Android using aspectJ

This project is a proof of concept trying out logging using aspect oriented techniques.
The project bases itself on an existing app(reach) and logs the activities, onPause, onResume methods clicked within those activities and also calculates the time spent by the user in those activities. Additionally it also logs the buttons clicked by the user while the app is in foreground.

The log messages can be seen by opening the android monitor in the cosole of android studio under the message "D/Class and Activity:".
eg. 

D/Class and Activity: Activity:STIC, Method Called:onPause, Time spent by user :7.918 seconds

D/Class and Activity: Landing onResume

The above example implies the method onPause has been executed in activity STIC and the time spent by the user in the activity "STIC" is 7.918 seconds and further the method onResume has been executed on the activity "Landing".


## Getting Started

Run the project in android studio and open up the android monitor console to check the log messages.

### Prerequisites

Android Studio and
Java

### Add the logging feature to an already built android application

Include the mavenCentral repository as a dependency in the build.gradle under Gradle Scripts.

Create a new logging module. for eg. log

Include a buildscript snippet in app.gradle and log.gradle to include the repository of mavenCentral and add the dependencies of aspectJtools and gradle build tools.

Include the aspectj compile dependency in the gradle file associated with the app and log modules.(compile 'org.aspectj:aspectjrt:1.8.1').

Add the code for build customization to include aspectJ compilation at runtime.This has to be added in the gradle files of the app and log modules.


Create a class in log module and include the logging logic by creating pointcut and advices.
For eg.


 // On Resume creating a pointcut.
 
    @Pointcut("execution(* *.onResume(..))")
    public void onClickResume(){
    }


    @Before("onClickPause()")
    public void onClickPause(JoinPoint joinPoint){
		// Include logic here
		}

Additional methods/events can be tracked by creating pointcuts and advices as demonstrated above.

## References 


[aspect-oriented-programming-in-android](https://fernandocejas.com/2014/08/03/aspect-oriented-programming-in-android/)

[HujiangTechnology gradle_plugin_android_aspectjx](https://github.com/HujiangTechnology/gradle_plugin_android_aspectjx)

[android AOP Example](https://github.com/android10/Android-AOPExample)

[aspectj-with-android-library](https://stackoverflow.com/questions/31142125/aspectj-with-android-library/31225630#31225630)

[aspect-oriented-with-aspectj-and-google-analytics](https://blog.egorand.me/going-aspect-oriented-with-aspectj-and-google-analytics/)

[user-guide#TOC-Shrinking-Resources](http://tools.android.com/tech-docs/new-build-system/user-guide#TOC-Shrinking-Resources)


## Acknowledgments

* Dr Kevin Gary
