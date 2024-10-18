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
- 

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

3. Important Step

To uncomment the password line in the `DATABASES` configuration of `settings.py` in a Django project, you should follow these steps:

1. Open the `settings.py` file in your project directory.

2. Find the `DATABASES` setting, which typically looks like this:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',  # Example for PostgreSQL
        'NAME': 'your_database_name',
        'USER': 'your_database_user',
        'PASSWORD': 'your_database_password',  # This line is commented
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

3. Look for the password line that is commented out. It will appear as follows:

```python
# 'PASSWORD': 'your_database_password',  # This line is commented
```

4. Uncomment the password line by removing the `#` symbol at the beginning of the line, like this:

```python
'PASSWORD': 'your_database_password',  # This line is now uncommented
```

5. Save the `settings.py` file.

Once this is done, the system will be able to use the database password when connecting to the database.


6. Apply migrations:

   ```bash
   python manage.py makemigrations
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




This updated README includes information on both the user and driver registration features, booking system functionality, real-time notifications via WebSocket, and the integration of a map for tracking.
