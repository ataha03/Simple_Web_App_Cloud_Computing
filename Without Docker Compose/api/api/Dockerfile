FROM python:3.9-slim
WORKDIR /app
COPY . /app
COPY requirements.txt /app/requirements.txt
RUN pip install -r requirements.txt
EXPOSE 8080
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8080"]