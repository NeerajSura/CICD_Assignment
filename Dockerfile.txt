# Use a base image with necessary dependencies for training
FROM python:3.10

# Copy the requirements file
COPY requirements.txt .

# Install requirements
RUN pip install --no-cache-dir -r requirements.txt

# Copy the entire current directory into the container
COPY . .

# Run the training script during build phase
RUN python train.py

# Define the command to run the container
CMD ["python", "test.py"]
