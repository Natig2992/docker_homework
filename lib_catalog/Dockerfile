FROM python:3.9
WORKDIR /app

EXPOSE 8000
COPY . .

#COPY requirements.txt /app

RUN pip install -r requirements.txt

ENTRYPOINT [ "/bin/sh", "-c", "./entry_python.sh"]




