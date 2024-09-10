FROM python:3.12
LABEL description="A Python Flask Application connected to MongoDB."
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
ENV FLASK_APP=app.py
ENV FLASK_ENV=development
EXPOSE 5000
CMD ["python", "app.py"]

