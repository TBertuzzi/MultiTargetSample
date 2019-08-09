# MultiTargetSample

Exemplo de como criar um projeto MultiTarget.

Edite o .csproj para verificar a "Magica".

Com os Target projects é possivel definir quais plataformas seu projeto sera utilizado :

```csharp

<TargetFrameworks></TargetFrameworks>
<TargetFrameworks Condition=" '$(OS)' == 'Windows_NT' ">netstandard1.0;netstandard2.0;Xamarin.iOS10;MonoAndroid80;uap10.0.16299</TargetFrameworks>
<TargetFrameworks Condition=" '$(OS)' != 'Windows_NT' ">netstandard1.0;netstandard2.0;Xamarin.iOS10;MonoAndroid80</TargetFrameworks>

````

Utilize os ItemGroup com a Condition para definir qual projeto ira receber quais classes.

```csharp

<ItemGroup Condition=" $(TargetFramework.StartsWith('MonoAndroid')) ">
    <Compile Include="**\*.android.cs" />
  </ItemGroup>

  <ItemGroup Condition=" $(TargetFramework.StartsWith('Xamarin.iOS')) ">
    <Compile Include="**\*.apple.cs" />
  </ItemGroup>

````
  
  
