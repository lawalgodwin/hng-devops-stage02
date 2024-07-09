# # Use the latest official Python image as a base
# FROM python:latest

# # Set the working directory
# WORKDIR /usr/src/app

# # Copy the application dependency files
# COPY pyproject.toml poetry.lock ./

# # Install Poetry
# RUN apt-get update && apt-get install -y curl && \
#     curl -sSL https://install.python-poetry.org | python3 - && \
#     ln -s /root/.local/bin/poetry /usr/local/bin/poetry

# # Install dependencies using Poetry
# RUN poetry install --no-root

# # Copy the application files
# COPY . .

# RUN poetry run bash ./prestart.sh

# # Run the application
# # CMD ["poetry", "run", "uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]


# Use the latest official Python image as a base
FROM python:latest

# Install Poetry using pip
RUN pip install poetry uvicorn

# Set the working directory
WORKDIR /app

# Copy the application files
COPY . .

# Install dependencies using Poetry
RUN poetry install

# RUN poetry run bash ./prestart.sh

# Run the prestart script and start the server
CMD ["sh", "-c", "poetry run bash ./prestart.sh && poetry run uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload"]