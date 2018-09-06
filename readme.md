# nuget server

1. 新建空白專案
1. nuget 安裝套件 nuget.server
1. 建置後修改 web.config 設定

```xml
    <add key="apiKey" value="key" />
    <add key="packagesPath" value="~/Packages" />
```

1. 佈署發行資料夾須注意 web.config 的區段，是否有重複的 `compilation`

```xml
  <system.web>
    <compilation targetFramework="4.6.2" />
    <!-- maxRequestLength is specified in Kb -->
    <httpRuntime targetFramework="4.6.2" maxRequestLength="30720" />
  </system.web>
```

1. 發行完畢後直接佈署於 IIS 站台

# nuget package

## Create Spec File

```
nuget spec
```

## Build Project

Ctrl + Shift + B

## Package file

```
nuget pack ArtJsonParser.csproj
```

## Upload package

nuget.exe push {package file} {apikey} -Source http://172.21.19.62/nuget
