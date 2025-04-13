# Step 1: Build stage
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build

# Set working directory inside the container
WORKDIR /code

# Copy the project folder into the container
ADD Worker /code/src/Worker

# Set working directory to where the .csproj is
WORKDIR /code/src/Worker

# Restore dependencies and publish the app to /app
RUN dotnet restore -v minimal \
    && dotnet publish -c Release -o /app

# Step 2: Runtime stage
FROM mcr.microsoft.com/dotnet/runtime:7.0

# Set working directory inside the runtime container
WORKDIR /app

# Copy the published app from the build stage
COPY --from=build /app .

# Start the application
CMD ["dotnet", "Worker.dll"]
