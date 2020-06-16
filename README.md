# Maven

Yiddish - "accumulator of knowledge"

A tool that handles our project's dependcies and it builds our application into an exectuable when its done.

Fairly universal - how one Maven project is built is how they're all built, so once you learn, its easy to see its similarities in other projects that use it.

POM.xml

- Project-Object-Model
- this is the file that defines our project and all of its dependencies

### Maven UIDs (Unique Identifiers)

groupID = Group or organization that the project belongs, offen expressed as a inverted domain name, ex: com.win

artifactID = name for the project, will be the name given to its library artifact (.JAR or .WAR file)

version = version of the project being built (0.0.1)

package = either JAR or WAR

### JAR and WAR

Simply zipped/compressed files after your program has been compiled.
Difference in package depends on what purpose your program is fulfilling

**JAR** = contains libraries, resources and accessories for an application
**WAR** = contains the web application that can be deployed to a server. Contains JSP, HTML, JS, etc. for the development of web applications.

### Adding a Manifest for your JAR file

We have to give the built-in maven-jar plugin in our `pom.xml` some configuration information so that it knows where your program's main() is for it to exectute.

Inside of the `<plugins>` section, find the `mavin-jar-plugin` and add the following under its artifactID and version:

```
...
<configuration>
    <archive>
        <manifest>
        // replace myPackage with the name of your own package
        <mainClass>com.myPackage.App</mainClass>
        </manifest>
    </archive>
</configuration>
```

## Setting up VS Code and Maven

1. Make sure you have set your JAVA_HOME environment variable on your computer: https://javatutorial.net/set-java-home-windows-10
2. In your VS Code settings.json add the following line:
   "java.home": "C:\\Program Files\\jdk"
   where the filepath is where your Java JDK is located
3. Download the "Binary zip archive" of Maven from here: https://maven.apache.org/download.cgi
4. Unzip the folder you just downloaded
5. In your VSC settings.json, add the following line:
   "maven.executable.path": "c:\\Program Files\\apache-maven-3.6.3-bin\\apache-maven-3.6.3\\bin\\mvn.cmd"
   where the filepath is to a file called `mvn.cmd` inside the folder you just unzipped
   (Note for MAC users - don't do `mvn.cmd`, just do `mvn`)
6. Save your settings.json file, close VSC and reopen it

## To compile and package your application as JAR file

1. Make sure you have the Java Language Extention Pack installed
2. In the Explorer sidebar, you should see a small window called "Maven Projects" where your Maven project is located.
3. Right click on it and select "compile" - this runs all of your code through the javac and creates .class files out of your .java files. You should see a "Build Succeded" message in your terminal when your app is done compiling.
4. Right click on your Maven project again and select "package". This will take your compiled code and zip it up into one complete package. You should see "Build Succeded" in your terminal again.
5. If your app was successfully packaged, you should have a JAR file inside your target folder named as `artifactID-Version.jar'.
6. To run this app, just run `java -jar /target/filename.jar` that was just created. You should see the output "Hello world!" in the terminal!
