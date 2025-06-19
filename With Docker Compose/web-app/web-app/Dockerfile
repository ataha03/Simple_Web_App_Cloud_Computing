FROM python:3.9-slim
WORKDIR /app
COPY app.py /app
COPY . /app
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0
COPY requirements.txt /app/requirements.txt
RUN pip install -r requirements.txt
EXPOSE 5000
CMD ["python", "app.py"]