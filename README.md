# floww-api-ver1

> **Credit:** Originally published at [prakharpks02/floww-api-ver1](https://github.com/prakharpks02/floww-api-ver1).

A dummy Django REST Framework project for creating, testing and documenting Floww delivery/order APIs. The `app1` app defines two class-based API views, `EditOrderInstructions` (POST `orderId` + `instruction`) and `GetOrderDetails` (GET `?orderId=`), which currently return placeholder order data. Every call is recorded in two logging models, `ErrorLogApi` and `UsageLogApi`.

## Status

This is a prototype. The views are not wired into `main_project/urls.py` (only `admin/` is routed), `app1` is not listed in `INSTALLED_APPS`, and `models.py` references a `CHAR_SIZE_MEDIUM` constant that is not defined. You need to fix all three before the API endpoints can be used.

## API views (in `main_project/app1/views.py`)

| View | Method | Input | Returns |
|---|---|---|---|
| `EditOrderInstructions` | POST | `orderId`, `instruction` | `{"status": "success"}` (201) |
| `GetOrderDetails` | GET | `orderId` query param | Order pickup/drop details, weight, status, instructions, task ID |

## Tech stack

Python, Django, Django REST Framework, SQLite (default). `requirements.txt` also pins other libraries (Firebase, Google APIs, pandas, SendGrid, Twilio and more) that the current code does not use.

## Running locally

```bash
cd main_project
pip install django djangorestframework
export DJANGO_SECRET_KEY="your-secret-key"
# optional: export DJANGO_DEBUG=1
python manage.py migrate
python manage.py runserver
```
