# Using official Python runtime base image
FROM python:2.7-alpine


# Set the application directory
WORKDIR /app


# Install the application requirements
ADD requirements.txt /app/requirements.txt
RUN pip install -r requirements.txt


# Copy the application code into the container
ADD . /app


# Expose port 80 for access
EXPOSE 80


# Define the command to run when the container starts
CMD ["gunicorn", "app:app", "-b", "0.0.0.0:80", "--log-file", "-", "--access-logfile", "-", "--workers", "4", "--keep-alive", "0"]