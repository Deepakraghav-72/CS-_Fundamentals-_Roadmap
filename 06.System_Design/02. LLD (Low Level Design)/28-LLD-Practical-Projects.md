# Topic 28: LLD Practical Projects

# 1. Introduction to LLD Practical Projects

## LLD Projects kya hote hain?

LLD Projects aise projects hote hain jinmein hum kisi real-world problem ka software-level design banate hain.

Ismein hum decide karte hain:

- Kaun-kaun si classes banengi?
- Classes ki responsibilities kya hongi?
- Objects ek doosre ke saath kaise interact karenge?
- Kaun se methods aur attributes honge?
- Kaun se design patterns useful honge?
- System ko test kaise karenge?

### Example

Maan lo humein ATM Machine design karni hai.

ATM mein:

- User card insert karega.
- PIN enter karega.
- Balance check karega.
- Cash withdraw karega.
- Receipt generate hogi.

Ab in sab functionalities ko implement karne ke liye classes aur objects design karna LLD hai.

## 2. LLD Project solve karne ka standard approach

Har LLD interview problem mein ye steps follow karo:

1. Problem Statement samjho.
2. Functional Requirements identify karo.
3. Non-Functional Requirements identify karo.
4. Main Entities identify karo.
5. Classes aur Objects identify karo.
6. Attributes aur Methods define karo.
7. Class Relationships define karo.
8. Suitable Design Patterns select karo.
9. UML Class Diagram banao.
10. Main Workflow / Sequence Diagram banao.
11. Code implement karo.
12. Edge Cases aur Test Cases likho.

**Important:** Interview mein coding start karne se pehle requirements aur assumptions clarify karna bahut zaroori hai.

---

# PROJECT 1: PARKING LOT MANAGEMENT SYSTEM

## 3. Problem Statement

Humein ek Parking Lot Management System design karna hai.

Is system mein vehicles parking lot mein enter karenge, available parking spot find karenge, vehicle park hoga aur exit ke time parking fee pay karega.

### Real-life example

Maan lo ek shopping mall mein parking hai.

Usmein:

- Multiple floors hain.
- Har floor par multiple parking spots hain.
- Cars aur bikes dono park ho sakti hain.
- Har vehicle ko ek suitable spot milna chahiye.
- Exit ke time parking fee calculate honi chahiye.

## 4. Functional Requirements

System mein ye functionalities honi chahiye:

1. Vehicle parking lot mein enter kar sake.
2. Available parking spot find ho.
3. Vehicle ko spot assign ho.
4. Parking ticket generate ho.
5. Vehicle exit kar sake.
6. Parking fee calculate ho.
7. Payment process ho.
8. Spot free ho jaye.
9. Available spots ki information mil sake.

## 5. Non-Functional Requirements

- System reliable hona chahiye.
- Ek spot par ek hi vehicle park ho.
- Multiple entry requests handle ho sakein.
- Parking status accurate rehna chahiye.
- Code maintainable hona chahiye.

## 6. Main Entities

Parking System ki main entities:

- ParkingLot
- ParkingFloor
- ParkingSpot
- Vehicle
- ParkingTicket
- Payment
- ParkingManager

## 7. Classes and Responsibilities

| Class          | Responsibility                         |
| -------------- | -------------------------------------- |
| ParkingLot     | Complete parking facility manage karna |
| ParkingFloor   | Parking floor manage karna             |
| ParkingSpot    | Individual parking spot manage karna   |
| Vehicle        | Vehicle information store karna        |
| ParkingTicket  | Entry aur exit information rakhna      |
| Payment        | Payment information handle karna       |
| ParkingManager | Parking workflow coordinate karna      |

## 8. Important Attributes and Methods

### ParkingLot

Attributes:

- name
- floors

Methods:

- addFloor()
- findAvailableSpot()
- parkVehicle()
- releaseSpot()

### ParkingFloor

Attributes:

- floorNumber
- parkingSpots

Methods:

- addSpot()
- getAvailableSpots()

### ParkingSpot

Attributes:

- spotId
- spotType
- isAvailable
- parkedVehicle

Methods:

- assignVehicle()
- removeVehicle()
- isFree()

### Vehicle

Attributes:

- vehicleNumber
- vehicleType

Methods:

