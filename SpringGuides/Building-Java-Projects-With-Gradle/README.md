# Building Java Project with Gradle
[spring tutorial for build java project with gradle](https://spring.io/guides/gs/gradle/)

## Before the start Tutorial What is Maven and Gradle.

> There is many build up tools, typically the make command used for Building c code.
> For Build Java code Ant, Maven, Gradle is used.
> In this tutorial build up the java project with gradle So you don't have to take closer.
> One thing you have to know is "Gradle is build up tools for JavaProject".
>
> Here is some link explain about Ant, Maven, Gradle
>[what is Ant, Maven, Gradle](https://technologyconversations.com/2014/06/18/build-tools/)


### Let's start tutorial

1. Make folder for java project.

>> <cmd> mkdir -p src/main/java/hello <cmd>


2. Make two .java file

>> touch Hello.java


<pre>
<code>
package hello;

public class HelloWorld {
  public static void main(String[] args) {
    Greeter greeter = new Greeter();
    System.out.println(greeter.sayHello());
  }
}</code>
</pre>

>> touch Greeter.java

<pre>
<code>
package hello;

public class HelloWorld {
  public static void main(String[] args) {
    Greeter greeter = new Greeter();
    System.out.println(greeter.sayHello());
  }
}</code>
</pre>

3. Install gradle

>> I recommand to using package installer.
>> I'm using Mac OS so i just download using Homebrew

>> <cmd> brew install gradle</code>

4. Make configuration file build.gradle

* check you Java version

>> touch build.gradle

<pre>
<code>
apply plugin: 'java'
apply plugin: 'application'

mainClassName = 'hello.HelloWorld'

sourceCompatibility = your_java_version
targetCompatibility = 11.0

jar {
    baseName = 'gs-gradle'
    version =  '0.1.0'
}
</code>
</pre>

5. Build the project with gradle wrapper


- Before the build project check your version of gradle

<pre>

 gradle -v
 gradle wrapper --gradle-version your_version

 ./gradlew build
 ./gradlew run

</pre>



### Add dependency of library

 - If i using other library in HelloWorld.java like this

 <pre>
 <code>
 package hello;

import org.joda.time.LocalTime;

public class HelloWorld {
  public static void main(String[] args) {
    LocalTime currentTime = new LocalTime();
    System.out.println("The current local time is: " + currentTime);

    Greeter greeter = new Greeter();
    System.out.println(greeter.sayHello());
  }
}
 </code>
 </pre>


- We can declear about this dependency in build.gradle file.

<pre>
repositories {
    mavenCentral()
}

'''

dependencies {
    compile "joda-time:joda-time:2.2"
    testCompile "junit:junit:4.12"
}
</pre>
