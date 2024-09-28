---
title: S.O.L.I.D. with examples
date: 2021-05-08 16:56:54
categories: design-pattern
keywords: kotlin
---

### S)ingle Responsibility Principle
*A class should have one, and only one, reason to change.*
A class should have a single responsibility within the software.

Bad Example:
```kotlin
class User {
    fun save() {
        // Logic to save user to the database
    }

    fun sendEmail() {
        // Logic to send email to the user
    }
}
```
Good Example:
```kotlin
class User {
    fun save() {
        // Logic to save user to the database
    }
}

class EmailService {
    fun sendEmail(user: User) {
        // Logic to send email to the user
    }
}
```

### O)pen Closed Principle
*You should be able to extend a class's behavior without modifying it.*
Objects should be open for extension but closed for modification.

Bad Example:
```kotlin
class Rectangle(val width: Double, val height: Double) {
    fun area(): Double {
        return width * height
    }
}

class Circle(val radius: Double) {
    fun area(): Double {
        return Math.PI * radius * radius
    }
}
```
Good Example:
```kotlin
interface Shape {
    fun area(): Double
}

class Rectangle(val width: Double, val height: Double) : Shape {
    override fun area(): Double {
        return width * height
    }
}

class Circle(val radius: Double) : Shape {
    override fun area(): Double {
        return Math.PI * radius * radius
    }
}
```

### L)iskov Substitution Principle
*Derived classes should be substitutable for their base classes.*
The Liskov Substitution Principle was introduced by Barbara Liskov in 1987:
"If for every object o1 of type S there is an object o2 of type T such that for all programs P, the behavior of P is unchanged when o1 is substituted by o2, then S is a subtype of T."

Bad Example:
```kotlin
open class Bird {
    open fun fly() {
        println("Flying")
    }
}

class Ostrich : Bird() {
    override fun fly() {
        throw Exception("Ostriches can't fly")
    }
}
```
Good Example:
```kotlin
open class Bird {
    open fun makeSound() {
        println("Chirp")
    }
}

class Sparrow : Bird() {
    override fun makeSound() {
        println("Chirp chirp")
    }
}

class Ostrich : Bird() {
    override fun makeSound() {
        println("Hiss")
    }
}
```

### I)nterface Segregation Principle
*Make interfaces that are client-specific.*
A class should not be forced to implement interfaces and methods that will not be used.

Bad Example:
```kotlin
interface Machine {
    fun print()
    fun scan()
    fun fax()
}

class Printer : Machine {
    override fun print() {
        // Logic to print
    }

    override fun scan() {
        throw UnsupportedOperationException("Printer cannot scan")
    }

    override fun fax() {
        throw UnsupportedOperationException("Printer cannot fax")
    }
}
```
Good Example:
```kotlin
interface Printer {
    fun print()
}

interface Scanner {
    fun scan()
}

class SimplePrinter : Printer {
    override fun print() {
        // Logic to print
    }
}

class MultiFunctionPrinter : Printer, Scanner {
    override fun print() {
        // Logic to print
    }

    override fun scan() {
        // Logic to scan
    }
}
```

### D)ependency Inversion Principle
*Depend on abstractions, not on concretions.*
A high-level module should not depend on low-level modules; both should depend on abstractions.

Bad Example:
```kotlin
class EmailService {
    fun sendEmail(message: String) {
        // Logic to send email
    }
}

class Notification {
    private val emailService = EmailService()

    fun notify(message: String) {
        emailService.sendEmail(message)
    }
}
```
Good Example:
```kotlin
interface MessageSender {
    fun send(message: String)
}

class EmailService : MessageSender {
    override fun send(message: String) {
        // Logic to send email
    }
}

class Notification(private val sender: MessageSender) {
    fun notify(message: String) {
        sender.send(message)
    }
}

// Usage
val emailService = EmailService()
val notification = Notification(emailService)
notification.notify("Hello, World!")
```
