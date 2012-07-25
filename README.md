Blazebit Parent POM
================
The parent POM for Blazebit community projects.

What is it?
-----------
The Blazebit parent POM provides default configuration for Blazebit Maven builds.
 
* Default versions for the most commonly used Maven plugins
* Manifest configuration for the jar and assembly plugins
* Profiles for generating source jars, and enforcing a minimum Maven version

How to use it?
--------------
Start out by adding the parent configuration to your pom.

    <parent>
      <groupId>com.blazebit</groupId>
      <artifactId>blazebit-parent</artifactId>
      <version>1</version>
    </parent>

Depending on the needs of your build, you can customize the plugins and other 
settings using properties.  For example, to override the default version of the
maven-compiler-plugin, just set a property.

    <properties>
      <version.compiler.plugin>2.3</version.compiler.plugin>
    </properties>

Or override the default Java compiler source and target level used in the build.  
Note the default level is 1.6.

    <properties>
      <maven.compiler.target>1.5</maven.compiler.target>
      <maven.compiler.source>1.5</maven.compiler.source>
    </properties>

For the full list of properties, refer to the POM itself.

The Release Profile
--------------------
This POM includes a Maven profile called "blazebit-release".  This profile includes 
settings for release deployment metadata and generating javadoc jar files.  The 
maven release plugin will automatically activate this profile during a release.  
Projects that do not use the maven release plugin must manually activate this 
profile during a release using "-Pblazebit-release", or something similar.

The GPG Sign Profile
--------------------
This POM includes a Maven profile called "gpg-sign" which provides default 
configuration to generate GPG signatures for the build artifacts.  This plugin 
requires that the properties "gpg.keyname" and "gpg.passphrase" are available to 
the current build.  These properties can either be set in a
build profile, or on the command line.

    <profile>
      <id>gpg-config</id>
      <properties>
        <gpg.keyname>me@home.com</gpg.keyname>
        <!-- Don't keep passphrase in plain text! -->
        <gpg.passphrase>secret</gpg.passphrase>
      </properties>
    </profile>

License
-------
* This software is in the public domain (The contents of this project have been taken from jboss-parent and adapted for Blazebit)