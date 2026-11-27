# Django Event Planner API

**A REST API for planning events, built in Django and Django REST Framework. The same CRUD feature is implemented four ways (function views, class-based views, mixins and generics) plus a ViewSet, to compare the styles side by side.**

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-3.2-092E20?logo=django&logoColor=white)
![DRF](https://img.shields.io/badge/DRF-3.15-A30000)
![SQLite](https://img.shields.io/badge/SQLite-003B57?logo=sqlite&logoColor=white)

## What it does

Create, list, read, update and delete events. Each event has a UUID, a name, a description, a location, start and end dates, and automatic created and updated timestamps. The project also keeps the Home and About pages from the first assignment.

## API styles in this project

| Style | Base path |
| --- | --- |
| Function-based views | `/events/`, `/events/create/`, `/events/<id>/`, `/events/<id>/update/`, `/events/<id>/delete/` |
| Class-based views | `/events/cbv/`, `/events/cbv/<id>/` |
| DRF mixins | `/events/mixins/` |
| DRF generics | `/events/generics/`, `/events/generics/<id>/` |
| ViewSet + router | `/events/viewset/` |
| Pages | `/events/home/`, `/events/about/` |

## Data model

`Event`: `id` (UUID), `name`, `description`, `location`, `start_date`, `end_date`, `created_at`, `updated_at`. The model replaced the first assignment's version: auto-increment id became a UUID, `title` became `name`, and `date` was split into start and end.

## Run it

```bash
git clone https://github.com/ahmedbadawix77x-gif/Django-Event-Planner.git
cd Django-Event-Planner
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

Open http://127.0.0.1:8000/events/.

Example request:

```bash
curl -X POST http://127.0.0.1:8000/events/create/ \
  -H "Content-Type: application/json" \
  -d '{"name":"Magic Party","description":"Fun times","location":"Hogwarts","start_date":"2025-01-01T10:00:00Z","end_date":"2025-01-01T12:00:00Z"}'
```

## Tests

```bash
python manage.py test events
```

This runs a full create, list, read, update, delete cycle against a test database. `test_api.py` is a separate manual smoke script that calls a running server with `requests`.

## Note

`DEBUG` is on and the secret key is a development key. Change both before any real deployment.

## Author

**Ahmed Badawy**. GitHub: [@ahmedbadawix77x-gif](https://github.com/ahmedbadawix77x-gif) · Portfolio: [ahmed-badawy-portfolio.vercel.app](https://ahmed-badawy-portfolio.vercel.app)
