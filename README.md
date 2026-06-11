# 🏨 GetAWAY — Resort Management System

> A full-stack PHP-based hotel and resort management web application featuring a public-facing website for guests and a secured administrative dashboard for hotel staff.

---

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Features](#-features)
  - [Guest-Facing Frontend](#guest-facing-frontend)
  - [Admin Panel](#admin-panel)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Database Schema](#-database-schema)
  - [Tables Overview](#tables-overview)
  - [Table Details](#table-details)
- [Module Breakdown](#-module-breakdown)
  - [Frontend (index.php)](#frontend-indexphp)
  - [Admin Login (admin/index.php)](#admin-login-adminindexphp)
  - [Admin Dashboard (admin/home.php)](#admin-dashboard-adminhomephp)
  - [Room Reservation (admin/reservation.php)](#room-reservation-adminreservationphp)
  - [Room Booking Management (admin/roombook.php)](#room-booking-management-adminroombookphp)
  - [Payment Management (admin/payment.php)](#payment-management-adminpaymentphp)
  - [Profit Analytics (admin/profit.php)](#profit-analytics-adminprofitphp)
  - [Newsletter / Followers (admin/messages.php)](#newsletter--followers-adminmessagesphp)
  - [Room Settings (admin/room.php)](#room-settings-adminroomphp)
  - [Print Receipt (admin/print.php)](#print-receipt-adminprintphp)
  - [User Settings (admin/usersetting.php)](#user-settings-adminusersettingphp)
  - [Logout (admin/logout.php)](#logout-adminlogoutphp)
- [Room Types & Pricing](#-room-types--pricing)
- [Booking Flow](#-booking-flow)
- [Admin Workflow](#-admin-workflow)
- [Frontend UI Sections](#-frontend-ui-sections)
- [CSS Libraries & Styling](#-css-libraries--styling)
- [JavaScript Libraries](#-javascript-libraries)
- [Installation & Setup](#-installation--setup)
- [Default Login Credentials](#-default-login-credentials)
- [Known Limitations & Security Notes](#️-known-limitations--security-notes)
- [Screenshots Summary](#-screenshots-summary)
- [Contact Information (Demo)](#-contact-information-demo)

---

## 🌐 Project Overview

**GetAWAY** is a web-based **Resort Management System** built with PHP and MySQL. It serves two primary user groups:

1. **Guests / Visitors** — Browse the resort's website, view room types, read testimonials, check the gallery, and submit contact/newsletter subscription forms.
2. **Hotel Administrators** — Log into a private dashboard to manage bookings, confirm or deny reservations, process payments, track profit, manage the room inventory, and send newsletters.

The project was originally developed as an academic or portfolio project (circa 2017) and includes a realistic end-to-end booking experience including CAPTCHA-style human verification and QR-based payment acknowledgment.

---

## ✨ Features

### Guest-Facing Frontend

| Feature | Description |
|---|---|
| **Responsive Header** | Top navigation bar with logo, social media links (Facebook, Twitter, Google+), phone, email, and a search box |
| **Hero Banner Slider** | Full-screen slideshow with 3 slides using ResponsiveSlides.js |
| **Room Reservation CTA** | Direct link to the reservation form from the homepage |
| **About Section** | Describes the resort philosophy and amenities |
| **Services Section** | Highlights "Stay First, Pay After" policy and 24-hour restaurant |
| **Team Section** | Tab-style profile cards for 4 team members (managers and receptionists) |
| **Photo Gallery** | 12-image gallery with SwipeBox popup lightbox |
| **Rooms & Rates** | Pricing cards for 4 room categories (Superior, Deluxe, Guest House, Single) with star ratings |
| **Testimonials Slider** | FlexSlider carousel with 4 guest reviews |
| **Contact & Newsletter Form** | Submits guest name, phone, and email to the database for newsletter subscription |
| **Google Maps Embed** | Interactive map pointing to Tannirbhavi Beach, Mangalore |
| **Footer** | Copyright notice |
| **Admin Login Button** | Prominent link to `admin/index.php` in the header |

### Admin Panel

| Feature | Description |
|---|---|
| **Secure Login** | Session-based authentication with username and password from the `login` table |
| **Status Dashboard** | Shows pending bookings (not confirmed), confirmed bookings, and newsletter followers |
| **Room Booking Management** | View all reservations, confirm/deny with action buttons |
| **Payment Processing** | View confirmed booking payment breakdowns including room rent, bed charges, meals, and grand total |
| **Profit Analytics** | Bar chart visualization (Morris.js) and table showing 10% profit margin per booking |
| **Newsletter Management** | View all subscribers, grant/revoke newsletter permission, delete subscribers, and compose/send new newsletters |
| **Room Settings** | View all rooms with their type, bedding, and availability status; add or delete rooms |
| **Print Receipts** | Generate printable payment receipts for confirmed bookings |
| **User Profile / Settings** | View and update admin username and password |
| **Logout** | Destroys session and redirects to login page |

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| **Server-side Language** | PHP 5.5+ (procedural style) |
| **Database** | MySQL 5.6 (via `mysqli_*` functions) |
| **Frontend Framework** | Bootstrap 3.x |
| **Icon Library** | Font Awesome 4.x |
| **Slider (Homepage Banner)** | ResponsiveSlides.js |
| **Testimonials Slider** | FlexSlider |
| **Gallery Lightbox** | jQuery SwipeBox |
| **Responsive Tabs** | Easy Responsive Tabs |
| **Date Picker** | jQuery UI Datepicker |
| **Charts (Admin)** | Morris.js + Raphael.js |
| **Data Tables (Admin)** | jQuery DataTables |
| **Form Validation** | jqBootstrapValidation.js |
| **Smooth Scrolling** | move-top.js + easing.js |
| **Modernizr** | v2.6.2 (feature detection) |
| **Google Fonts** | Oswald, Federo, Lato (frontend) / Open Sans (admin) |
| **Local Dev Environment** | XAMPP / WAMP (Apache + PHP + MySQL) |

---

## 📁 Project Structure

```
resort-management-system/
│
├── index.php                  # Main public-facing homepage
├── db.php                     # Root-level database connection (for frontend)
├── hotel.sql                  # MySQL database dump (import to set up DB)
├── Information.txt            # Quick-start credentials reference
│
├── css/                       # Frontend CSS stylesheets
│   ├── bootstrap.css          # Bootstrap 3 grid & components
│   ├── font-awesome.css       # Icon fonts
│   ├── style.css              # Primary custom styles (66KB)
│   ├── chocolat.css           # Chocolat lightbox CSS
│   ├── easy-responsive-tabs.css
│   ├── flexslider.css         # FlexSlider carousel CSS
│   ├── jquery-ui.css          # jQuery UI datepicker/widgets
│   ├── swipebox.css           # SwipeBox gallery CSS
│   └── common.css             # Minimal shared overrides
│
├── js/                        # Frontend JavaScript libraries
│   ├── jquery-2.1.4.min.js    # jQuery core
│   ├── bootstrap-3.1.1.min.js # Bootstrap JS
│   ├── jquery-ui.js           # jQuery UI (450KB, includes datepicker)
│   ├── jquery.flexslider.js   # FlexSlider plugin
│   ├── jquery.swipebox.min.js # SwipeBox gallery popup
│   ├── responsiveslides.min.js# Banner slider
│   ├── easy-responsive-tabs.js# Tab plugin for team section
│   ├── jqBootstrapValidation.js # Form validation
│   ├── modernizr-2.6.2.min.js # Feature detection
│   ├── main.js                # Custom initialization scripts
│   ├── move-top.js            # Scroll-to-top utility
│   └── easing.js              # jQuery easing functions
│
├── images/                    # All frontend images (45 files)
│   ├── 1.jpg, 2.jpg, 3.jpg    # Hero banner background images
│   ├── about.jpg, a1.jpg      # About section images
│   ├── r1.jpg–r4.jpg          # Room category thumbnail images
│   ├── g1.jpg–g10.jpg         # Gallery images
│   ├── c1.jpg–c4.jpg          # Service/category images
│   ├── sajjun.jpg, meetha.jpg,
│   │   dachui.jpg, arav.jpg   # Testimonial reviewer photos
│   ├── teamb1.jpg–teamb4.jpg,
│   │   teams2.jpg–teams4.jpg  # Team member photos
│   ├── services.jpg           # Services section background
│   ├── contact.jpg            # Contact section background
│   ├── sumanth.jpg, sruj.jpg  # Additional team/profile photos
│   └── icons.svg, arr.png,
│       c-arrows.png, etc.     # UI icons/arrows
│
├── fonts/                     # Font Awesome webfont files
│   ├── FontAwesome.otf
│   ├── fontawesome-webfont.eot/.svg/.ttf/.woff/.woff2
│   └── glyphicons-halflings-regular.*
│
└── admin/                     # Admin panel (protected area)
    ├── index.php              # Admin login page
    ├── home.php               # Dashboard (status overview)
    ├── reservation.php        # Public room booking form
    ├── roombook.php           # Manage all reservations
    ├── roomdel.php            # Delete a reservation
    ├── room.php               # Room inventory management
    ├── payment.php            # Payment details view
    ├── profit.php             # Profit analytics with chart
    ├── print.php              # Print receipt for a booking
    ├── show.php               # Show detailed booking info
    ├── messages.php           # Newsletter subscriber management
    ├── newsletter.php         # Grant/revoke newsletter permission
    ├── newsletterdel.php      # Delete a subscriber
    ├── settings.php           # General settings page
    ├── usersetting.php        # Admin profile management
    ├── usersettingdel.php     # Delete an admin user
    ├── logout.php             # Session destroy + redirect
    ├── db.php                 # Admin database connection (duplicate)
    ├── css/
    │   └── style.css          # Admin login page cloud animation styles
    └── assets/                # Admin panel assets
        ├── css/               # Bootstrap, Font Awesome, custom admin CSS
        ├── js/                # jQuery, Bootstrap, Morris.js, DataTables, MetisMenu
        ├── fonts/             # Admin font files
        ├── font-awesome/      # Admin Font Awesome assets
        └── img/
            └── gpayqr.jpg     # Google Pay QR code for payments
```

---

## 🗄 Database Schema

### Tables Overview

| Table | Purpose |
|---|---|
| `login` | Admin user credentials |
| `room` | Master room inventory with availability status |
| `roombook` | Guest reservation/booking records |
| `payment` | Processed payment details for confirmed bookings |
| `contact` | Newsletter subscribers (from contact form) |
| `newsletterlog` | Archive of sent newsletter messages |

> **Database name:** `hotel`
> **File:** `hotel.sql` (import this into phpMyAdmin or MySQL CLI)

---

### Table Details

#### `login` — Admin Credentials
| Column | Type | Description |
|---|---|---|
| `id` | INT(10) UNSIGNED, PK | Auto-incremented ID |
| `usname` | VARCHAR(30) | Admin username |
| `pass` | VARCHAR(30) | Admin password (plain text — see security notes) |

**Pre-seeded data:**
```
Admin / 1234
Prasath / 12345
```

---

#### `room` — Room Inventory
| Column | Type | Description |
|---|---|---|
| `id` | INT(10) UNSIGNED, PK | Room ID |
| `type` | VARCHAR(15) | Room type (Superior Room, Deluxe Room, Guest House, Single Room) |
| `bedding` | VARCHAR(10) | Bedding type (Single, Double, Triple, Quad) |
| `place` | VARCHAR(10) | Availability status (`Free` or occupied) |
| `cusid` | INT(11) | Associated customer ID (nullable) |

**Pre-seeded rooms (15 total):**
- Superior Room: Single, Double, Triple, Quad (×2)
- Deluxe Room: Single, Double, Triple, Quad
- Guest House: Single, Double, Quad
- Single Room: Single, Double, Triple, Quad

---

#### `roombook` — Reservation Records
| Column | Type | Description |
|---|---|---|
| `id` | INT(10) UNSIGNED, PK | Booking ID |
| `Title` | VARCHAR(5) | Salutation (Mr., Mrs., Dr., etc.) |
| `FName` | TEXT | Guest first name |
| `LName` | TEXT | Guest last name |
| `Email` | VARCHAR(50) | Guest email (used for duplicate check) |
| `National` | VARCHAR(30) | Nationality (Indian / Non Indian) |
| `Country` | VARCHAR(30) | Passport country |
| `Phone` | TEXT | Phone number (max 10 chars) |
| `TRoom` | VARCHAR(20) | Room type selected |
| `Bed` | VARCHAR(10) | Bedding type selected |
| `NRoom` | VARCHAR(2) | Number of rooms |
| `Meal` | VARCHAR(15) | Meal plan (Room only, Breakfast, Half Board, Full Board) |
| `cin` | DATE | Check-in date |
| `cout` | DATE | Check-out date |
| `stat` | VARCHAR(15) | Booking status (`Not Confirm` or `Confirm`) |
| `nodays` | INT(11) | Calculated number of stay days (auto-calculated via SQL `DATEDIFF`) |

---

#### `payment` — Payment Records
| Column | Type | Description |
|---|---|---|
| `id` | INT(11) | Booking reference ID |
| `title` | VARCHAR(5) | Salutation |
| `fname` | VARCHAR(30) | First name |
| `lname` | VARCHAR(30) | Last name |
| `troom` | VARCHAR(30) | Room type |
| `tbed` | VARCHAR(30) | Bed type |
| `nroom` | INT(11) | Number of rooms |
| `cin` | DATE | Check-in date |
| `cout` | DATE | Check-out date |
| `ttot` | DOUBLE(8,2) | Room rent total |
| `fintot` | DOUBLE(8,2) | Final grand total |
| `mepr` | DOUBLE(8,2) | Meal price per day |
| `meal` | VARCHAR(30) | Meal plan name |
| `btot` | DOUBLE(8,2) | Bed/board total |
| `noofdays` | INT(11) | Number of days stayed |

---

#### `contact` — Newsletter Subscribers
| Column | Type | Description |
|---|---|---|
| `id` | INT(10) UNSIGNED, PK | Subscriber ID |
| `fullname` | VARCHAR(100) | Subscriber full name |
| `phoneno` | INT(10) | Phone number |
| `email` | TEXT | Email address |
| `cdate` | DATE | Date subscribed |
| `approval` | VARCHAR(12) | Permission status (`Allowed` or `Not Allowed`) |

---

#### `newsletterlog` — Sent Newsletters
| Column | Type | Description |
|---|---|---|
| `id` | INT(10) UNSIGNED, PK | Log entry ID |
| `title` | VARCHAR(52) | Newsletter title |
| `subject` | VARCHAR(100) | Newsletter subject line |
| `news` | TEXT | Newsletter body content |

---

## 🔍 Module Breakdown

### Frontend (`index.php`)

The single-page public website. It includes the database connection (`db.php`) and handles the newsletter sign-up form POST submission inline. Key sections:

- **Header/Navbar** — Bootstrap responsive navbar with brand name "GET AWAY", navigation links (Home, About, Team, Gallery, Rooms, Contact Us), an "Admin Login" button, social icons, phone, email, and a toggle search bar.
- **Hero Slider** — 3-slide responsive banner with taglines like *"We know what you love"*, *"Stay with friends & families"*, and *"Want luxurious vacation?"*. Each slide has a "Learn More" button that opens a Bootstrap modal.
- **Room Reservation Quick Link** — A prominent banner strip linking directly to the reservation page.
- **About Section** — Description and two images.
- **Services Section** — "Stay first, Pay after" and "24 Hour Restaurant" service highlights.
- **Team Section** — Tabbed profiles: Dejesh Poojay (Manager), Vamini Smith (Receptionist), Jayaram Simpson (Manager), Power Prasanna (Receptionist).
- **Gallery** — 12 images in a 4-column grid with SwipeBox popup.
- **Rooms & Rates** — 4 pricing cards with room image, star rating, price per night, and a "Book Now" link.
- **Testimonials** — FlexSlider with 4 real visitor testimonial cards (Padma Prabhu, Vijay Kaltappa, Appu Shetty, Annachi Kutikere).
- **Contact Form** — Submits to `contact` table. Fields: Full Name, Phone Number, Email Address. Status is initialized to `"Not Allowed"`.
- **Google Maps** — Embedded iframe for Tannirbhavi Beach, Mangalore.
- **JavaScript initialization** — Smooth scroll, datepicker, SwipeBox, FlexSlider, ResponsiveSlides, responsive tabs all initialized at page bottom.

---

### Admin Login (`admin/index.php`)

- Animated CSS cloud background (clouds CSS in `admin/css/style.css`)
- If already logged in (`$_SESSION["user"]` is set), redirects to `home.php`
- POST form with `user` and `pass` fields
- Authenticates against the `login` table using `mysqli_real_escape_string`
- On success: sets `$_SESSION['user']` and `$_SESSION['pass']`, redirects to `home.php`
- On failure: shows a JavaScript `alert` with "Your Login Name or Password is invalid"
- "GET AWAY HOMEPAGE" link at the bottom to return to the public site

---

### Admin Dashboard (`admin/home.php`)

- **Session guard**: redirects to `index.php` if not logged in
- **Sidebar navigation**: Status, News Letters, Room Booking, Payment, Profit, Room Settings, Logout
- **Top navbar**: shows logged-in username; dropdown for User Profile, Settings, Logout
- **New Room Bookings panel** (blue): Table of all reservations with `stat = "Not Confirm"`, with columns: #, Name, Email, Country, Room, Bedding, Meal, Check In, Check Out, Status, and an "Action" link to `roombook.php?rid=`
- **Newly Booked Rooms panel** (info): Card grid of confirmed bookings showing guest name and a "Show" button to `show.php?sid=`
- **Followers panel** (danger): Table of all `contact` entries with their approval status
- **Update Modal**: Inline form to change admin username and password

---

### Room Reservation (`admin/reservation.php`)

This page is **accessible without login** — it serves as the **public booking form** linked from the homepage.

**Personal Information section:**
- Title (Dr., Miss., Mr., Mrs., Prof., Rev., Rev. Fr)
- First Name, Last Name, Email
- Nationality (Indian / Non Indian radio buttons)
- Passport Country (full world country dropdown — 200+ countries)
- Phone Number

**Reservation Information section:**
- Room Type: Superior Room, Deluxe Room, Guest House, Single Room
- Bedding Type: Single, Double, Triple, Quad, None
- Number of Rooms: currently limited to 1
- Meal Plan: Room only, Breakfast, Half Board, Full Board
- Check-In Date (minimum: today)
- Check-Out Date (minimum: day after check-in; validated by JS)

**Payment & Verification section:**
- Displays a GPay QR code image (`assets/img/gpayqr.jpg`) with per-room pricing
- Input for Transaction ID
- **CAPTCHA-style Human Verification**: a random integer (`rand()`) displayed, user must type it back correctly
- Legal notice: *"Once you have booked the resort, cancellation is not possible. If you do not pay, you will be fined, legally."*

**Server-side logic:**
1. Validates CAPTCHA (user-entered code vs hidden field)
2. Checks if email already exists in `roombook`
3. Checks room availability for selected dates (max 4 bookings of same type allowed)
4. Inserts booking with `stat = "Not Confirm"` and calculated `nodays` via `DATEDIFF`
5. Also inserts transaction ID into `qrpay` table (note: `qrpay` table not in `hotel.sql` — may need manual creation)

---

### Room Booking Management (`admin/roombook.php`)

- Lists all bookings from `roombook` table
- Admin can confirm or reject a booking
- When confirmed, the booking data is moved/copied to the `payment` table with calculated amounts
- When rejected/deleted, `roomdel.php` removes the record

---

### Payment Management (`admin/payment.php`)

- Session-protected admin page
- Reads all records from the `payment` table
- Displays in a DataTables-powered table with columns: Name, Room type, Bed Type, Check in, Check out, No of Rooms, Meal Type, Room Rent, Bed Rent, Meals, Grand Total, Print
- Alternating row colors (gradeC / gradeU)
- Each row has a "Print" button linking to `print.php?pid=<id>`

---

### Profit Analytics (`admin/profit.php`)

- Session-protected admin page
- Reads all `payment` records
- **Morris.js Bar Chart**: plots profit per checkout date; profit calculated as `fintot * 10 / 100` (10% of grand total)
- **Data table**: same records showing Room Rent (₹), Bed Rent (₹), Meals (₹), Grand Total (₹), and Profit (₹)
- Running total accumulated in `$tot` variable (displayed in chart data)

---

### Newsletter / Followers (`admin/messages.php`)

- Session-protected admin page
- **Compose Newsletter modal**: Admin can enter Title, Subject, and News body; saved to `newsletterlog` table
- **Subscribers table**: Lists all `contact` entries with Name, Phone, Email, Subscription Date, Approval status
- Each row has:
  - "Permission" button → `newsletter.php?eid=<id>` (toggles approval between Allowed/Not Allowed)
  - "Delete" button → `newsletterdel.php?eid=<id>` (removes subscriber)

---

### Room Settings (`admin/room.php`)

- Session-protected admin page
- Displays all rooms from the `room` table with ID, Type, Bedding, Availability
- Admin can add new rooms or delete existing ones
- Room availability is reflected here and used by the booking availability check

---

### Print Receipt (`admin/print.php`)

- Generates a formatted, printable receipt for a specific payment record (identified by `?pid=`)
- Intended to be opened in a new window for browser print functionality

---

### User Settings (`admin/usersetting.php`)

- Session-protected admin page
- Allows updating admin username and password stored in the `login` table
- **Delete** functionality via `usersettingdel.php`

---

### Logout (`admin/logout.php`)

```php
session_start();
session_destroy();
header("location: index.php");
```

Destroys the session and redirects to the admin login page.

---

## 🏠 Room Types & Pricing

| Room Type | Rate per Night | Star Rating |
|---|---|---|
| **Superior Room** | ₹3,200 | ⭐⭐⭐⭐ |
| **Deluxe Room** | ₹2,200 | ⭐⭐⭐⭐ |
| **Guest House** | ₹1,800 | ⭐⭐⭐ |
| **Single Room** | ₹1,500 | ⭐⭐⭐⭐⭐ |

**Bedding options available:** Single, Double, Triple, Quad

**Meal plans available:**
- Room only
- Breakfast
- Half Board
- Full Board

---

## 🔄 Booking Flow

```
Guest visits index.php
        │
        ├──► Clicks "Book Now" or "ROOM RESERVATION"
        │
        ▼
admin/reservation.php (public — no login required)
        │
        ├── Fills personal info (name, email, nationality, country, phone)
        ├── Selects room type, bed type, meal plan, dates
        ├── Scans GPay QR code and pays
        ├── Enters Transaction ID
        └── Completes human verification CAPTCHA
                │
                ▼ (server-side checks)
                ├── CAPTCHA valid?
                ├── Email not already booked?
                └── Room available for those dates? (max 4 of same type)
                        │
                        ▼
                INSERT into `roombook` (stat = "Not Confirm")
                INSERT into `qrpay` (transaction ID)
                        │
                        ▼
                Alert: "Your booking application has been sent"
                        │
                        ▼
                Admin sees it on dashboard (home.php)
                        │
                        ▼ Admin reviews & confirms
                roombook.php → Confirm Action
                        │
                        ▼
                INSERT into `payment` (with calculated amounts)
                UPDATE `roombook` stat = "Confirm"
                        │
                        ▼
                Admin can view payment.php & print receipt (print.php)
```

---

## 🖥 Admin Workflow

```
Admin visits admin/index.php
        │
        ├── Enters username & password
        └── Authenticated via `login` table
                │
                ▼
        admin/home.php (Dashboard)
                │
                ├── View pending bookings (Not Confirm)
                ├── View confirmed bookings
                ├── View newsletter followers
                │
                ├──► messages.php      — Manage subscribers, send newsletters
                ├──► roombook.php      — Confirm/deny reservations
                ├──► payment.php       — View payment summaries, print receipts
                ├──► profit.php        — Visualize profit per booking (bar chart)
                ├──► room.php          — Manage room inventory
                ├──► usersetting.php   — Update admin credentials
                └──► logout.php        — End session
```

---

## 🎨 Frontend UI Sections

| Section ID | Content |
|---|---|
| `#home` | Hero banner slider |
| `#about` | About the resort |
| `#team` | Meet the team (tabbed) |
| `#gallery` | Photo gallery |
| `#rooms` | Room types and pricing cards |
| `#contact` | Contact form and Google Maps |

Navigation items smoothly scroll to these anchors using jQuery animate.

---

## 🎨 CSS Libraries & Styling

| File | Purpose |
|---|---|
| `css/bootstrap.css` | Bootstrap 3 responsive grid and UI components |
| `css/font-awesome.css` | 500+ scalable vector icons |
| `css/style.css` | Primary custom theme (66KB) — colors, layouts, cards, slider |
| `css/flexslider.css` | Testimonials carousel styles |
| `css/chocolat.css` | Chocolat lightbox styles (imported but swipebox is used) |
| `css/easy-responsive-tabs.css` | Horizontal responsive tabs for Team section |
| `css/jquery-ui.css` | jQuery UI datepicker and widget styles |
| `css/swipebox.css` | Gallery popup overlay styles |
| `css/common.css` | Minor shared overrides |
| `admin/css/style.css` | Admin login page with animated CSS cloud effects |
| `admin/assets/css/custom-styles.css` | Admin dashboard layout, sidebar, panels |

---

## 📜 JavaScript Libraries

| File | Version | Purpose |
|---|---|---|
| `modernizr-2.6.2.min.js` | 2.6.2 | HTML5/CSS3 feature detection |
| `jquery-2.1.4.min.js` | 2.1.4 | Core DOM manipulation library |
| `bootstrap-3.1.1.min.js` | 3.1.1 | Bootstrap modals, dropdowns, collapse |
| `jquery-ui.js` | Latest (bundled) | Datepicker widgets |
| `jquery.flexslider.js` | — | Testimonial carousel |
| `responsiveslides.min.js` | — | Hero banner slider |
| `easy-responsive-tabs.js` | — | Team section tabs |
| `jquery.swipebox.min.js` | — | Gallery lightbox popup |
| `jqBootstrapValidation.js` | — | Client-side Bootstrap form validation |
| `move-top.js` | — | Scroll-to-top animation |
| `easing.js` | — | jQuery easing functions for smooth scroll |
| `main.js` | — | Custom initialization code |

---

## ⚙ Installation & Setup

### Prerequisites

- **XAMPP** (or WAMP/LAMP/MAMP) with:
  - Apache web server
  - PHP 5.5+ (works with PHP 7.x with minor deprecation warnings)
  - MySQL 5.6+
- A web browser

### Steps

1. **Clone or copy** the project folder into your server's web root:
   ```
   C:\xampp\htdocs\resort-management-system\
   ```

2. **Start** Apache and MySQL services from the XAMPP Control Panel.

3. **Import the database:**
   - Open your browser and navigate to: `http://localhost/phpmyadmin`
   - Create a new database named **`hotel`**
   - Select the `hotel` database, click **Import**, and upload `hotel.sql`
   - Click **Go**

4. **Verify database connection** in `db.php`:
   ```php
   $con = mysqli_connect("localhost", "root", "", "hotel");
   ```
   - The default XAMPP MySQL user is `root` with an **empty password**
   - If your MySQL has a password, update the third parameter accordingly

5. **Access the application:**
   - **Frontend (Guest site):** `http://localhost/resort-management-system/index.php`
   - **Admin Login:** `http://localhost/resort-management-system/admin/index.php`

> **Note:** The `admin/db.php` file is a duplicate of the root `db.php`. Both must have the correct connection settings.

---

## 🔑 Default Login Credentials

| Role | Username | Password |
|---|---|---|
| Admin | `Admin` | `1234` |
| Secondary Admin | `Prasath` | `12345` |

---

## ⚠️ Known Limitations & Security Notes

> This project was developed as an academic/portfolio project. The following issues are present and should be addressed before any production deployment:

| Issue | Description | Recommendation |
|---|---|---|
| **SQL Injection** | Most queries use string interpolation directly with `$_POST` values | Use PDO prepared statements or `mysqli_stmt_bind_param` |
| **Plain-text passwords** | Passwords stored as plain text in the `login` table | Use `password_hash()` / `password_verify()` |
| **No CSRF protection** | Forms lack CSRF tokens | Add CSRF token validation to all POST forms |
| **Weak CAPTCHA** | The human verification uses PHP `rand()` stored in a hidden field — trivially bypassable | Use Google reCAPTCHA |
| **No input sanitization** | User inputs are not consistently sanitized | Use `htmlspecialchars()` for output, prepared statements for queries |
| **Session security** | Session IDs are not regenerated after login | Use `session_regenerate_id(true)` after authentication |
| **`qrpay` table missing** | `reservation.php` inserts into a `qrpay` table that is **not included** in `hotel.sql` | Manually create the `qrpay` table or remove that INSERT |
| **Duplicate `db.php`** | Both `/db.php` and `/admin/db.php` exist — they must both be configured identically | Consolidate into a single shared config file |
| **Passwords in session** | `$_SESSION['pass']` stores plain-text password | Never store passwords in session variables |
| **PHP version** | Uses deprecated `mysql_error()` in root `db.php` | Replace with `mysqli_connect_error()` |

---

## 📸 Screenshots Summary

| Page | Description |
|---|---|
| `index.php` | Full-screen hero banner with navigation, rooms section, gallery, testimonials, and contact form |
| `admin/index.php` | Clean login form with animated CSS cloud background |
| `admin/home.php` | Bootstrap-styled dashboard with collapsible panels for bookings and followers |
| `admin/reservation.php` | Two-column booking form with GPay QR code and CAPTCHA verification |
| `admin/payment.php` | DataTable showing full financial breakdown per confirmed booking |
| `admin/profit.php` | Morris.js bar chart + profit data table |
| `admin/messages.php` | Newsletter subscriber list with permission toggles and compose modal |

---

## 📞 Contact Information (Demo)

The demo contact information embedded in the frontend:

| Field | Value |
|---|---|
| **Phone** | +91 (78)994-96-87 |
| **Email** | INFO@GetAWAY.COM |
| **Address** | Summi Nager, Tannirbhavi, Mangalore, India |
| **Location** | Tannirbhavi Beach, Mangalore, Karnataka, India |

---

## 📄 License

This project is an academic/portfolio project. No explicit license is provided.  
Feel free to use it for learning purposes, but ensure proper security hardening before any live deployment.

---

*© 2024 GetAWAY Resort. All Rights Reserved.*
