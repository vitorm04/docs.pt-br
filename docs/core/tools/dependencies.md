---
title: "Gerenciamento de dependências das ferramentas do .NET Core | Microsoft Docs"
description: "Explica como gerenciar suas dependências com as ferramentas do .NET Core."
keywords: CLI, extensibilidade, comandos personalizados, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 74b87cdb-a244-4c13-908c-539118bfeef9
ms.translationtype: Human Translation
ms.sourcegitcommit: 25847dd6921e547074f4501d34d865dfb1b98b59
ms.openlocfilehash: de496d96120df1ec275bb4a69f01b6266b0b5a89
ms.contentlocale: pt-br
ms.lasthandoff: 05/17/2017

---

# <a name="managing-dependencies-with-net-core-sdk-10"></a>Gerenciando dependências com o SDK 1.0 do .NET Core

Com a mudança dos projetos do .NET Core de project.json para csproj e o MSBuild, também ocorreu um investimento significativo que resultou na unificação do arquivo de projeto e dos ativos que permitem o acompanhamento de dependências. Para projetos do .NET Core, isso é semelhante ao project.json. Não há nenhum arquivo JSON ou XML separado que rastreia dependências do NuGet. Com essa alteração, também apresentamos outro tipo de *referência* para a sintaxe csproj, chamada `<PackageReference>`. 

Este documento descreve o novo tipo de referência. Ele também mostra como adicionar uma dependência de pacote usando esse novo tipo de referência para o seu projeto. 

## <a name="the-new-packagereference-element"></a>O novo elemento \<PackageReference>
O `<PackageReference>` tem a estrutura básica mostrada a seguir:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Se você estiver familiarizado com o MSBuild, ele será parecido com outros tipos de referência que já existem. A chave é a instrução do `Include`, que especifica a ID do pacote que você deseja adicionar ao projeto. O elemento filho `<Version>` especifica a versão obtida. As versões são especificadas por [Regras de versão do NuGet](https://docs.microsoft.com/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Se você não está familiarizado com a sintaxe `csproj` geral, é possível usar a documentação de [referência de projeto MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-project-file-schema-reference) para mais informações.  

Pode-se adicionar uma dependência disponível somente em um destino específico usando condições como no exemplo a seguir:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp1.0'" />
```

Isso significa que a dependência só será válida se o build estiver ocorrendo para esse destino específico. O `$(TargetFramework)` na condição é uma propriedade do MSBuild que está sendo definida no projeto. Para aplicativos .NET Core mais comuns, não será necessário fazer isso. 

## <a name="adding-a-dependency-to-your-project"></a>Adicionar uma dependência ao projeto
Adicionar uma dependência ao projeto é simples. Veja um exemplo de como adicionar a versão `9.0.1` do Json.NET ao seu projeto. Obviamente, isso se aplica a qualquer outra dependência NuGet. 

Ao abrir o arquivo de projeto, você verá dois ou mais nós `<ItemGroup>`. Você perceberá que um dos nós já tem elementos `<PackageReference>` contidos nele. É possível adicionar a nova dependência a esse nó ou criar uma nova; isso cabe a você, pois o resultado será o mesmo. 

Neste exemplo, usaremos o modelo padrão removido pelo `dotnet new console`. Este é um aplicativo de console simples. Ao abrir o projeto, localizamos o `<ItemGroup>` com `<PackageReference>` já existentes nele. Em seguida, adicionamos o seguinte:

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
Depois disso, salve o projeto e execute o comando de `dotnet restore` para instalar a dependência. 

O projeto completo tem esta aparência:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="removing-a-dependency-from-the-project"></a>Remover uma dependência do projeto
Para remover uma dependência do arquivo de projeto, simplesmente remova `<PackageReference>` do arquivo de projeto.

