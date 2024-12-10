VERSION 0.8
FROM scratch

build:
    COPY --dir . ./dist
    SAVE ARTIFACT ./dist/ dist

deps:
    FROM python:3.12-slim-bullseye

    RUN pip install poetry
    RUN poetry config virtualenvs.create false

    ENV PYTHONUNBUFFERED=1

    COPY poetry.lock pyproject.toml /app/lib/python/norfair
    WORKDIR /app/lib/python/norfair

    RUN poetry install
    COPY --dir src/ .
