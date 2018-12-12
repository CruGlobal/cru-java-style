Cru Java Style
==============
The checkstyle rules that enforce (much of) [Cru's java style guide](https://docs.google.com/document/d/16TGhx6nL3d3cjN8Rmpo-oY55ErTSUT6sZx8RVDTpgJU/edit?usp=sharing).

This builds on top of Checkstyle's ruleset that enforces Google's style guide.
So rules that we've added on top of google's are not enforced here.



Usage in a maven project:

```xml
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-checkstyle-plugin</artifactId>
        <version>3.0.0</version>
        <configuration>
          <configLocation>cru_checks.xml</configLocation>
          <includeTestSourceDirectory>true</includeTestSourceDirectory>
        </configuration>
        <dependencies>
          <!-- the maven plugin's version is too outdated -->
          <dependency>
            <groupId>com.puppycrawl.tools</groupId>
            <artifactId>checkstyle</artifactId>
            <version>8.10.1</version>
          </dependency>

          <dependency>
            <groupId>org.cru.style</groupId>
            <artifactId>cru-java-style</artifactId>
            <version>0-SNAPSHOT</version>
          </dependency>
        </dependencies>
        <executions>
          <execution>
            <id>enforce-style</id>
            <phase>test</phase>
            <goals>
              <goal>check</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
```


Usage in intellij:

Install the CheckStyle-IDEA intellij plugin.
Run a maven build, so that maven-checkstyle-plugin creates a
target/checkstyle-checker.xml file.
Then point the intellij plugin to that file.

My wsapi .idea/checkstyle-idea.xml looks like this:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project version="4">
  <component name="CheckStyle-IDEA">
    <option name="configuration">
      <map>
        <entry key="active-configuration" value="PROJECT_RELATIVE:$PROJECT_DIR$/target/checkstyle-checker.xml:wsapi_checks" />
        <entry key="checkstyle-version" value="8.10.1" />
        <entry key="copy-libs" value="false" />
        <entry key="location-0" value="BUNDLED:(bundled):Sun Checks" />
        <entry key="location-1" value="BUNDLED:(bundled):Google Checks" />
        <entry key="location-2" value="PROJECT_RELATIVE:$PROJECT_DIR$/target/checkstyle-checker.xml:wsapi_checks" />
        <entry key="scan-before-checkin" value="false" />
        <entry key="scanscope" value="JavaOnlyWithTests" />
        <entry key="suppress-errors" value="false" />
      </map>
    </option>
  </component>
</project>
```

My config pane looks like this:
![screenshot of my checkstyle config](https://lh3.googleusercontent.com/II2OIYbchiGGXhDAGzdSAz5cb-t2-VXCWv-Y_AQtVZyZVSJNeoVWb12HlW68a3c_z5aIiX5H8aBsUZww9S8AKHsB8OFC14lJFXjT499XpSjfycldbITb6QRFeKjW5hocNy9fnCm8MKe2aqFyAlUH328oWBQqWRoSZa4P5E9sW03JM857hyPxxxe_TXMM56-gaX8M7w0Alr_ToiZ98cuc09VtF08_I1bTwxqcLuOt5azgR7TittmRcxQLPDEPxHoVwrBgslB9E4eynibp-O04nvFieSAEYnHrAa3HQxVjl9Bxt6dyr4Sk4-6r1sPbQhu27_AHoOTjjFXu5ayEMpCh-p0CdhEqg9-E5zj8y9hwkfGOZS-68u5gYJ4Y3QzfhIi11eEuhpgh5Ta-KHAG13BkEMeDKOd4ifRxt14QWHpqKYWxfDvpNSMA7W99nGrzudZ0EE3MTitmk0mH5KQSFIxCpyI1HpCYFBvEti_alti-OWRa0993qo7ax5p6_mhil41n1pJb9SONMdlXP5vUqsJkpeimrkobK1DbAQ-63PH5-AkLJ4DStGKgXOS7Iaiz8x2ujwT9HaPDdX2SRZQtrzY4zOLpMz7TBe3wvagvn-RCePFZ1hLS3ENXALXuU5PWtq_VXB8NR1kEmili-hl8UTu7D-ZAC0OwtSEkXUHm_0N13bxUORQDLiARaiV-UZ553wQ0Yvt2hny57ipOt0WmmA=w1440-h1058-no)

(Note that wsapi uses a slightly modified version of cru_checks.xml, called wsapi_checks.xml)
