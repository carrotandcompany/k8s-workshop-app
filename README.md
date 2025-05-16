# K8s Workshop Demo App

This repository contains two minimal Flask + SPA demo apps for Kubernetes workshops.

# What are these apps doing?

The apps are designed to be used in a Kubernetes workshop. They are simple Flask applications that serve a minimal Single Page Application (SPA) and query every second the backend to provide some stats to make some kubernetes features easier comprehensible.

## Structure

- `version1/`: Minimal SPA + Flask backend (no database)
- `version2/`: SPA + Flask backend + PostgreSQL (records requests, returns stats)

## Prerequisites
- Python 3.8+
- [uv](https://github.com/astral-sh/uv) (for dependency management)
- (For version2) PostgreSQL instance (local or remote)

## Setup

The easiest way is to start the devcontainer eg. with VSCode.

## Running the Apps

NOTE: These apps are designed for demonstration purposes and are not production-ready!

Starting version 1 to be servied at 0.0.0.0:3000 run the following command:

```bash
uv run version1/app.py 
```

Version 2 needs a PostgreSQL instance. One is started as part of the devcontainer. Credentials can be set via environment variables. The default values for the postgresdb instance and the app.py are:
```bash
POSTGRES_HOST=db
POSTGRES_PORT=5432
POSTGRES_DB=demo
POSTGRES_USER=demo
POSTGRES_PASSWORD=demo
```

```bash
uv run version2/app.py 
```


## Hot-Reloading

To have the apps reloaded automatically when you change the code, you can start the apps with `--debug` flag.

```
uv run version1/app.py --debug
```

## Notes
- The frontend is a minimal HTML/JS SPA in `static/index.html`.
- Version 2 will create the required table automatically if it does not exist.
- App version is printed on startup.
- Graceful shutdown is handled in version 2.

For questions, regarding the workshop, please reach out to hello@cnc.io