---
title: Organizando e testando projetos com a linha de comando do .NET Core | Microsoft Docs
description: Este tutorial explica como organizar e testar projetos do .NET Core por meio da linha de comando.
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 03/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 52ff1be3-d92e-4477-9c84-8c1771e87ab5
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 3f401907a59d5427cbcfaa0b785931a7ed82110f
ms.lasthandoff: 03/07/2017

---

# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>Organizando e testando projetos com a linha de comando do .NET Core

Este tutorial segue a [Introdução ao .NET Core no Windows/Linux/macOS usando a linha de comando](./using-with-xplat-cli.md) para mostrar como ir além dos simples cenários “olá, mundo” e preparar o caminho para aplicativos mais avançados e bem organizados.

## <a name="using-folders-to-organize-code"></a>Usar pastas para organizar o código

Digamos que você deseja apresentar alguns novos tipos para trabalhar. É possível fazer isso adicionando mais arquivos e verificando se eles receberam namespaces que podem ser incluídos no arquivo *Program.cs*.

```
/MyProject
|__Program.cs
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
```

Isso funciona muito bem quando o tamanho do projeto é relativamente pequeno. No entanto, se você tiver um aplicativo maior com vários tipos de dados diferentes e possivelmente várias camadas, será recomendável organizar as coisas de maneira lógica. É nesse momento que as pastas entram em cena. Você pode acompanhar [o projeto de exemplo NewTypes](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild) que este guia aborda ou criar seus próprios arquivos e pastas.

Para começar, crie uma nova pasta na raiz do seu projeto. `/Model` é escolhido aqui.

```
/NewTypes
|__/Model
|__Program.cs
|__NewTypes.csproj
```

Agora adicione alguns novos tipos à pasta:

```
/NewTypes
|__/Model
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__Program.cs
|__NewTypes.csproj
```

Agora, da mesma forma que faria com arquivos no mesmo diretório, conceda a todos eles o mesmo namespace para que você possa incluí-los no seu `Program.cs`.

### <a name="example-pet-types"></a>Exemplo: Tipos de animais de estimação

Esse exemplo cria dois novos tipos, `Dog` e `Cat`, e faz com que eles implementem uma interface comum, `IPet`.

Estrutura de Pastas:

```
/NewTypes
|__/Pets
   |__Dog.cs
   |__Cat.cs
   |__IPet.cs
|__Program.cs
|__NewTypes.csproj
```

`IPet.cs`:
```csharp
using System;

namespace Pets
{
    public interface IPet
    {
        string TalkToOwner();
    }
}
```

`Dog.cs`:
```csharp
using System;

namespace Pets
{
    public class Dog : IPet
    {
        public string TalkToOwner() => "Woof!";
    }
}
```

`Cat.cs`:
```csharp
using System;

namespace Pets
{
    public class Cat : IPet
    {
        public string TalkToOwner() => "Meow!";
    }
}
```

`Program.cs`:
```csharp
using System;
using Pets;
using System.Collections.Generic;

namespace ConsoleApplication
{
    public class Program
    {
        public static void Main(string[] args)
        {
            List<IPet> pets = new List<IPet>
            {
                new Dog(),
                new Cat()  
            };
            
            foreach (var pet in pets)
            {
                Console.WriteLine(pet.TalkToOwner());
            }
        }
    }
}
```

`NewTypes.csproj`:
```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />
  
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <Compile Include="**\*.cs" />
    <EmbeddedResource Include="**\*.resx" />
  </ItemGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.NETCore.App">
      <Version>1.0.1</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Sdk">
      <Version>1.0.0-alpha-20161104-2</Version>
      <PrivateAssets>All</PrivateAssets>
    </PackageReference>
  </ItemGroup>
  
  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```

E se você executar isso:

```
$ dotnet restore
$ dotnet run
Woof!
Meow!
```

É possível adicionar novos tipos de animais de estimação (como um `Bird`), estendendo esse projeto.

## <a name="testing-your-console-app"></a>Testando seu Aplicativo de Console

Você provavelmente vai querer testar seus projetos em algum momento. Aqui está uma boa maneira de fazer isso:

