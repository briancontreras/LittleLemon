# LittleLemon Restaurant API

A Django REST API project for managing a restaurant's menu and booking system. This project provides endpoints for menu management and table reservations with authentication support.

## 🍋 Features

- **Menu Management**: CRUD operations for restaurant menu items
- **Booking System**: Table reservation management
- **Authentication**: Token-based authentication using Django REST Framework
- **RESTful API**: Clean, RESTful endpoints for all operations

## 🛠️ Tech Stack

- **Backend**: Django 4.x
- **API Framework**: Django REST Framework
- **Authentication**: Django REST Framework Token Authentication
- **Database**: SQLite (development) / MySQL (production ready)
- **Python Version**: 3.12

## 📋 Prerequisites

- Python 3.12 or higher
- pipenv (for dependency management)

## 🚀 Installation & Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd LittleLemon
   ```

2. **Install dependencies**
   ```bash
   cd Littlelemon
   pipenv install
   ```

3. **Activate virtual environment**
   ```bash
   pipenv shell
   ```

4. **Run migrations**
   ```bash
   python manage.py migrate
   ```

5. **Create superuser (optional)**
   ```bash
   python manage.py createsuperuser
   ```
   
   **Pre-configured superuser accounts:**
   - Username: `b`, Password: `superb`
   - Username: `brian`, Password: `superbrian`

6. **Run the development server**
   ```bash
   python manage.py runserver
   ```

The API will be available at `http://localhost:8000/`

## 📚 API Endpoints

### Authentication

#### Get Authentication Token
```
POST /restaurant/api-token-auth/
```
**Request Body:**
```json
{
    "username": "your_username",
    "password": "your_password"
}
```
**Response:**
```json
{
    "token": "your_auth_token"
}
```

### Menu Management

#### Get All Menu Items
```
GET /restaurant/menu/
```
**Headers:** `Authorization: Token your_auth_token`

#### Create New Menu Item
```
POST /restaurant/menu/
```
**Headers:** `Authorization: Token your_auth_token`
**Request Body:**
```json
{
    "title": "Margherita Pizza",
    "price": "12.99",
    "inventory": 50
}
```

#### Get Specific Menu Item
```
GET /restaurant/menu/{id}/
```

#### Update Menu Item
```
PUT /restaurant/menu/{id}/
```
**Headers:** `Authorization: Token your_auth_token`

#### Delete Menu Item
```
DELETE /restaurant/menu/{id}/
```

### Booking Management

#### Get All Bookings
```
GET /restaurant/booking/
```
**Headers:** `Authorization: Token your_auth_token`

#### Create New Booking
```
POST /restaurant/booking/
```
**Headers:** `Authorization: Token your_auth_token`
**Request Body:**
```json
{
    "name": "John Doe",
    "no_of_guests": 4,
    "bookingDate": "2024-01-15T19:00:00Z"
}
```

#### Get Specific Booking
```
GET /restaurant/booking/{id}/
```

#### Update Booking
```
PUT /restaurant/booking/{id}/
```

#### Delete Booking
```
DELETE /restaurant/booking/{id}/
```

## 🗄️ Data Models

### Menu Model
- `id` (IntegerField, Primary Key)
- `title` (CharField, max_length=255)
- `price` (DecimalField, max_digits=10, decimal_places=2)
- `inventory` (IntegerField)

### Booking Model
- `id` (IntegerField, Primary Key)
- `name` (CharField, max_length=255)
- `no_of_guests` (IntegerField)
- `bookingDate` (DateTimeField)

### User Model
- `url` (CharField, max_length=255)
- `username` (CharField, max_length=255)
- `email` (CharField, max_length=255)
- `groups` (CharField, max_length=255)

## 🔧 Testing with Insomnia

1. **Get Authentication Token:**
   - Method: `POST`
   - URL: `http://localhost:8000/restaurant/api-token-auth/`
   - Body: `{"username": "b", "password": "superb"}`

2. **Use Token for Protected Endpoints:**
   - Add header: `Authorization: Token your_token_here`

## 📁 Project Structure

```
LittleLemon/
├── Littlelemon/
│   ├── restaurant/
│   │   ├── models.py          # Data models
│   │   ├── views.py           # API views
│   │   ├── serializers.py     # Data serializers
│   │   ├── urls.py            # URL routing
│   │   ├── admin.py           # Admin configuration
│   │   └── templates/         # HTML templates
│   ├── Littlelemon/
│   │   ├── settings.py        # Django settings
│   │   ├── urls.py            # Main URL configuration
│   │   └── wsgi.py            # WSGI configuration
│   ├── manage.py              # Django management script
│   ├── Pipfile                # Dependencies
│   └── db.sqlite3             # Database file
└── README.md                  # This file
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🆘 Support

If you encounter any issues or have questions, please open an issue in the repository.
