Hello-World
 <Window x:Class="OpenWindow.MainWindow"
         xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
         xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
         xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
         xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
         xmlns:local="clr-namespace:OpenWindow"
         mc:Ignorable="d"
         Title="MainWindow" Height="450" Width="800">
      <Grib>
          <Button
               Content="OpenWindow"
               HorizontalAlignment="Center"
               VerticalAlignment="Center"
               Width="90"
               Click="Button_Click"/>
       </Grib>
   </Window>
   
.md

  FROM goland
  
  ENV GO111MODULE=on
  
  WORKDIR /app
  
  COPY go.mod .
  COPY go.sum .
  
  RUN go mod download
  
  COPY . .
  
  RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build
  
  EXPOSE 8080
  ENTRYPOINT ["/app/tttpserver"]

 i686-linux    kube-router
 x86_64-linux  kube-router
 aarch64-linux kube-router
 
jekyll

 
 
   "script": {
   "test": "echo \"Error: no test specified\" && exit 1",
   "start": "node server.js",
   "server": "nodemon server.js"
   },
# Authentication

There are three ways to authenticate through GitHub API v3.Reguests that reguire authentication will
return 404 Not Found instead of 403 Forbidden in some places.This is to prevent the accidental
leakage of private repositories to unauthorized users.

