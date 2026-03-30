from Flask import flask
app = Flask(__name__)
@app.route(' / ')
def hello():
    return "Hello from CI/CD automated container!"
if __name__ == "__main__":
    app.run(host="0.0.0.0",port-8080)


FROM python:3.10-slim
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["python3","app.py"]

flask

PORT=8080
echo "Building Docker image..."
docker build -t myapp:latest .
echo "Stopping old containers . . ."
docker stop myapp || true
docker rm myapp || true
echo "Running a new container on port $PORT..."
docker run -d --name myapp -p $PORT:8080 myapp:latest
echo "App deployed"
echo "Use killercoda traffic tab port $PORT"