1. Mova o código-fonte do seu projeto existente para uma nova pasta `src`.

   ```
   /Project
   |__/src
   ```

2. Crie um diretório `/test` e `cd` dentro dele.

   ```
   /Project
   |__/src
   |__/test
   ```

3. Inicialize o diretório com um comando `dotnet new xunit`. Isso pressupõe o xUnit, mas você também pode usar o MSTest substituindo `xunit` por `mstest`.
   
### <a name="example-extending-the-newtypes-project"></a>Exemplo: Estendendo o projeto NewTypes

Agora que o sistema do projeto está em vigor, você pode criar seu projeto de teste e começar a escrever testes. A partir daqui, este guia usará e estenderá [o projeto Types de exemplo](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild). Além disso, ele usará a estrutura de teste do [Xunit](https://xunit.github.io/). Fique à vontade para acompanhá-lo ou criar seu próprio sistema multiprojeto com testes.

A estrutura de todo o projeto deve assemelhar-se a:

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

Há duas coisas que você precisa ter no seu projeto de teste:

1. Um arquivo *NewTypesTests.csproj* correto com o seguinte:

   * Uma referência a `xunit`
   * Uma referência a `dotnet-test-xunit`
   * Uma referência para o namespace correspondente ao código em teste

   Isso pode ser criado digitando `dotnet new xunit` em um prompt de comando no diretório *NewTypesTests* e adicionando uma referência de projeto ao projeto `NewTypes`.

    `NewTypesTests/NewTypesTests.csproj`:
    ```xml
    <Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />

      <PropertyGroup>
        <OutputType>Exe</OutputType>
        <TargetFramework>netcoreapp1.0</TargetFramework>
      </PropertyGroup>

      <ItemGroup>
        <Compile Include="**\*.cs" />
        <EmbeddedResource Include="**\*.resx" />
      </ItemGroup>

      <ItemGroup>
        <PackageReference Include="Microsoft.NETCore.App">
          <Version>1.0.1</Version>
        </PackageReference>
        <PackageReference Include="Microsoft.NET.Sdk">
          <Version>1.0.0-alpha-20161104-2</Version>
          <PrivateAssets>All</PrivateAssets>
        </PackageReference>
        <PackageReference Include="Microsoft.NET.Test.Sdk">
          <Version>15.0.0-preview-20161024-02</Version>
        </PackageReference>
        <PackageReference Include="xunit">
          <Version>2.2.0-beta3-build3402</Version>
        </PackageReference>
        <PackageReference Include="xunit.runner.visualstudio">
          <Version>2.2.0-beta4-build1188</Version>
        </PackageReference>
        <ProjectReference Include="../../src/NewTypes/NewTypes.csproj"/>
      </ItemGroup>

      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

2. Uma classe de teste xUnit.

    `PetTests.cs`: 
    ```csharp
    using System;
    using Xunit;
    using Pets;
    public class PetTests
    {
        [Fact]
        public void DogTalkToOwnerTest()
        {
            string expected = "Woof!";
            string actual = new Dog().TalkToOwner();
            
            Assert.Equal(expected, actual);
        }
        
        [Fact]
        public void CatTalkToOwnerTest()
        {
            string expected = "Meow!";
            string actual = new Cat().TalkToOwner();
            
            Assert.Equal(expected, actual);
        }
    }
    ```
   
Agora você pode executar testes. O comando [`dotnet test`](../tools/dotnet-test.md) executa o executor de teste que você especificou no seu projeto. Lembre-se de iniciar pelo diretório de nível superior.
 
```
$ cd test/NewTypesTests
$ dotnet restore
$ dotnet test
```
 
A saída deve ser semelhante a esta:
 
```
xUnit.net .NET CLI test runner (64-bit win10-x64)
  Discovering: NewTypesTests
  Discovered:  NewTypesTests
  Starting:    NewTypesTests
  Finished:    NewTypesTests
=== TEST EXECUTION SUMMARY ===
   NewTypesTests  Total: 2, Errors: 0, Failed: 0, Skipped: 0, Time: 0.144s
SUMMARY: Total: 1 targets, Passed: 1, Failed: 0.
```

