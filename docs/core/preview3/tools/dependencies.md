---
title: "Gerenciamento de dependências das ferramentas da Visualização 3 do .NET Core"
description: "A Visualização 3 traz alterações no gerenciamento de dependências"
keywords: CLI, extensibilidade, comandos personalizados, .NET Core
author: blackdwarf
manager: wpickett
ms.date: 11/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 74b87cdb-a244-4c13-908c-539118bfeef9
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: e04d5f3b08c7f6885ed9914a91fc308234e6ce3b

---

<a name="managing-dependencies-in-net-core-preview-3-tooling"></a>Gerenciamento de dependências das ferramentas da Visualização 3 do .NET Core
----------------------------------------------------

# <a name="overview"></a>Visão Geral
Com a mudança dos projetos do .NET Core do project.json para o csproj e MSBuild, também ocorreu um investimento significativo que resultou na unificação do arquivo de projeto e dos ativos que permitem controlar dependências. Para projetos do .NET Core, isso é semelhante ao project.json. Não há nenhum arquivo JSON ou XML separado que rastreia dependências do NuGet. Com essa alteração, também apresentamos outro tipo de *referência* para a sintaxe csproj, chamada `<PackageReference>`. 

Este documento descreve o novo tipo de referência. Ele também mostra como adicionar uma dependência de pacote usando esse novo tipo de referência para o seu projeto. 

# <a name="the-new-packagereference-element"></a>O novo elemento <PackageReference>
O `<PackageReference>` tem a estrutura básica mostrada a seguir:

```xml
<PackageReference Include="<Package_ID>">
    <Version>PACKAGE_VERSION</Version>
</PackageReference>
```

Se você estiver familiarizado com o MSBuild, ele será parecido com outros [tipos de referência]() que já existem. A chave é a instrução do `Include`, que especifica a ID do pacote que você deseja adicionar ao projeto. O elemento filho `<Version>` especifica a versão obtida. As versões são especificadas por [Regras de versão do NuGet](https://docs.nuget.org/ndocs/create-packages/dependency-versions#version-ranges).  

> **Observação:** se você não estiver familiarizado com a sintaxe `csproj` geral, é possível usar a [documentação de referência de projeto MSBuild]() para se ambientar.  

Pode-se adicionar uma dependência disponível somente em um destino específico usando condições:

```xml
<PackageReference Include="<Package_ID>" Condition="'$(TargetFramework)' == 'netcoreapp1.0'">
    <Version>PACKAGE_VERSION</Version>
</PackageReference>
```

Isso significa que a dependência só será válida se o build estiver ocorrendo para esse destino específico. O `$(TargetFramework)` na condição é uma propriedade do MSBuild que está sendo definida no projeto. Para aplicativos .NET Core mais comuns, não será necessário fazer isso. 

# <a name="adding-a-dependency-to-your-project"></a>Adicionar uma dependência ao projeto
Adicionar uma dependência ao projeto é simples. Veja um exemplo de como adicionar a `JSON.net` versão `9.0.1` ao seu projeto. Obviamente, isso se aplica a qualquer outra dependência NuGet. 

Ao abrir o arquivo de projeto, você verá dois ou mais nós `<ItemGroup>`. Você perceberá que um dos nós já tem elementos `<PackageReference>` contidos nele. É possível adicionar a nova dependência a esse nó ou criar uma nova; isso cabe a você, pois o resultado será o mesmo. 

Neste exemplo, usaremos o modelo padrão removido pelo `dotnet new`. Este é um aplicativo de console simples. Ao abrir o projeto, localizamos o `<ItemGroup>` com `<PackageReference>` já existentes nele. Em seguida, adicionamos o seguinte:

```xml
<PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1</Version>
</PackageReference>
```
Depois disso, salve o projeto e execute o comando de `dotnet restore` para instalar a dependência. 

O projeto completo tem esta aparência:

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
    <PackageReference Include="Newtonsoft.Json">
        <Version>9.0.1</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Sdk">
      <Version>1.0.0-alpha-20161104-2</Version>
      <PrivateAssets>All</PrivateAssets>
    </PackageReference>
  </ItemGroup>
  
  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```

# <a name="removing-a-dependency-from-the-project"></a>Remover uma dependência do projeto
Para remover uma dependência do arquivo de projeto, simplesmente remova `<PackageReference>` do arquivo de projeto. 





<!--HONumber=Nov16_HO3-->


