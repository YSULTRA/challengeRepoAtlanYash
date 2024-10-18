Here’s an updated version of the `README.md` for your project, now incorporating the user, driver, and admin features, as well as the logistics platform features as described in the context:

```markdown
# Driver Booking System with WebSocket Notifications

An on-demand logistics platform that connects users who need goods transportation with a fleet of drivers, providing real-time availability, pricing, and tracking. The system supports high scalability, with features for both users and drivers, and real-time vehicle tracking using WebSockets and geolocation APIs.

---

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
  - [User Features](#user-features)
  - [Driver Features](#driver-features)
  - [Admin Features](#admin-features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [License](#license)

---

## Introduction
This project is designed to provide a real-time logistics platform for users to book transportation services and track vehicles. It allows drivers to register, accept/reject delivery requests, and update the status of their job. The platform uses Django and Django Channels for WebSocket-based real-time communication, and Mapbox API for geolocation and real-time tracking.

---

## Features

### User Features
- **Account Registration and Login:**
    - Users can register and log in to their accounts to book transportation services for goods.
    - Users can view available vehicles, request a booking, and receive real-time notifications.
  
- **Booking Service:**
    - Users can book a vehicle for transporting goods, including specifying pickup and drop-off locations, vehicle type, and estimated cost.
  
- **Real-Time Tracking:**
    - Once a vehicle is booked, users can track the driver's real-time location on a map.

- **Price Estimation:**
    - Users are provided with upfront price estimates based on distance, vehicle type, and demand.

### Driver Features
- **Driver Registration and Login:**
    - Drivers can register and log in to their accounts.
  
- **Job Acceptance/Decline:**
    - Drivers receive real-time booking requests and can accept or reject the job based on availability.

- **Job Status Updates:**
    - Drivers can update the status of their job (e.g., en route, goods collected, delivered).

- **Real-Time Location Sharing:**
    - Drivers’ real-time locations are shared with users for tracking purposes using WebSockets.

### Admin Features
- **Fleet Management:**
    - Admins can monitor and manage the fleet of available vehicles and their status.
  
- **Data Analytics:**
    - Admins can view statistics like the number of trips completed, average trip time, driver performance, etc.

---

## Requirements
- Python 3.8 or higher
- Django 3.x or higher
- Channels
- Channels Redis (for real-time communication)
- Mapbox API Key for geolocation and tracking
- SQLite (default database, replaceable with other databases)

---

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/driver-booking-system.git
   cd driver-booking-system
   ```

2. Create and activate a virtual environment:

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Set up your Mapbox API key:
   - Sign up at [Mapbox](https://www.mapbox.com/).
   - Get your API key and set it in the environment variables or the config file.

5. Apply migrations:

   ```bash
   python manage.py migrate
   ```

6. Create a superuser (optional, for admin access):

   ```bash
   python manage.py createsuperuser
   ```

7. Run the development server:

   ```bash
   python manage.py runserver
   ```

8. Access the application at `http://127.0.0.1:8000`.

---

## Configuration

- **ASGI Configuration:** In `asgi.py`, the WebSocket routing is configured. Ensure your production environment supports ASGI for real-time communication.
  
- **WebSocket Consumer:** `DriverNotificationConsumer` handles real-time updates for drivers, notifying them about booking requests and tracking user interactions.

- **Geolocation:** The `get_coordinates` function uses the Mapbox API to convert user-specified locations into latitude and longitude coordinates, which is essential for matching users with nearby drivers.

---

## Usage

### For Users:
- **Register/Login:** Create an account, log in, and access the booking system.
- **Book a Ride:** Input your pickup and drop-off locations, choose a vehicle, and view the estimated cost.
- **Track Real-Time:** Once a ride is booked, track the driver's location on the map.
- **Receive Notifications:** Get real-time updates on the status of your booking via WebSocket notifications.

### For Drivers:
- **Register/Login:** Create a driver profile, log in, and set your availability.
- **Accept or Reject Jobs:** View booking requests and accept or reject them based on your availability.
- **Update Job Status:** As you proceed with the booking, update the status (en route, goods collected, delivered).
- **Share Real-Time Location:** Your location is shared with users for tracking purposes.

### For Admins:
- **Monitor Fleet:** View available drivers and vehicles.
- **Track Booking Statistics:** View data on completed trips, average times, and driver performance.

---

## Project Structure

```
driver-booking-system/
│
├── your_project/                   # Django project folder
│   ├── __init__.py
│   ├── settings.py                 # Django settings file
│   ├── urls.py                     # URL routing
│   ├── asgi.py                     # ASGI configuration for Channels
│
├── your_app/                       # Your Django app
│   ├── __init__.py
│   ├── models.py                   # Database models (Booking, Driver, etc.)
│   ├── views.py                    # Views for booking and driver management
│   ├── consumers.py                # WebSocket consumer for driver notifications
│   ├── templates/
│   │   └── driver_notification.html  # WebSocket UI for the driver
│   └── static/                     # Static files (CSS, JS)
├── requirements.txt                # Python dependencies
├── manage.py                       # Django management script
└── README.md                       # Project documentation
```

### Important Files:
- **`your_project/asgi.py`**: Configures the ASGI application and WebSocket routing.
- **`your_app/consumers.py`**: Contains the WebSocket consumer to handle real-time communication.
- **`your_app/models.py`**: Defines the booking, user, and driver models.
- **`your_app/views.py`**: Contains views for handling the booking logic.
- **`your_app/templates/driver_notification.html`**: WebSocket interface for the driver.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Feel free to contribute to the project, raise issues, or suggest improvements. If you have any questions, don't hesitate to reach out via the [GitHub Issues](https://github.com/your-username/driver-booking-system/issues).

```

### Customization Notes:
- Replace `your-username` with your actual GitHub username.
- Modify sections to better match your project implementation or requirements.

This updated README includes information on both the user and driver registration features, booking system functionality, real-time notifications via WebSocket, and the integration of a map for tracking.