- getVehicleNumber()
- getVehicleType()

### ParkingTicket

Attributes:

- ticketId
- vehicle
- entryTime
- exitTime

Methods:

- generateTicket()
- calculateDuration()

### Payment

Attributes:

- paymentId
- amount
- paymentStatus

Methods:

- processPayment()
- refundPayment()

## 9. Class Relationship

```text
ParkingLot
    |
    | contains
    v
ParkingFloor
    |
    | contains
    v
ParkingSpot
    |
    | assigned to
    v
Vehicle

ParkingManager
    |
    | manages
    v
ParkingTicket
    |
    | payment
    v
Payment
```

Ye conceptual diagram hai. Actual design mein ParkingLot ke paas multiple floors aur har floor ke paas multiple spots honge.

## 10. Parking Lot – Basic JavaScript Implementation

```javascript
class Vehicle {
  constructor(number, type) {
    this.number = number;
    this.type = type;
  }
}

class ParkingSpot {
  constructor(id, type) {
    this.id = id;
    this.type = type;
    this.vehicle = null;
  }

  isFree() {
    return this.vehicle === null;
  }

  assignVehicle(vehicle) {
    if (!this.isFree()) {
      return false;
    }

    if (this.type !== vehicle.type) {
      return false;
    }

    this.vehicle = vehicle;
    return true;
  }

  removeVehicle() {
    const vehicle = this.vehicle;
    this.vehicle = null;
    return vehicle;
  }
}

class ParkingLot {
  constructor(spots) {
    this.spots = spots;
  }

  parkVehicle(vehicle) {
    const spot = this.spots.find(
      (spot) => spot.isFree() && spot.type === vehicle.type,
    );

    if (!spot) {
      return "No suitable parking spot available";
    }

    spot.assignVehicle(vehicle);

    return `Vehicle parked at spot ${spot.id}`;
  }
}

const spots = [new ParkingSpot(1, "CAR"), new ParkingSpot(2, "BIKE")];

const parkingLot = new ParkingLot(spots);

const car = new Vehicle("UP13AB1234", "CAR");

console.log(parkingLot.parkVehicle(car));
```

Output:

```text
Vehicle parked at spot 1
```

### Code Explanation

1. Vehicle class vehicle ki information rakhti hai.
2. ParkingSpot class spot ka status manage karti hai.
3. `isFree()` check karta hai ki spot available hai ya nahi.
4. `assignVehicle()` vehicle ko spot assign karta hai.
5. ParkingLot class available suitable spot search karti hai.
6. Vehicle park hone par confirmation return hota hai.

**Note:** Ye basic educational implementation hai. Complete production system mein tickets, payments, floors, concurrency, locking aur error handling bhi implement karne honge.

## 11. Suitable Design Patterns

| Pattern  | Use                                          |
| -------- | -------------------------------------------- |
| Strategy | Different parking fee calculation strategies |
| Factory  | Different vehicle types create karna         |
| State    | Parking spot ke states manage karna          |

## 12. Important Edge Cases

- Parking lot full ho.
- Vehicle type ke according spot available na ho.
- Same vehicle dobara enter karne ki request kare.
- Occupied spot par doosra vehicle assign ho.
- Invalid ticket se exit request aaye.
- Payment fail ho.
- Do vehicles ek hi spot ko simultaneously reserve karne ki koshish karein.

---

# PROJECT 2: LIBRARY MANAGEMENT SYSTEM

## 13. Problem Statement

Humein ek Library Management System design karna hai.

Library mein books available hongi. Members books search, borrow aur return kar sakenge.

System books aur members ka record maintain karega.

## 14. Functional Requirements

1. New books add karna.
2. Books search karna.
3. Members register karna.
4. Book issue karna.
5. Book return karna.
6. Book availability check karna.
7. Due date manage karna.
8. Late return par fine calculate karna.

## 15. Non-Functional Requirements

- Book records accurate hone chahiye.
- Multiple members handle hone chahiye.
- Duplicate book issue nahi honi chahiye.
- System reliable aur maintainable hona chahiye.

## 16. Main Entities

- Library
- Book
- BookCopy
- Member
- Librarian
- Loan
- Fine

**Important:** Book aur BookCopy ko alag samajhna useful hai.

Example:

