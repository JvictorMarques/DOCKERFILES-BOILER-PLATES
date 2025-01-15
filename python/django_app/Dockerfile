FROM python:3.12.3-alpine
LABEL owner="JvictorMarques"
RUN addgroup -S python && adduser -S python -G python

WORKDIR /app

COPY --chown=python:python . .
RUN pip install --no-cache-dir -r requirements.txt

USER python

EXPOSE 8000
CMD ["gunicorn", "django_app.wsgi:application", "--bind", "0.0.0.0:8000", "--workers", "3"]
