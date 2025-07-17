# Flask Full CRUD RESTful API - Event Manager

## Overview

This project implements a RESTful API using Python and Flask to manage a list of events. It supports full **CRUD** operations:

- **Create** an event (POST)
- **Read** events (not required in this lab but implied)
- **Update** event title (PATCH)
- **Delete** an event (DELETE)

Data is stored in-memory using a custom `Event` class. All responses are returned as structured JSON with appropriate status codes.

---

## Setup Instructions

1. **Clone the repository**

   ```bash
   git clone <your-repo-url>
   cd course-8-module-5-flask-full-crud-api-lab
   ```

2. **Install dependencies**

   ```bash
   pip install flask
   ```

3. **Run the app**
   ```bash
   python app.py
   ```

---

## API Endpoints

### `POST /events`

Create a new event.

**Request Body**

```json
{
  "title": "Hackathon"
}
```

**Response**

```json
{
  "id": 3,
  "title": "Hackathon"
}
```

**Status:** `201 Created`

---

### `PATCH /events/<id>`

Update the title of an existing event.

**Request Body**

```json
{
  "title": "Hackathon 2025"
}
```

**Response**

```json
{
  "id": 1,
  "title": "Hackathon 2025"
}
```

If not found:

```json
{
  "error": "Event not found"
}
```

**Status:** `200 OK` or `404 Not Found`

---

### `DELETE /events/<id>`

Delete an event by ID.

**Response:** No content.

**Status:** `204 No Content`

If not found:

```json
{
  "error": "Event not found"
}
```

**Status:** `404 Not Found`

---

## Notes

- All data is stored in memory (no database).
- Each event has a unique auto-incrementing ID.
- All responses use `jsonify()` and include proper HTTP status codes.
- Includes input validation for required `title` field.
- Uses helper logic to prevent modifying the list during iteration.

---

## Tests

Run all tests with:

```bash
pytest
```

You should see all 5 tests in `tests/test_app.py` passing:

- Create event
- Update event
- Update event (not found)
- Delete event
- Delete event (not found)

---

## Author

Built by Andrew Snyder as part of the Full CRUD Flask API module of Flatiron's Software Engineering Program.
