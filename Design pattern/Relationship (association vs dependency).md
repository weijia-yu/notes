<!-- toc -->

- [Relationship (association vs dependency)](#Relationship-association-vs-dependency)
    + [Association](#Association)
    + [Dependency](#Dependency)

<!-- tocstop -->
# Relationship (association vs dependency)

### Association

Here a class A holds a class level reference to class B

```java
class Asset { ... }
class Player {
Asset asset;
public Player(Assest purchasedAsset) { ... } /*Set the asset via Constructor or a setter*/
}
```

### Dependency

you receive a reference to a class as part of a particular operation / method. 

```java
class Die { public void Roll() { ... } }
class Player
{
public void TakeTurn(Die die) /*Look ma, I am dependent on Die and it's Roll method to do my work*/
{ die.Roll(); ... }
}```

### Composition

When class B is composed by class A, class A instance owns the creation or controls lifetime of instance of class B. 


```java
public class Piece { ... }
public class Player
{
Piece piece = new Piece(); /*Player owns the responsibility of creating the Piece*/
...
}```