Ek book ka title "JavaScript Basics" hai. Library mein uski 5 physical copies hain.

`Book` title aur author ki information rakhegi, jabki `BookCopy` har individual copy ka record rakhegi.

## 17. Classes and Responsibilities

| Class     | Responsibility                  |
| --------- | ------------------------------- |
| Library   | Library operations manage karna |
| Book      | Book title aur author details   |
| BookCopy  | Individual copy ka status       |
| Member    | Library member details          |
| Librarian | Library administration          |
| Loan      | Issue aur return record         |
| Fine      | Late return fine calculation    |

## 18. Attributes and Methods

### Book

Attributes:

- bookId
- title
- author
- ISBN

Methods:

- getDetails()

### BookCopy

Attributes:

- copyId
- book
- status

Methods:

- markAvailable()
- markIssued()

### Member

Attributes:

- memberId
- name
- email

Methods:

- borrowBook()
- returnBook()

### Loan

Attributes:

- loanId
- member
- bookCopy
- issueDate
- dueDate
- returnDate

Methods:

- createLoan()
- closeLoan()
- calculateLateDays()

### Fine

Attributes:

- fineId
- amount
- status

Methods:

- calculateFine()
- payFine()

## 19. Class Relationship

```text
Library
   |
   | contains
   v
Book
   |
   | has multiple copies
   v
BookCopy
   |
   | issued through
   v
Loan
   |
   | belongs to
   v
Member

Loan
   |
   | may generate
   v
Fine
```

## 20. Basic JavaScript Implementation

```javascript
class Book {
  constructor(id, title) {
    this.id = id;
    this.title = title;
  }
}

class BookCopy {
  constructor(id, book) {
    this.id = id;
    this.book = book;
    this.available = true;
  }
}

class Member {
  constructor(id, name) {
    this.id = id;
    this.name = name;
  }
}

class Library {
  constructor() {
    this.copies = [];
    this.loans = [];
  }

  addCopy(copy) {
    this.copies.push(copy);
  }

  issueBook(member, bookId) {
    const copy = this.copies.find(
      (item) => item.book.id === bookId && item.available,
    );

    if (!copy) {
      return "Book not available";
    }

    copy.available = false;

    const loan = {
      member,
      copy,
      issueDate: new Date(),
    };

    this.loans.push(loan);

    return "Book issued successfully";
  }
}

const book = new Book(1, "JavaScript Basics");

const copy = new BookCopy(101, book);

const member = new Member(1, "Rahul");

const library = new Library();

library.addCopy(copy);

console.log(library.issueBook(member, 1));
```

Output:

```text
Book issued successfully
```

### Code Explanation

1. Book class book ki details store karti hai.
2. BookCopy individual copy ka status rakhti hai.
3. Member class member ki information rakhti hai.
4. Library class copies aur loans manage karti hai.
5. `issueBook()` available copy find karta hai.
6. Copy available hone par uska status unavailable ho jata hai aur loan record create hota hai.

## 21. Suitable Design Patterns

| Pattern  | Use                                                     |
| -------- | ------------------------------------------------------- |
| Factory  | Book copies ya notifications create karna               |
| Strategy | Different fine calculation rules                        |
| Observer | Book available hone par waiting members ko notify karna |

## 22. Important Edge Cases

- Book available na ho.
- Member already maximum borrowing limit reach kar chuka ho.
- Same copy dobara issue karne ki request aaye.
- Book return date expire ho gayi ho.
- Invalid member ID ho.
- Same book ki multiple copies hon.

---

# PROJECT 3: ATM SYSTEM

## 23. Problem Statement

Humein ATM Machine ka LLD design karna hai.

ATM ke through bank customers:

- Account access karenge.
- Balance check karenge.
- Cash withdraw karenge.
- Cash deposit karenge.
- Receipt receive karenge.

## 24. Functional Requirements

1. ATM card insert karna.
2. PIN verify karna.
3. Account authenticate karna.
4. Balance check karna.
5. Cash withdraw karna.
6. Cash deposit karna.
7. Receipt generate karna.
8. Card eject karna.

## 25. Non-Functional Requirements

- Security high honi chahiye.
- Transactions accurate honi chahiye.
- Unauthorized access prevent hona chahiye.
- ATM cash availability maintain honi chahiye.
- Transactions reliable honi chahiye.

