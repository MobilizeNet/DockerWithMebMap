
## Welcome to the Wild World of Windows Containers with .NET Framework 4.8 WebMap app!

So, you've decided to dive into the exciting realm of Windows containers with a classic .NET Framework 4.8 app? Buckle up, because you're in for a wild ride! But fear not, brave adventurer, for this README shall be your trusty guide through the murky waters of containerization. 

### Pre-requisites:

* Windows 10 Pro or Enterprise (64-bit) or Windows Server 2019 (or later)
* Docker Desktop for Windows (Because, let's face it, containers are the cool kids' playground)
* A mug of your favorite beverage (trust us, you'll need it)

### Instructions:

    1. Prepare the WebMap app:
    First things first, make sure your .NET Framework 4.8 app is all set and ready to go. Give it a pep talk if necessary; containers can be intimidating.

    2. Dockerfile Magic:
    Time to work your magic with Dockerfile! Open your favorite text editor (Notepad++ for the win!) and let the incantations begin: 
```docker file
# Use the official Microsoft ASP.NET image as a base image
FROM mcr.microsoft.com/dotnet/framework/aspnet:4.8

# Set the working directory inside the container
WORKDIR /inetpub/wwwroot

# Set the permission for the specific path
RUN cmd /c icacls C:/inetpub/wwwroot /grant:r Everyone:F /t

# Set the ASPNETCORE_URLS variable 
ENV ASPNETCORE_URLS=http://0.0.0.0:90

# Copy the application binaries files into the container
COPY deploy .

# Expose the port that the application will use
EXPOSE 90

# Set the entry point for the container
ENTRYPOINT ["WebMapApp.exe"]

```

    3.Build Your Container:
    Time to summon your container into existence! Open PowerShell in the directory containing your Dockerfile and execute the following dark ritual (remember to switch Windows Containers):

``` Powershell
docker build -t your-image-name .
```
    4.Run Your Container:
    Now comes the moment of truth! Launch your container into the void with this arcane command:

``` Powershell
docker run -d -p <ANY_PORT>:90 --name your-container-name your-image-name
```

    5.Test the containerized application: 
    Visit http://localhost:<ANY_PORT> in your web browser to test your .NET Framework application running inside the Docker container. 

### Troubleshooting:
If things go awry (as they often do in the realm of containers), take a deep breath and remember: Google is your best friend. And if Google fails you, Stack Overflow is your knight in shining armor.

### Final Words:
Congratulations, brave soul! You have successfully embarked on a perilous journey through the labyrinth of Windows containers with a .NET Framework 4.8 app. May your containers be ever resilient, your apps forever functional, and your sense of humor never waver in the face of technological adversity.

Happy containerizing! 🐳🚀 