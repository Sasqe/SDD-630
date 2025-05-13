# Activity 1

- This is Activity 1...

Cheers! :beers:

## Fruits
1. Apples
     1. Red
     2. Yellow
     3. Green
2. Oranges
3. Pears

## Links / Images

[google](https://www.google.com)

[wikiBob](https://gitlab.com/bobby.estey/wikibob/-/blob/master/README.md)

![America's Flagship Seal](https://gitlab.com/bobby.estey/wikibob/-/raw/master/docs/icons/cv64AmericasFlagShip100x100.png)
![America's Flagship Seal](https://gitlab.com/bobby.estey/wikibob/-/raw/master/docs/icons/cv64AmericasFlagShip100x100.png "America's Flag Ship")

## Tables
|First Name|Last Name|
|--|--|
|Chris|King|
|Bobby|Estey|

```java
public class CodeBlock {
    public static void main(String[] args) {
        System.out.println("Code Block Example");
    }
}
```

```python
print("Hello world!")
```
```mermaid
---
title: MermaidJS - Class Diagram - Animal example
---
classDiagram
    note "From Duck till Zebra"
    Animal <|-- Duck
    note for Duck "can fly\ncan swim\ncan dive\ncan help in debugging"
    Animal <|-- Fish
    Animal <|-- Zebra
    Animal : +int age
    Animal : +String gender
    Animal: +isMammal()
    Animal: +mate()
    class Duck{
        +String beakColor
        +swim()
        +quack()
    }
    class Fish{
        -int sizeInFeet
        -canEat()
    }
    class Zebra{
        +bool is_wild
        +run()
    }
```
