Smart Parking Management System

  A comprehensive parking management system implemented in C using AVL Trees for efficient data storage and retrieval. This system manages parking spaces, user registrations, membership policies, and provides various sorting and analytical features.
  
Language : C

•Table of Contents
- [Features](#features)
- [Data Structures](#data-structures)
- [Algorithms](#algorithms)
- [Operations](#operations)
- [Installation & Usage](#installation--usage)
- [File Structure](#file-structure)
- [System Architecture](#system-architecture)
- [Future Enhancements](#future-enhancements)

•Features

Core Functionality
- **Real-time Parking Management**: Track 50 parking spaces with live status updates
- **User Registration & Authentication**: Secure user management with vehicle number-based identification
- **Smart Allocation Policy**: Membership-based parking space allocation with priority systems
- **Dynamic Membership System**: Automatic upgrades based on parking duration (Premium at 100+ hours, Golden at 200+ hours)
- **Flexible Payment System**: Tiered pricing with membership discounts
- **Persistent Data Storage**: File-based data persistence across sessions

Advanced Features
- **Multi-criteria Sorting**: Sort users by amount paid, number of parkings, and parking spaces by occupancy/revenue
- **Time-based Analytics**: Calculate parking duration with precision
- **Revenue Management**: Track individual parking space revenue and overall system performance
- **Authentication System**: Name-based user verification for secure transactions

User Interface
- **Interactive Menu System**: Easy-to-navigate console interface
- **Comprehensive Reporting**: Detailed parking records and analytics
- **Real-time Feedback**: Live updates on parking status and payments

•Data Structures

Primary Data Structures

1. **AVL Tree for Parking Status**
```c
typedef struct ParkingStatus_Tag {
    int parkingID;        // Unique parking space identifier (1-50)
    int status;           // 0 = empty, 1 = occupied
    int occ;              // Total occupancy count
    int revenue;          // Total revenue generated
    int height;           // AVL tree height
    struct ParkingStatus_Tag *left, *right;
} Status;
```

2. **AVL Tree for User Details**
```c
typedef struct details_tag {
    char vn[20];              // Vehicle number (unique identifier)
    char name[50];            // User name
    int memb;                 // Membership: 0=general, 1=premium, 2=golden
    float tpHours;            // Total parking hours
    int psID;                 // Current parking space ID
    struct tm arrival;        // Arrival timestamp
    struct tm departure;      // Departure timestamp
    float totalAmountPaid;    // Cumulative amount paid
    float totalParkings;      // Total parking sessions
    int height;               // AVL tree height
    struct details_tag *left, *right;
} details;
```

Why AVL Trees?
- **O(log n) Operations**: Guaranteed logarithmic time complexity for search, insert, and delete
- **Self-balancing**: Maintains optimal tree height automatically
- **Efficient Sorting**: In-order traversal provides sorted data
- **Memory Efficient**: Minimal overhead compared to other balanced trees

•Algorithms

Tree Operations
- **AVL Insertion**: Self-balancing insertion with rotation operations
- **AVL Search**: Efficient O(log n) search operations
- **Tree Rotations**: Left and right rotations for maintaining balance
- **Height Calculation**: Dynamic height updates during operations

Sorting Algorithms
- **In-order Traversal**: For ascending order sorting
- **Reverse In-order**: For descending order sorting
- **Multi-key Sorting**: Custom comparison functions for different criteria

Allocation Algorithm
- **Smart Space Allocation**: Membership-based priority allocation
- **Recursive Search**: Depth-first search for available spaces
- **Eligibility Check**: Membership verification for restricted areas

Time Calculation
- **Duration Computation**: Precise time difference calculation using `mktime()` and `difftime()`
- **Ceiling Function**: Hour-based billing with ceiling rounding

•Operations

Management
- **Registration**: New user creation with vehicle number validation
- **Authentication**: Name-based verification for existing users
- **Search**: O(log n) user lookup by vehicle number
- **Update**: Dynamic user information updates

Parking Operations
- **Space Allocation**: Intelligent parking space assignment
- **Status Management**: Real-time parking status updates
- **Duration Tracking**: Automatic parking time calculation
- **Payment Processing**: Dynamic fare calculation with membership discounts

Data Analytics
- **Revenue Analysis**: Per-space and total revenue calculation
- **Occupancy Statistics**: Space utilization metrics
- **User Analytics**: Customer behavior analysis
- **Sorting Operations**: Multi-criteria data organization

File Operations
- **Data Persistence**: Automatic save/load functionality
- **Tree Serialization**: Efficient tree structure storage
- **Error Handling**: Robust file operation error management

•Installation & Usage

Prerequisites
- GCC Compiler
- Standard C Libraries
- Terminal/Command Prompt

Compilation
```bash
gcc -o parking_system parking_system.c -lm
```

Running the System
```bash
./parking_system
```

Menu Options
1. **User Interface**: Vehicle entry and exit management
2. **Display Records**: View all parking system records
3. **Sort by Amount**: Display users sorted by total amount paid
4. **Sort by Parkings**: Display users sorted by parking frequency
5. **Parking Analytics**: View parking spaces sorted by occupancy and revenue
6. **Exit**: Save data and terminate

•File Structure

```
parking-management-system/
│
├── parking_system.c          # Main source code
├── user_tree_data.txt       # User data persistence file
├── status_tree_data.txt     # Parking status data file
├── README.md                # This file
└── LICENSE                  # License information
```

•System Architecture

Membership Hierarchy
- **Golden (Level 2)**: Access to spaces 1-50, 10% discount, requires 200+ hours
- **Premium (Level 1)**: Access to spaces 11-50, 10% discount, requires 100+ hours  
- **General (Level 0)**: Access to spaces 21-50, no discount

Pricing Structure
- **First 3 hours**: ₹100 per hour
- **Additional hours**: ₹50 per hour
- **Membership discount**: 10% for Premium and Golden members

Space Allocation Priority
1. **Spaces 1-10**: Golden members only
2. **Spaces 11-20**: Premium and Golden members
3. **Spaces 21-50**: All members

•Future Enhancements

- **GUI Implementation**: Graphical user interface for better user experience
- **Database Integration**: Migration from file-based to database storage
- **Mobile App**: Android/iOS application for remote parking management
- **Payment Gateway**: Integration with digital payment systems
- **IoT Integration**: Sensor-based automatic space detection
- **Reservation System**: Advance parking space booking
- **Analytics Dashboard**: Real-time analytics and reporting
- **Multi-location Support**: Support for multiple parking facilities

•Performance Metrics

- **Search Complexity**: O(log n)
- **Insertion Complexity**: O(log n)
- **Space Complexity**: O(n)
- **Maximum Parking Spaces**: 50 (configurable)
- **File I/O**: Efficient binary tree serialization
