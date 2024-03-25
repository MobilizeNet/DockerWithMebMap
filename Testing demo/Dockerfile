# Use the official Microsoft ASP.NET image as a base image
FROM mcr.microsoft.com/dotnet/framework/aspnet:4.8

# Set the working directory inside the container
WORKDIR /inetpub/wwwroot

# Set the permission for the specific path
RUN cmd /c icacls C:/inetpub/wwwroot /grant:r Everyone:F /t

# Set the ASPNETCORE_URLS variable 
ENV ASPNETCORE_URLS=http://0.0.0.0:90

# Copy the application binaries files into the container
COPY app .

# Expose the port that the application will use
EXPOSE 90

# Set the entry point for the container
ENTRYPOINT ["TestingDemo.exe"]