# Campus Facility Management — Quick Start

A minimal C++ console application for booking campus facilities (students, faculty, admin).

Build

```bash
# If the source file has no extension, rename to .cpp or compile directly:
# Rename (optional):
# mv campus-facility-managment-system campus-facility-managment-system.cpp

g++ -std=c++11 campus-facility-managment-system.cpp -o campus_facility
```

Run

```bash
./campus_facility
```

Default admin login

- Username: `admin`
- Password: `admin`

Data files (created in the program working directory):

- `users.txt` — id|name|password|role|balance
- `facilities.txt` — id|name|rate|capacity|available(1/0)
- `bookings.txt` — bookingid|userid|facilityid|username|facilityname|starthour|duration|cost|status

Notes

- This is a single-file, single-user console app. Input validation is minimal.
- Use the admin menu to add facilities and save data.
