# rid-test
Test for managed runtime target libraries.

## Prepare

```
dotnet build -Restore src\A\A.msbuildproj
nuget pack -Properties "Version=1.0.0.0;Configuration=(Debug|Release);BaseDir=..\artifacts\bin" .nuget\A.nuspec
nuget push -source %NugetHome%\packages A.1.0.0.0.nupkg
```

## Consume
```
dotnet build -Restore -p:UseAppHost=False ConsoleApp1\ConsoleApp1.csproj
```
Depending on where you run this dotnet application it will output
> Hello, World!  
> Windows

on Windows, and
> Hello, World!  
> Linux

on Linux systems.