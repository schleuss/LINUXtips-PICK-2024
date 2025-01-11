# Build stage
FROM cgr.dev/chainguard/python:latest-dev AS build

ADD requirements.txt .

RUN pip install --no-cache-dir --user -r requirements.txt


# Final stage
FROM cgr.dev/chainguard/python:latest

WORKDIR /app

# copy python libs
COPY --from=build /home/nonroot/.local/ /home/nonroot/.local

# copy app files
ADD static/ static/
ADD templates/ templates/
ADD tailwind.config.js .
ADD app.py .

EXPOSE 5000

ENTRYPOINT [ "/home/nonroot/.local/bin/flask", \
             "run", \
             "--host", \
             "0.0.0.0" ]
