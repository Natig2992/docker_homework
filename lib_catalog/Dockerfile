FROM python:3.9-buster
WORKDIR /app

EXPOSE 8000
COPY . .

#COPY requirements.txt /app
RUN useradd natig  && chown -R natig /app && pip install -r requirements.txt
#RUN pip install -r requirements.txt

#USER natig

ENTRYPOINT [ "/bin/sh", "-c", "./entry_python.sh"]