## 26. Main Entities

- ATM
- Card
- Customer
- BankAccount
- BankService
- CashDispenser
- Transaction
- Receipt

## 27. Classes and Responsibilities

| Class         | Responsibility                          |
| ------------- | --------------------------------------- |
| ATM           | ATM workflow manage karna               |
| Card          | Card information represent karna        |
| Customer      | Customer details                        |
| BankAccount   | Account balance aur account information |
| BankService   | Bank operations coordinate karna        |
| CashDispenser | Cash dispense karna                     |
| Transaction   | Transaction details maintain karna      |
| Receipt       | Transaction receipt generate karna      |

## 28. Important Attributes and Methods

### ATM

Attributes:

- atmId
- location
- state

Methods:

- insertCard()
- authenticate()
- ejectCard()
- startTransaction()

### Card

Attributes:

- cardNumber
- expiryDate
- accountId

Methods:

- validate()

### BankAccount

Attributes:

- accountNumber
- balance

Methods:

- getBalance()
- debit()
- credit()

### CashDispenser

Attributes:

- availableCash

Methods:

- hasSufficientCash()
- dispenseCash()

### Transaction

Attributes:

- transactionId
- amount
- transactionType
- status

Methods:

- execute()
- getStatus()

## 29. Class Relationship

```text
Customer
   |
   | owns
   v
BankAccount
   |
   | accessed through
   v
Card

ATM
   |
   | uses
   v
BankService
   |
   | coordinates
   v
Transaction
   |
   | may use
   v
CashDispenser
```

## 30. ATM Withdrawal Workflow

```text
Start
  |
Insert Card
  |
Enter PIN
  |
Validate PIN
  |
PIN Correct?
 /       \
No        Yes
|          |
Reject     Select Withdrawal
|          |
Eject      Enter Amount
Card       |
           v
      Check Balance
           |
      Check ATM Cash
           |
       Both Valid?
        /     \
       No      Yes
       |        |
     Reject   Process
              Transaction
                 |
              Dispense Cash
                 |
              Generate Receipt
                 |
              Eject Card
                 |
                End
```

## 31. Basic JavaScript Implementation

```javascript
class BankAccount {
  constructor(balance) {
    this.balance = balance;
  }

  withdraw(amount) {
    if (amount <= 0) {
      return "Invalid amount";
    }

    if (amount > this.balance) {
      return "Insufficient balance";
    }

    this.balance -= amount;

    return "Withdrawal successful";
  }

  getBalance() {
    return this.balance;
  }
}

class ATM {
  constructor(account) {
    this.account = account;
  }

  withdrawCash(amount) {
    return this.account.withdraw(amount);
  }
}

const account = new BankAccount(10000);

const atm = new ATM(account);

console.log(atm.withdrawCash(2000));

console.log(account.getBalance());
```

Output:

```text
Withdrawal successful
8000
```

### Code Explanation

1. BankAccount class balance manage karti hai.
2. `withdraw()` amount validate karta hai.
3. Balance sufficient hone par amount deduct hota hai.
4. ATM class account ki withdrawal functionality use karti hai.
5. Client ATM ke through withdrawal request karta hai.

**Important:** Ye sirf simplified learning example hai. Real ATM mein PIN authentication, bank authorization, encrypted communication, transaction rollback, cash dispenser synchronization aur audit logging zaroori hain. PIN ko plain text mein store nahi karna chahiye.

## 32. Suitable Design Patterns

| Pattern  | Use                                  |
| -------- | ------------------------------------ |
| State    | ATM ke different states manage karna |
| Strategy | Different transaction methods        |
| Factory  | Transaction objects create karna     |

## 33. Important Edge Cases

- Incorrect PIN.
- Multiple incorrect PIN attempts.
- Expired card.
- Insufficient account balance.
- ATM mein cash insufficient ho.
- Invalid withdrawal amount.
- Network failure.
- Cash dispense hone mein failure.
- Transaction ke beech power failure.

---

# PROJECT 4: TIC-TAC-TOE GAME

## 34. Problem Statement

Humein Tic-Tac-Toe game design karna hai.

Ye ek two-player game hai jisme 3×3 board hota hai.

Players:

- Player X
- Player O

Players alternate turns mein board par apna symbol place karte hain.

