# Use an official GCC image as the base image
FROM gcc:latest

# Set the working directory inside the container
WORKDIR /app

# Copy the source code into the container
COPY main.cpp .

# Compile the C++ code
RUN g++ -o myapp main.cpp

# Define the command to run when the container starts
CMD ["./myapp"]
