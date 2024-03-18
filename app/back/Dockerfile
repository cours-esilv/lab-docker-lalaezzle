# Use an official Python runtime as the parent image
FROM python:3.9

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file into the container at /app
COPY requirements.txt /app/

# Install any needed packages specified in requirements.txt
RUN pip install -r requirements.txt

# Copy the rest of the application's code into the container at /app
COPY . /app

EXPOSE 5000

# Define the command to run the app using Flask
CMD ["python3", "-m", "flask", "run", "--host=0.0.0.0"]