# S.O.L.I.D. Principles

## Futher Reading

- [A Simple Way to Understand SOLID Principles](https://dev.to/kevin-uehara/solid-the-simple-way-to-understand-47im?ref=dailydev) by Kevin Uehara

## Table of Contents

- [S.O.L.I.D. Principles](#solid-principles)
  - [Futher Reading](#futher-reading)
  - [Table of Contents](#table-of-contents)
  - [Single Responsibility Principle (SRP)](#single-responsibility-principle-srp)
  - [Open/Closed Principle (OCP)](#openclosed-principle-ocp)
  - [Liskov Substitution Principle (LSP)](#liskov-substitution-principle-lsp)
  - [Interface Segregation Principle (ISP)](#interface-segregation-principle-isp)
  - [Dependency Inversion Principle (DIP)](#dependency-inversion-principle-dip)

---

## Single Responsibility Principle (SRP)

> Each object class must have one, and only one, reason to change.

**Problem:** this class has multiple responsibilities, such as API connection, task management, notification, and report.

```typescript
class TaskManager {
  constructor() {}
  // api connection
  connectAPI(): void {}
  // task
  createTask(): void {
    console.log('Create Task');
  }
  updateTask(): void {
    console.log('Update Task');
  }
  removeTask(): void {
    console.log('Remove Task');
  }
  // notification
  sendNotification(): void {
    console.log('Send Notification');
  }
  // report
  sendReport(): void {
    console.log('Send Report');
  }
}
```

**Solution:** After refactoring, each class has only one responsibility, respecting the SRP.

```typescript
class APIConnector {
  constructor() {}
  connectAPI(): void {}
}

class Report {
  constructor() {}
  sendReport(): void {
    console.log('Send Report');
  }
}

class Notificator {
  constructor() {}
  sendNotification(): void {
    console.log('Send Notification');
  }
}

class TaskManager {
  constructor() {}
  createTask(): void {
    console.log('Create Task');
  }
  updateTask(): void {
    console.log('Update Task');
  }
  removeTask(): void {
    console.log('Remove Task');
  }
}
```

## Open/Closed Principle (OCP)

> Software entities (such as classes and methods) must be open for extension but closed for modification.

**Problem:** in the code below we have a class that approves exams, but the method `approveRequestExam` has a lot of conditions that need to be checked. If we need to add a new type of exam, we will need to modify the class, which violates the OCP.

```typescript
type ExamType = {
  type: 'BLOOD' | 'XRay';
};

class ExamApprove {
  constructor() {}
  // approve exam
  approveRequestExam(exam: ExamType): void {
    // check exam type
    if (exam.type === 'BLOOD') {
      // check conditions
      if (this.verifyConditionsBlood(exam)) {
        console.log('Blood Exam Approved');
      }
      // check exam type
    } else if (exam.type === 'XRay') {
      // check conditions
      if (this.verifyConditionsXRay(exam)) {
        console.log('XRay Exam Approved!');
      }
    }
  }
  // blood conditions
  verifyConditionsBlood(exam: ExamType): boolean {
    return true;
  }
  // xray conditions
  verifyConditionsXRay(exam: ExamType): boolean {
    return false;
  }
}
```

**Solution:** create a class for each type of exam that implements the ExamApprove interface. This way, we can add new types of exams without modifying the ExamApprove class.

```typescript
type ExamType = {
  type: 'BLOOD' | 'XRay';
};

// approve exam
interface ExamApprove {
  approveRequestExam(exam: NewExamType): void;
  verifyConditionExam(exam: NewExamType): boolean;
}

// blood exam
class BloodExamApprove implements ExamApprove {
  // approve exam
  approveRequestExam(exam: ExamApprove): void {
    if (this.verifyConditionExam(exam)) {
      console.log('Blood Exam Approved');
    }
  }
  // verify conditions
  verifyConditionExam(exam: ExamApprove): boolean {
    return true;
  }
}

// xray exam
class RayXExamApprove implements ExamApprove {
  // approve exam
  approveRequestExam(exam: ExamApprove): void {
    if (this.verifyConditionExam(exam)) {
      console.log('RayX Exam Approved');
    }
  }
  // verify conditions
  verifyConditionExam(exam: NewExamType): boolean {
    return true;
  }
}
```

## Liskov Substitution Principle (LSP)

> Derived classes (or child classes) must be able to replace their base classes (or parent classes). Approach separeting respective responsabilities between entities.

**Problem:** Postgraduate students don't deliver an undergraduate thesis, but in the code below they inherit the method from the Student class. This violates the prinicple and restricts us from creating a PostgraduateStudent class that doesn't deliver an undergraduate thesis.

```typescript
class Student {
  constructor(public name: string) {}

  study(): void {
    console.log(`${this.name} is studying`);
  }

  deliverUndergradeThesis() {
    // Problem: Post graduate Students don't deliver an undergrade thesis
  }
}

class PostgraduateStudent extends Student {
  study(): void {
    console.log(`${this.name} is studying and searching`);
  }

  // Problem: we unintentionally inherit the deliverUndergradeThesis
  // method, which we shouldn't have access to
}
```

**Solution:** separate the responsibilities of the entities, have a base class with the common methods and the derived classes with the specific methods that override the base methods and expand the functionality.

```typescript
class Student {
  constructor(public name: string) {}
  // base
  study(): void {
    console.log(`${this.name} is studying`);
  }
}

class StudentGraduation extends Student {
  // override base
  study(): void {
    console.log(`${this.name} is studying`);
  }
  // extend base
  deliverTCC() {}
}

class StudentPosGraduation extends Student {
  // override base
  study(): void {
    console.log(`${this.name} is studying and searching`);
  }
}
```

## Interface Segregation Principle (ISP)

> A class should not be forced to implement interfaces and methods that will not be used.

**Probelem:** In a commision based shop, sellers and receptionists have a salary, but only sellers earn a commission. In the example below, the Seller and Receptionist classes implement a sindle Employee interface, but the Receptionists don't earn comission. So we are force to implement a method on the Receptionist class that will never be used.

```typescript
interface Employee {
  salary(): number;
  generateCommission(): void;
}

class Seller implements Employee {
  salary(): number {
    return 1000;
  }
  generateCommission(): void {
    console.log('Generating Commission');
  }
}

class Receptionist implements Employee {
  salary(): number {
    return 1000;
  }
  generateCommission(): void {
    // Problem: Receptionist don't have commission
  }
}
```

**Solution:** Segment the Employee methods from the Commissionable methods in two interfaces. Sellers will implement both interfaces, while Receptionists will only implement the Employee interface. This way the Receptionist class is not forced to implement the method that will never be used.

```typescript
interface Employee {
  salary(): number;
}

interface Commissionable {
  generateCommission(): void;
}

class Seller implements Employee, Commissionable {
  salary(): number {
    return 1000;
  }

  generateCommission(): void {
    console.log('Generating Commission');
  }
}

class Receptionist implements Employee {
  salary(): number {
    return 1000;
  }
}
```

## Dependency Inversion Principle (DIP)

> Depend on abstractions rather than concrete implementations. Dependencies should be abstracted and injected into the classes that use them.

**Problem:** when an OrderService class is directly coupled to the concrete implementation of OrderRepository class.

```typescript
interface Order {
  id: number;
  name: string;
}

class OrderRepository {
  constructor() {}
  saveOrder(order: Order) {}
}

class OrderService {
  private orderRepository: OrderRepository;

  constructor() {
    this.orderRepository = new OrderRepository();
  }

  processOrder(order: Order) {
    this.orderRepository.saveOrder(order);
  }
}
```

**Solution:** receive the repository as parameter on the constructor to instanciate and use. Now we depend of the abstraction and we don't need to know what repository (MySQL Postgres, MongoDB, etc.) we are using. The repository dependency is injected into the order class.

```typescript
interface Order {
  id: number;
  name: string;
}

class OrderRepository {
  constructor() {}
  saveOrder(order: Order) {}
}

class OrderService {
  private orderRepository: OrderRepository;

  constructor(repository: OrderRepository) {
    this.orderRepository = repository;
  }

  processOrder(order: Order) {
    this.orderRepository.saveOrder(order);
  }
}
```