Jo player pehle horizontal, vertical ya diagonal direction mein 3 same symbols bana deta hai, woh winner hota hai.

## 35. Functional Requirements

1. Game board create karna.
2. Two players register/select karna.
3. Player turn manage karna.
4. Valid move allow karna.
5. Invalid move reject karna.
6. Winner identify karna.
7. Draw condition check karna.
8. New game start karna.

## 36. Non-Functional Requirements

- Game rules correctly follow hone chahiye.
- Invalid moves prevent hone chahiye.
- Game state accurate rehni chahiye.
- Code easily extendable hona chahiye.

## 37. Main Entities

- Game
- Board
- Player
- Move
- GameStatus

## 38. Classes and Responsibilities

| Class      | Responsibility                         |
| ---------- | -------------------------------------- |
| Game       | Complete game manage karna             |
| Board      | 3×3 board maintain karna               |
| Player     | Player information                     |
| Move       | Player ka selected position            |
| GameStatus | Game ka current status represent karna |

## 39. Important Attributes and Methods

### Player

Attributes:

- name
- symbol

Methods:

- getName()
- getSymbol()

### Board

Attributes:

- cells

Methods:

- display()
- makeMove()
- isCellEmpty()
- checkWinner()
- isFull()

### Game

Attributes:

- players
- board
- currentPlayer
- status

Methods:

- startGame()
- playTurn()
- switchPlayer()
- checkGameStatus()
- restartGame()

## 40. Class Relationship

```text
       Game
        |
   -----------
   |         |
  Board    Players
              |
        -------------
        |           |
      Player X   Player O
```

## 41. Basic JavaScript Implementation

```javascript
class Player {
  constructor(name, symbol) {
    this.name = name;
    this.symbol = symbol;
  }
}

class Board {
  constructor() {
    this.cells = Array(9).fill(null);
  }

  makeMove(position, symbol) {
    if (position < 0 || position >= 9) {
      return false;
    }

    if (this.cells[position] !== null) {
      return false;
    }

    this.cells[position] = symbol;

    return true;
  }

  checkWinner() {
    const winningCombinations = [
      [0, 1, 2],
      [3, 4, 5],
      [6, 7, 8],
      [0, 3, 6],
      [1, 4, 7],
      [2, 5, 8],
      [0, 4, 8],
      [2, 4, 6],
    ];

    for (const combination of winningCombinations) {
      const [a, b, c] = combination;

      if (
        this.cells[a] &&
        this.cells[a] === this.cells[b] &&
        this.cells[b] === this.cells[c]
      ) {
        return this.cells[a];
      }
    }

    return null;
  }

  isFull() {
    return this.cells.every((cell) => cell !== null);
  }
}

const board = new Board();

board.makeMove(0, "X");
board.makeMove(1, "O");
board.makeMove(3, "X");
board.makeMove(4, "O");
board.makeMove(6, "X");

console.log(board.checkWinner());
```

Output:

```text
X
```

### Code Explanation

1. Player class player ki details store karti hai.
2. Board class 9 cells ka array maintain karti hai.
3. `makeMove()` valid position par symbol place karta hai.
4. `checkWinner()` 8 winning combinations check karta hai.
5. Agar kisi combination mein same non-null symbol ho, toh winner return hota hai.

## 42. Suitable Design Patterns

| Pattern  | Use                                        |
| -------- | ------------------------------------------ |
| State    | Game ke states manage karna                |
| Strategy | Different game rules ya winning strategies |
| Observer | UI ko game state changes notify karna      |

## 43. Important Edge Cases

- Already occupied cell par move.
- Invalid position.
- Game end hone ke baad move.
- Draw condition.
- Same player ke consecutive turns.
- Restart ke baad old board clear hona.

---

# PROJECT 5: ELEVATOR SYSTEM

## 44. Problem Statement

Humein ek Elevator System design karna hai.

Building mein multiple floors aur elevators hain.

Users:

- Kisi floor se elevator call kar sakte hain.
- Destination floor select kar sakte hain.
- Elevator users ko desired floor tak le jaata hai.

System ko decide karna hoga ki kaunsa elevator request handle karega.

## 45. Functional Requirements

