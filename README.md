# Campus Facility Management System

Campus Facility Management System is a simple C++ console application that provides a minimal booking system for campus facilities. It models three user roles (Student, Faculty, Admin), supports creating users, viewing and adding facilities, making and viewing bookings, and persists data to text files between runs.

## Stack
- Language(s): C++
- Standard: C++11 or later
- Build tool: g++ (or any C++11-compatible compiler)

## Features
- Role-based console menus for Student, Faculty, and Admin
- Facility management (add, view, mark available)
- Booking creation and viewing with basic cost calculation
- Simple persistence to text files: `users.txt`, `facilities.txt`, `bookings.txt`
- Default admin credentials: `admin` / `admin`

## Files of interest
- `campus-facility-managment-system` — main C++ source file (single-file console application). Implements classes: `user`, `student`, `faculty`, `admin`, `Facility`, `Booking` and the application flow.
- `users.txt`, `facilities.txt`, `bookings.txt` — data files used for persistence (created automatically in the working directory when the program saves data).

## How it works (high level)
The program is a single-process console application. On startup it reads saved records from `users.txt`, `facilities.txt`, and `bookings.txt` into in-memory vectors of objects. Users can register (students), admin can add facilities, and users can create bookings. When the program exits, or when the admin chooses "Save data", the application writes the current in-memory state back to the three text files using a pipe-separated (`|`) format.

Key C++ classes:
- `user` (abstract base): common properties (id, name, password, role, balance)
- `student`, `faculty`, `admin` — derived classes with specific menus and behaviour
- `Facility` — represents a bookable facility (id, name, rate, capacity, availability)
- `Booking` — stores booking details and status (Pending by default)

Persistence format (pipe-separated per line):
- users.txt: `id|name|password|role|balance`
- facilities.txt: `id|name|rate|capacity|available(1/0)`
- bookings.txt: `bookingid|userid|facilityid|username|facilityname|starthour|duration|cost|status`

## Build and run
Note: the repository's main source file is named `campus-facility-managment-system`. If your compiler/compiler driver expects a `.cpp` extension, you can rename it to `campus-facility-managment-system.cpp` before compiling.

Example compile and run commands:

```bash
# from repository root
# If the file has no extension
g++ -std=c++11 campus-facility-managment-system -o campus_facility
# or, after renaming to .cpp
# g++ -std=c++11 campus-facility-managment-system.cpp -o campus_facility

# Run the program
./campus_facility
```

When you run, the program loads saved data (if present). Use the menu options to login (admin: `admin` / `admin`), register students, add facilities, create bookings, save data, and exit. Data will be written to `users.txt`, `facilities.txt`, and `bookings.txt` in the working directory.

## Default data and credentials
- Admin user is created in code with ID `1`, username `admin`, password `admin`.
- Newly registered students start with a default balance of 100.0 (modifiable in code).

## Known limitations
- Single-file, single-threaded console app — no web UI or simultaneous users.
- Bookings approval/rejection is a placeholder (not fully implemented in the admin menu).
- Minimal validation on input (the program uses `cin >>` directly), so invalid input may cause unexpected behavior.
- No authentication beyond matching username/password strings in-memory.

## Suggested improvements
- Split source into .cpp/.h files and add a build system (Makefile or CMake)
- Improve input validation and error handling
- Implement booking approval/rejection flows and notifications
- Replace text-file persistence with a lightweight database (SQLite)
- Add unit tests and sample data files for quick start

## Contributing
This is a small educational project. Feel free to open issues or PRs with fixes or improvements.

## License
No license specified. Add a LICENSE file if you want to make this project open-source under a specific license.
