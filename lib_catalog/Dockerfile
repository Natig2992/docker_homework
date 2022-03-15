FROM python:3.9-buster
WORKDIR /app

EXPOSE 8000
COPY . .

RUN useradd natig  && chown -R natig /app && pip install -r requirements.txt

USER natig

ENTRYPOINT [ "/bin/sh", "-c", "./entry_python.sh"]

HEALTHCHECK --interval=30s --timeout=10s --retries=3 CMD curl -sS http://localhost:8000/admin/ || exit 1



