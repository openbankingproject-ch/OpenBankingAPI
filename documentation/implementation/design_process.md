## Technology choices
### Java
Java was mainly chosen because of its robust type system and because in most open banking implementations
we analyzed Java was the language of choice. 

It also has a strong ecosystem and tooling for handling the security needs of an open banking project.

Java supports multi threading for doing cryptographic calculations in a non blocking way.

There is also a lot of developers that are familiar with Java. Java is also often used to teach programming
in Business Computer Science Programs.

### Maven
We chose Maven as the build system because we have more experience with it compared to Gradle.

### Javalin
Javalin was chosen because it is more lightweight than Spring which we determined was a positive aspect.
This is because the main complexity in the API is the security and consent flow. This means we want everything
that is not consent and security to be as simple as possible.