1. Multiple floors support karna.
2. Multiple elevators support karna.
3. Elevator call request receive karna.
4. Destination floor select karna.
5. Elevator direction manage karna.
6. Suitable elevator assign karna.
7. Elevator doors open aur close karna.
8. Elevator movement manage karna.
9. Emergency stop support karna.

## 46. Non-Functional Requirements

- Passenger safety important honi chahiye.
- Elevator requests efficiently handle honi chahiye.
- System reliable hona chahiye.
- Multiple requests manage karni chahiye.
- Emergency handling available honi chahiye.

## 47. Main Entities

- ElevatorSystem
- Elevator
- Floor
- ElevatorController
- ElevatorRequest
- Door
- ElevatorScheduler

## 48. Classes and Responsibilities

| Class              | Responsibility                        |
| ------------------ | ------------------------------------- |
| ElevatorSystem     | Complete elevator system manage karna |
| Elevator           | Individual elevator manage karna      |
| Floor              | Floor information                     |
| ElevatorController | Elevator movement control karna       |
| ElevatorRequest    | User request maintain karna           |
| Door               | Door open/close manage karna          |
| ElevatorScheduler  | Elevator assignment decide karna      |

## 49. Important Attributes and Methods

### Elevator

Attributes:

- elevatorId
- currentFloor
- direction
- status
- requests

Methods:

- moveUp()
- moveDown()
- stop()
- openDoor()
- closeDoor()

### Floor

Attributes:

- floorNumber

Methods:

- requestElevator()

### ElevatorRequest

Attributes:

- sourceFloor
- destinationFloor
- direction

Methods:

- createRequest()

### ElevatorScheduler

Methods:

- findBestElevator()
- assignRequest()

## 50. Elevator States

Elevator ki possible states:

- IDLE
- MOVING_UP
- MOVING_DOWN
- DOOR_OPEN
- MAINTENANCE
- EMERGENCY

Simplified State Diagram:

```text
        IDLE
         |
    New Request
         |
    -------------
    |           |
Moving Up   Moving Down
    |           |
    -------------
         |
       Stop
         |
      Door Open
         |
      Door Close
         |
        IDLE
```

## 51. Basic JavaScript Implementation

```javascript
class Elevator {
  constructor(id, currentFloor = 0) {
    this.id = id;
    this.currentFloor = currentFloor;
    this.status = "IDLE";
  }

  moveTo(destinationFloor) {
    if (destinationFloor === this.currentFloor) {
      return "Already on this floor";
    }

    if (destinationFloor > this.currentFloor) {
      this.status = "MOVING_UP";
    } else {
      this.status = "MOVING_DOWN";
    }

    this.currentFloor = destinationFloor;

    this.status = "DOOR_OPEN";

    return `Elevator ${this.id} reached floor ${destinationFloor}`;
  }
}

class ElevatorScheduler {
  constructor(elevators) {
    this.elevators = elevators;
  }

  findBestElevator(requestedFloor) {
    return this.elevators.reduce((best, current) => {
      const bestDistance = Math.abs(best.currentFloor - requestedFloor);

      const currentDistance = Math.abs(current.currentFloor - requestedFloor);

      return currentDistance < bestDistance ? current : best;
    });
  }
}

const elevators = [new Elevator(1, 0), new Elevator(2, 5)];

const scheduler = new ElevatorScheduler(elevators);

const selectedElevator = scheduler.findBestElevator(4);

console.log(selectedElevator.moveTo(4));
```

Output:

```text
Elevator 2 reached floor 4
```

### Code Explanation

1. Elevator class individual elevator represent karti hai.
2. `moveTo()` destination floor par movement simulate karta hai.
3. ElevatorScheduler multiple elevators maintain karta hai.
4. `findBestElevator()` requested floor se nearest elevator select karta hai.
5. Selected elevator request handle karta hai.

**Note:** Ye sirf basic demonstration hai. Real elevator scheduling mein direction, existing stops, passenger load, safety interlocks, door sensors, emergency handling aur concurrent requests consider karne padte hain. Nearest elevator hamesha best choice nahi hota.

## 52. Suitable Design Patterns

| Pattern  | Use                                                               |
| -------- | ----------------------------------------------------------------- |
| State    | Elevator ke different states                                      |
| Strategy | Different elevator scheduling algorithms                          |
| Observer | Floor aur elevator status updates                                 |
| Command  | Elevator requests ko command objects ke roop mein represent karna |

