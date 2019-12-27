# Configuration in Maven module

HTML documentation is generated from Markdown source on phase *site*. Plugin `maven-site-plugin` search for markdown files in directory *src/site/markdown/* and uses Velocity template file to generate HTML output. Output files are saved in directory *target/site/* directory.

## Example plugin configuration

```
<plugin>
   <artifactId>maven-site-plugin</artifactId>
   <configuration>
     <generateReports>false</generateReports>
     <templateFile>src/site/markdown-site.vm</templateFile>
     <relativizeDecorationLinks>false</relativizeDecorationLinks>
   </configuration>
   <dependencies>
     <dependency>
       <groupId>org.apache.maven.doxia</groupId>
       <artifactId>doxia-module-markdown</artifactId>
       <version>1.9</version>
     </dependency>
   </dependencies>
</plugin>
```

Template from file *src/site/markdown-site.vm* defines simple structure of every documentation page.

```
<html>
  <head>
    <meta charset="utf-8" />
  </head>
  <body>
    <a href="index.html">Home</a>
  	#*   *#$bodyContent
  </body>
</html>

```

Every page contains body - result of parsing markdown files (referenced as *$bodyContent*) and link to start page (rendered from *index.md*).

## References

* [Maven Site Plugin](http://maven.apache.org/plugins/maven-site-plugin/index.html)

* [Doxia Markup Languages](http://maven.apache.org/doxia/references/index.html)