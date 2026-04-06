# Bus_Reservation_System
# 🚌 Bus Reservation System - Java Project

A complete console-based Bus Reservation System built with core **Java OOP concepts**.

---

## 📁 Project Structure

```
BusReservationSystem/
└── src/
    ├── Bus.java                  ← Step 1: Bus entity
    ├── Passenger.java            ← Step 2: Passenger entity
    ├── SeatManager.java          ← Step 3: 2D seat layout manager
    ├── BaseBooking.java          ← Abstract base class (Abstraction)
    ├── Booking.java              ← Step 4: Booking logic (extends BaseBooking)
    ├── Ticket.java               ← Step 5: Ticket generator
    ├── BusService.java           ← Step 6: Bus management
    ├── BookingService.java       ← Step 7: Booking management
    ├── FileHandler.java          ← Step 8: Save/Load data
    └── BusReservationSystem.java ← Step 9: Main menu program
```

---

## ⚙️ How to Compile & Run

Open terminal in the `src/` folder:

```bash
# Step 1 - Compile all files
javac *.java

# Step 2 - Run the program
java BusReservationSystem
```

> ✅ Requires **Java 8 or above** (uses `java.time` API)

---

## 🎯 Features

| # | Feature             | Where Implemented        |
|---|---------------------|--------------------------|
| 1 | Add Bus             | `BusService.addBus()`    |
| 2 | View Buses          | `BusService.viewAllBuses()` |
| 3 | Search Bus          | `BusService.searchBus()` |
| 4 | Check Availability  | `SeatManager.showSeats()` |
| 5 | Book Seat           | `BookingService.bookSeat()` |
| 6 | Cancel Booking      | `BookingService.cancelBooking()` |
| 7 | Passenger Details   | `Passenger.displayPassengerInfo()` |
| 8 | Ticket Generation   | `Ticket.printTicket()`   |
| 9 | Save Data           | `FileHandler.saveBuses()` / `saveBookings()` |

---

## 📚 OOP Concepts Used

### 1. 🔒 Encapsulation
Every class uses **private fields** with public getters/setters.
```java
// In Bus.java
private String busId;       // private — can't be accessed directly
public String getBusId() {  // accessed via getter
    return busId;
}
```

### 2. 🧬 Inheritance
`Booking` extends `BaseBooking` — it **inherits** common fields and overrides behavior.
```java
public class Booking extends BaseBooking {
    // Inherits: bookingId, passenger, bus, seatNumber
    // Adds: isActive field
}
```

### 3. 🎭 Polymorphism
`confirmBooking()` is declared abstract in `BaseBooking` and **overridden** in `Booking`.
```java
// BaseBooking.java (abstract)
public abstract boolean confirmBooking();

// Booking.java (concrete implementation)
@Override
public boolean confirmBooking() {
    // actual seat-booking logic here
}
```

### 4. 🧩 Abstraction
`BaseBooking` is an abstract class — you **can't create it directly**.
It hides implementation details and only exposes what's needed.

---

## 🗃️ Data Structures Used

| Structure        | Used In              | Purpose                         |
|------------------|----------------------|---------------------------------|
| `char[][]`       | `SeatManager`        | 2D grid of seat status (O/X)    |
| `ArrayList<Bus>` | `BusService`         | List of all buses               |
| `HashMap<String, Booking>` | `BookingService` | Fast lookup by booking ID |
| `HashMap<String, Passenger>` | `BookingService` | Fast lookup by passenger ID |

---

## 💾 File Handling

Data is saved using **Java Serialization** (Object → bytes → file):
- `buses.dat`    → All bus data
- `bookings.dat` → All booking, passenger, and ticket data

Data is automatically loaded when the program starts.

---

## 🧪 Exception Handling

| Exception              | Handled In           | Reason                            |
|------------------------|----------------------|-----------------------------------|
| `NumberFormatException`| `getIntInput()`      | User enters text instead of number|
| `IOException`          | `FileHandler`        | File read/write errors            |
| `ClassNotFoundException`| `FileHandler`       | Class mismatch during deserialization |

---

## 📌 Sample Menu Output

```
  ╔══════════════════════════════════════╗
  ║     BUS RESERVATION SYSTEM MENU     ║
  ╠══════════════════════════════════════╣
  ║  1. Add Bus                         ║
  ║  2. View All Buses                  ║
  ║  3. Search Bus (Source→Destination) ║
  ║  4. Check Seat Availability         ║
  ║  5. Book a Seat                     ║
  ║  6. Cancel Booking                  ║
  ║  7. View All Bookings               ║
  ║  8. Print Ticket                    ║
  ║  9. Save Data                       ║
  ║  0. Exit                            ║
  ╚══════════════════════════════════════╝
```

---

## 🎓 For Beginners

Each `.java` file is **heavily commented** to explain:
- What each class does
- What each method does
- Which OOP concept is being demonstrated

Start reading the files in this order:
1. `Bus.java` — understand encapsulation
2. `Passenger.java` — simple data class
3. `SeatManager.java` — see how 2D arrays work
4. `BaseBooking.java` → `Booking.java` — see abstraction + inheritance
5. `Ticket.java` — formatted output
6. `BusService.java` + `BookingService.java` — service layer
7. `FileHandler.java` — saving/loading
8. `BusReservationSystem.java` — the main menu tying it all together
