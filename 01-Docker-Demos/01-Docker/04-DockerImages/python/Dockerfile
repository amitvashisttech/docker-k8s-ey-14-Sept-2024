# Base Run Time Env
FROM python:3.9-slim

# Set the Working Dir 
WORKDIR /app

# Copy the code for current dir
COPY . /app

# Install any required packages 
RUN pip install --no-cache-dir -r req.txt

# Listen to port : 5000
EXPOSE 5000

# Run app.py when the container launches
CMD ["python", "app.py"] 

