FROM redhat/ubi8  
LABEL name="ashutoshh"
LABEL email="ashutoshh@linux.com"
# label is optional but to share image owner details to users 
RUN dnf install dotnet-sdk-8.0 -y  
RUN mkdir /ashuapp 
COPY sample-dotnetweb-app /ashuapp/
WORKDIR /ashuapp
RUN dotnet build -o ashubin 
RUN dotnet publish -o ashu_publish -p:AssemblyName=ashudotnet
# while publish i can change the name of app
CMD ./ashu_publish/ashudotnet --urls=http://0.0.0.0:5000
# must be the final keyword of dockerfile which will run your app
