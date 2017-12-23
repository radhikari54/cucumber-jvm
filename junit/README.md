Cucumber JUnit 
==============

Use JUnit to execute cucumber scenarios.

Add the `cucumber-junit` dependency to your pom.

```xml
<dependencies>
  [...]
    <dependency>
        <groupId>io.cucumber</groupId>
        <artifactId>cucumber-junit</artifactId>
        <version>${cucumber.version}</version>
        <scope>test</scope>
    </dependency>
  [...]
</dependencies>
```

Create an empty class that uses the Cucumber JUnit runner.

```java
package com.example;

import cucumber.api.CucumberOptions;
import cucumber.api.junit.Cucumber;
import org.junit.runner.RunWith;

@RunWith(Cucumber.class)
@CucumberOptions(plugin = "json:target/cucumber-report.json")
public class RunCukesTest {
}
```

This will execute all scenarios in the package of the runner. By default glue code is assumed to be in the same 
package. The `@CucumberOptions` can be used to provide additional configuration to the runner.

## Using JUnit Rules ##

Cucumber supports JUnits `@ClassRule`, `@BeforeClass` and `@AfterClass` annotations. These will be invoked around the 
suite of features. Using these is not recommended as it limits the portability between different runners. Instead it is
recommended to use Cucumbers `Before` and `After` hooks to setup scaffolding.

## Using other JUnit features ##

The Cucumber runner acts like a suite of a JUnit tests. As such other JUnit features such as Categories, Custom JUnit 
Listeners and Reporters can all be expected to work.

For more information on JUnit, see the {{{http://www.junit.org}JUnit web site}}.
