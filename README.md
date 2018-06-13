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
