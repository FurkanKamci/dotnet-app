------
1 - Dotnet Web App projesi oluşturma :

>Not : Benim sunucumda dotnet core 6.0 yüklü olduğu için otomatik olarak projeyi 6.0 ile oluşturacaktır.
```
dotnet new webapp -o dotnet-app → Bulunduğumuz klasörde dotnet-app isminde bir web app projesi oluşturur.
dotnet new sln → Yeni bir solution oluşturur.
dotnet sln add dotnet-app → dotnet-app projesini oluşturduğu solution’a dahil eder.
```
------
2 - Projeyi Manuel veya Docker ile çalıştırma : 

Manuel Çalıştırma : 
```
dotnet restore --use-current-runtime
dotnet publish -c Release --no-restore
dotnet run
dotnet clean
```
Docker ile Çalıştırma : 
```
docker build -t dotnet-app .
docker run -it --rm -p 5000:80 -t dotnet-app dotnet-app
http://localhost:5000
```
------

>Not : dotnet clean komutu bin ve obj de oluşan klasörleri ve dosyaları silmez. Bu klasörleri de silmek istersek aşağıdaki komutları .csproj dosyamızda Project ‘in içerisine eklememiz gerekiyor. Eklendikten sonra projemizi publish etmeden önce restore etmemiz gerekiyor.

```
  <Target Name="SpicNSpan"  AfterTargets="Clean">
      <!-- Remove obj folder -->
      <RemoveDir Directories="$(BaseIntermediateOutputPath)" />  
      <!-- Remove bin folder -->   
      <RemoveDir Directories="$(BaseOutputPath)" />  
  </Target>
 ```
------
