# Eclipse Setup #

We use the following tools for development:

  * [Eclipse](http://eclipse.org/) 3.7 or higher. We recommend the Eclipse Classic distribution.
  * [Subclipse](http://subclipse.tigris.org/) 1.6.x
    * update site: http://subclipse.tigris.org/update_1.6.x
  * [m2e](http://m2eclipse.sonatype.org/) 1.0.100.20110804-1717 or higher.
    * update site: http://m2eclipse.sonatype.org/sites/m2e
  * Maven SCM handler for Subclipse
    * update site: http://m2eclipse.sonatype.org/sites/m2e-extras

# Maven Setup #

This projects makes use of some libraries that are not readily available in public Maven repositories. Therefore we have set up a Maven repository which provides these libraries as well as releases of this project. To use this repository, we suggest you use the settings.xml in the hidden subdirectory .m2 of your home directory and augment it with the following sections:

```
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">
  <profiles>
    <profile>
      <id>ukp-oss-releases</id>
      <repositories>
        <repository>
          <id>ukp-oss-releases</id>
          <url>http://zoidberg.ukp.informatik.tu-darmstadt.de/artifactory/public-releases</url>
          <releases>
            <enabled>true</enabled>
            <updatePolicy>never</updatePolicy>
            <checksumPolicy>warn</checksumPolicy>
          </releases>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
        </repository>
      </repositories>
      <pluginRepositories>
        <pluginRepository>
          <id>ukp-oss-releases</id>
          <url>http://zoidberg.ukp.informatik.tu-darmstadt.de/artifactory/public-releases</url>
          <releases>
            <enabled>true</enabled>
            <updatePolicy>never</updatePolicy>
            <checksumPolicy>warn</checksumPolicy>
          </releases>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
        </pluginRepository>
      </pluginRepositories>
    </profile>
    <profile>
      <id>ukp-oss-snapshots</id>
      <repositories>
        <repository>
          <id>ukp-oss-snapshots</id>
          <url>http://zoidberg.ukp.informatik.tu-darmstadt.de/artifactory/public-snapshots</url>
          <releases>
            <enabled>false</enabled>
          </releases>
          <snapshots>
            <enabled>true</enabled>
          </snapshots>
        </repository>
      </repositories>
    </profile>
  </profiles>
  <activeProfiles>
    <activeProfile>ukp-oss-releases</activeProfile>
    <!-- Uncomment the following entry if you need SNAPSHOT versions. -->
    <!--activeProfile>ukp-oss-snapshots</activeProfile-->
  </activeProfiles>
</settings>
```

If you do not have _settings.xml_ file in your _.m2_ directory, just create one with exactly the same content as above. You can also use the _settings.xml_ provided in [Downloads section](http://code.google.com/p/uby/downloads/list) and copy it to your _.m2_ folder.

# Checking out #

  * Open the **SVN Repositories perspective** in Eclipse (Menu -> Window -> Show View -> Other... -> SVN -> SVN Repositories)
  * **Add** a SVN repository with the URL http://uby.googlecode.com/svn/de.tudarmstadt.ukp.uby
  * **Expand** the new repository node in the SVN Repositories view
  * Right-click on **trunk** and select **Check out as Maven project**
    * Note: if you do not see this menu item, make sure you have installed the Maven SCM handler for Subclipse.
  * (optional) Eclipse will create some of projects now. We recommend to group these projects into a working set:
    * Select **Next**
    * Check **Add project(s) to working set**
    * Click **More...**
    * Click **New...**
    * Double-click **Java**
    * Enter the working set name Uby
    * Click **Finish**
    * Click **OK**
    * Select the working set Uby from the working set drop-down box
    * **Note:** when you are completely through with these and the following steps, remember to go to the Package Explorer view. There is a small triangular icon in its top right corner. Click on that and select Top Level Elements -> Working Sets.
  * Click **Finish.**