## 53. Important Edge Cases

- Elevator already busy ho.
- Multiple floors se requests aayein.
- Elevator maintenance mode mein ho.
- Emergency stop activate ho.
- Invalid floor request aaye.
- Elevator door properly close na ho.
- Multiple passengers different floors select karein.

---

# PART 6: FIVE PROJECTS COMPARISON

## 54. All Projects at a Glance

| Project     | Main Classes                        | Important Patterns          |
| ----------- | ----------------------------------- | --------------------------- |
| Parking Lot | Vehicle, Spot, Floor, Ticket        | Strategy, Factory, State    |
| Library     | Book, Member, Loan, Fine            | Strategy, Observer, Factory |
| ATM         | ATM, Account, Card, Transaction     | State, Strategy, Factory    |
| Tic-Tac-Toe | Game, Board, Player, Move           | State, Strategy, Observer   |
| Elevator    | Elevator, Floor, Request, Scheduler | State, Strategy, Observer   |

## 55. Projects mein common concepts

In sab projects mein kuch common LLD concepts use hote hain:

### OOP

- Classes
- Objects
- Encapsulation
- Abstraction
- Inheritance
- Polymorphism
- Composition

### SOLID

- Single Responsibility
- Open/Closed
- Liskov Substitution
- Interface Segregation
- Dependency Inversion

### Design Patterns

- Factory
- Singleton
- Strategy
- Observer
- State
- Command
- Decorator

### UML

- Class Diagram
- Sequence Diagram
- Activity Diagram

---

# PART 7: LLD INTERVIEW APPROACH

## 56. LLD Interview mein project kaise solve karein?

Maan lo interviewer tumse Parking Lot System design karne ko kehta hai.

Tumhe ye approach follow karni chahiye:

### Step 1: Requirements Clarify Karo

Questions:

- Kitne floors honge?
- Kaun se vehicle types support honge?
- Different vehicle ke liye different spots honge?
- Payment kaise calculate hogi?
- Multiple entry gates honge?

### Step 2: Requirements List Karo

Functional aur Non-Functional requirements separately likho.

### Step 3: Main Entities Identify Karo

ParkingLot, Floor, Spot, Vehicle, Ticket aur Payment.

### Step 4: Classes Design Karo

Har class ki responsibility, attributes aur methods define karo.

### Step 5: Relationships Define Karo

Association, Composition, Inheritance aur Dependency identify karo.

### Step 6: Design Patterns Choose Karo

Sirf wahi patterns use karo jo actual problem solve karte hain.

### Step 7: UML Diagram Banao

Class diagram aur important workflow ka sequence diagram banao.

### Step 8: Code Implement Karo

Clean, readable aur testable code likho.

### Step 9: Edge Cases Discuss Karo

Invalid input, duplicate requests, concurrency aur failures consider karo.

### Step 10: Testing Discuss Karo

Unit, Integration aur important workflow tests define karo.

---

# PART 8: PRACTICAL ASSIGNMENTS

## 57. Beginner Level

In projects ko khud implement karne ki practice karo:

1. Tic-Tac-Toe Game.
2. Basic Library Management.
3. Simple Parking Lot.

Focus:

- Classes
- Objects
- Methods
- Encapsulation
- Relationships

## 58. Intermediate Level

1. ATM System.
2. Elevator System.
3. Advanced Parking Lot.

Focus:

- SOLID Principles
- Design Patterns
- UML Diagrams
- Error Handling
- Unit Testing

## 59. Advanced Improvements

Apne projects mein ye improvements add karo:

- Multiple users.
- Multiple concurrent requests.
- Database integration.
- Logging.
- Input validation.
- Automated tests.
- Proper error handling.
- Extensible architecture.

**Important:** Pehle basic working design banao. Uske baad requirements ke according complexity add karo.

---

# PART 9: INTERVIEW QUESTIONS

## 60. Important LLD Project Questions

### Q1. How do you start an LLD problem?

Sabse pehle problem statement samajhta hoon, requirements clarify karta hoon, entities identify karta hoon aur phir classes aur relationships design karta hoon.

### Q2. Why do we identify entities?

Entities identify karne se system ke important objects aur responsibilities samajhne mein help milti hai.

