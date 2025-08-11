Docker Compose Setup for Django Todolist App with MySQL
📌 Project Overview
This project sets up a Django-based Todo-List application with a MySQL database using Docker Compose.
The configuration ensures data persistence through named volumes and automatically executes necessary setup commands when containers start.

🛠 Tech Stack
    - Docker & Docker Compose

    - MySQL

    - Python / Django

    - Shell (entrypoint scripts)

🚀 What Was Done
    1. Created a docker-compose.yml file to define and run two services:

        - mysql

        - pythonapp (Django application)

    2. Used a custom Dockerfile.mysql to build the MySQL image and expose port 3306.

    3. Attached a named volume (db-data) to persist MySQL data in /var/lib/mysql.

    4. Removed:

        - RUN python manage.py migrate
    from the Django Dockerfile to avoid running migrations during build time.

    5. Refactored the ENTRYPOINT of the Django container to:

        - Wait for the MySQL database to become available.

        - Run migrations after the database is ready.

    6. Configured depends_on with healthcheck in docker-compose.yml to ensure the Django service starts only after MySQL is healthy.

    7. Created INSTRUCTION.md with detailed steps on how to:

        - Run the setup with Docker Compose.

        - Stop and clean up containers and volumes.

    8. Ensured that todos are stored in MySQL and persist between restarts thanks to the named volume.

