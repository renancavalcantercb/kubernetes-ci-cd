FROM python:3.9-slim

WORKDIR /app

# COPY requirements.txt /app/

# RUN pip install -r requirements.txt --no-cache-dir
RUN pip install flask --no-cache-dir

COPY . /app

CMD ["python", "app.py"]