### Q3. Why is SOLID important in LLD?

SOLID principles maintainable, flexible aur testable code design karne mein help karte hain.

### Q4. Which design patterns are commonly used in LLD?

Factory, Singleton, Strategy, Observer, State, Adapter, Decorator aur Facade commonly studied patterns hain.

### Q5. What is the difference between a class and an entity?

Entity ek important domain concept ya object ko represent karti hai. Class programming mein us object ka structure aur behavior define karne ka blueprint hoti hai. Har entity ka separate class hona compulsory nahi hai.

### Q6. Why are UML diagrams useful?

UML diagrams system ka structure aur object interactions visually communicate karne mein help karte hain.

### Q7. What is the importance of edge cases?

Edge cases unusual aur boundary conditions mein system ki correctness verify karne mein help karte hain.

### Q8. Should we use every design pattern in an LLD project?

No. Sirf wahi design patterns use karne chahiye jo actual design problem solve karte hain.

### Q9. How do you make LLD code testable?

Classes ki responsibilities clear rakho, dependencies ko inject karo, unnecessary tight coupling avoid karo aur methods ko independently testable banao.

### Q10. What is the difference between LLD and HLD?

LLD detailed class-level design, methods aur object interactions par focus karta hai. HLD overall system architecture, services, databases aur components ke high-level structure par focus karta hai.

---

# PART 10: QUICK REVISION

## 61. Five Projects – Quick Summary

### 1. Parking Lot

- Vehicle parking.
- Spot allocation.
- Ticket generation.
- Payment.
- Spot release.

### 2. Library Management

- Book management.
- Member registration.
- Book issue.
- Book return.
- Fine calculation.

### 3. ATM System

- Card authentication.
- PIN verification.
- Balance check.
- Cash withdrawal.
- Cash deposit.

### 4. Tic-Tac-Toe

- Board management.
- Player turns.
- Valid moves.
- Winner detection.
- Draw detection.

### 5. Elevator System

- Elevator requests.
- Floor management.
- Direction management.
- Elevator scheduling.
- Emergency handling.

## 62. LLD Project Solve Karne ka Formula

```text
Problem
   |
   v
Requirements
   |
   v
Entities
   |
   v
Classes & Objects
   |
   v
Attributes & Methods
   |
   v
Relationships
   |
   v
SOLID Principles
   |
   v
Design Patterns
   |
   v
UML Diagrams
   |
   v
Implementation
   |
   v
Testing
   |
   v
Refactoring
```

---

# 63. Final Subject 02 Completion Checklist

- [ ] Parking Lot Management System samajh liya.
- [ ] Library Management System samajh liya.
- [ ] ATM System samajh liya.
- [ ] Tic-Tac-Toe Game samajh liya.
- [ ] Elevator System samajh liya.
- [ ] Har project ki requirements samajh li.
- [ ] Main entities aur classes identify karna seekh liya.
- [ ] Attributes aur methods define karna seekh liya.
- [ ] Class relationships samajh liye.
- [ ] Suitable design patterns identify karna seekh liya.
- [ ] UML diagrams revise kar liye.
- [ ] Edge cases identify karna seekh liya.
- [ ] LLD interview approach samajh liya.

---

# 64. Subject 02 – LLD Completion

**Congratulations! Subject 02 – Low Level Design ke total 28 topics complete ho gaye.**

Is subject mein humne cover kiya:

1. Introduction to LLD
2. OOP Concepts
3. Classes & Objects
4. Encapsulation
5. Abstraction
6. Inheritance
7. Polymorphism
8. Association, Aggregation & Composition
9. Interfaces & Abstract Classes
10. SOLID Principles
11. Single Responsibility Principle
12. Open/Closed Principle
13. Liskov Substitution Principle
14. Interface Segregation Principle
15. Dependency Inversion Principle
16. UML Class Diagrams
17. UML Sequence Diagrams
18. Use Case & Activity Diagrams
19. Introduction to Design Patterns
20. Singleton Pattern
21. Factory Pattern
22. Builder Pattern
23. Strategy Pattern
24. Observer Pattern
25. Adapter Pattern
26. Decorator & Facade Patterns
27. LLD Design Approach, Testing & Best Practices
28. LLD Practical Projects

**Subject 02 Complete!**
