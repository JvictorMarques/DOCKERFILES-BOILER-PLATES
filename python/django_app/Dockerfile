FROM python:3.12.3-alpine
USER python
WORKDIR /app

COPY --chown=python:python requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY --chown=python:python . .

EXPOSE 8000

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]