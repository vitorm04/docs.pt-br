---
title: Gerenciar dependências no .NET Core
description: Explica como gerenciar as dependências do projeto para um aplicativo .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399143"
---
# <a name="manage-dependencies-in-net-core-applications"></a>Gerenciar dependências em aplicativos .NET Core

Este artigo explica como adicionar e remover dependências editando o arquivo do projeto ou usando o CLI.

## <a name="the-packagereference-element"></a>O \<elemento PackageReference>

O `<PackageReference>` elemento de arquivo do projeto tem a seguinte estrutura:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

O `Include` atributo especifica o ID do pacote para adicionar ao projeto. O `Version` atributo especifica a versão a ser get. As versões são especificadas de acordo com [as regras da versão NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Se você não estiver familiarizado com a sintaxe de arquivo de projeto, consulte a documentação de referência do [projeto MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) para obter mais informações.

Use condições para adicionar uma dependência disponível apenas em um alvo específico, como mostrado no exemplo a seguir:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

A dependência no exemplo anterior só será válida se a compilação estiver acontecendo para esse determinado alvo. A `$(TargetFramework)` condição é uma propriedade MSBuild que está sendo definida no projeto. Para a maioria dos aplicativos .NET Core mais comuns, você não precisa fazer isso.

## <a name="add-a-dependency-by-editing-the-project-file"></a>Adicione uma dependência editando o arquivo do projeto

Para adicionar uma dependência, `<PackageReference>` adicione `<ItemGroup>` um elemento dentro de um elemento. Você pode adicionar a `<ItemGroup>` um existente ou criar um novo. O exemplo a seguir usa o projeto de `dotnet new console`aplicativo de console padrão criado por :

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="3.1.2" />
  </ItemGroup>

</Project>
```

## <a name="add-a-dependency-by-using-the-cli"></a>Adicione uma dependência usando o CLI

Para adicionar uma dependência, [dotnet add package](dotnet-add-package.md) execute o comando, como mostrado no exemplo a seguir:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>Remova uma dependência editando o arquivo do projeto

Para remover uma dependência, `<PackageReference>` remova seu elemento do arquivo do projeto.

## <a name="remove-a-dependency-by-using-the-cli"></a>Remova uma dependência usando o CLI

Para remover uma dependência, [dotnet remove package](dotnet-remove-package.md) execute o comando, conforme mostrado no exemplo a seguir:

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>Confira também

* [Pacotes NuGet em arquivos de projeto](../project-sdk/msbuild-props.md#nuget-packages)
* [dotnet list packageComando](dotnet-remove-package.md)
