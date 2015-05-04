# Warehouse 14
Supernatural artifacts collected by Ano-Tech Computers.

## Adding the warehouse to your POM
You can add the warehouse to your Maven POM as a repository for automatic dependency resolution.
```xml
<repositories>
  <repository>
    <id>warehouse14</id>
    <url>https://github.com/Ano-Tech-Computers/Warehouse14/tree/maven/</url>
  </repository>
</repositories>
```

## Adding your artifact to the warehouse
For an artifact to be supernatural, its POM must inherit from [our super POM *no.atc:super-pom*](no/atc/super-pom/), either directly or indirectly. For direct inheritance, you can add this parent declaration to your POM:
```xml
<parent>
  <groupId>no.atc</groupId>
  <artifactId>super-pom</artifactId>
  <version>1.0</version>
</parent>
```
Our super POM binds deployment to the warehouse to the *deploy* phase. It uses [Github Site Plugin](http://github.github.com/maven-plugins/site-plugin) to commit the artifact to the warehouse automatically. 

### Configuration
The only configuration required is authentication. A server entry with the ID *warehouse14* in your [Maven settings](https://maven.apache.org/settings.html) should contain your authentication credentials. See the example below and [the Github Site Plugin documentation](https://github.github.com/maven-plugins/site-plugin/authentication.html) for more information on storing your credentials for Github Site Plugin.
```xml
<servers>
  <server>
    <id>warehouse14</id>
    <password>Insert personal access (OAuth2) token here</password>
  </server>
</servers>
```
For more information on personal access tokens, see [this GitHub Help page](https://help.github.com/articles/creating-an-access-token-for-command-line-use/). The token will need the *public_repo* scope. It is also recommended that you [encrypt your Maven settings](https://maven.apache.org/guides/mini/guide-encryption.html).

### Indirect inheritance
The warehouse also provides some useful base POMs to simplify specific types of projects. They all inherit our super POM, and can be found in [the *no.atc* group](no/atc/) under names starting with *super-pom-*.

**For Maven to resolve our base POMs (including our super POM), you will also have to [add the warehouse to your POM](#adding-the-warehouse-to-your-pom).**
