# For more information, please refer to https://aka.ms/vscode-docker-python
FROM python:3.9.11

# Install pip requirements
COPY requirements.txt .
RUN python -m pip install -r requirements.txt

WORKDIR /app
COPY . /app

# Creates a non-root user with an explicit UID and adds permission to access the /app folder and NLTK data directory
RUN adduser -u 5678 --disabled-password --gecos "" appuser && chown -R appuser /app 
USER appuser

# During debugging, this entry point will be overridden. For more information, please refer to https://aka.ms/vscode-docker-python-debug
CMD ["streamlit", "run", "segmentation.py","--server.port","8080","--server.headless","true"]
