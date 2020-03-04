---
title: Gerenciar dependências no .NET Core
description: Explica como gerenciar dependências de projeto para um aplicativo .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157239"
---
# <a name="manage-dependencies-in-net-core-applications"></a>Gerenciar dependências em aplicativos .NET Core

Este artigo explica como adicionar e remover dependências editando o arquivo de projeto ou usando a CLI.

## <a name="the-packagereference-element"></a>O elemento \<PackageReference >

O elemento de arquivo de projeto `<PackageReference>` tem a seguinte estrutura:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

O atributo `Include` especifica a ID do pacote a ser adicionado ao projeto. O atributo `Version` especifica a versão a ser obtida. As versões são especificadas de acordo com [as regras de versão do NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Se você não estiver familiarizado com a sintaxe Project-File, consulte a documentação de [referência do projeto MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) para obter mais informações.

Use condições para adicionar uma dependência que está disponível somente em um destino específico, conforme mostrado no exemplo a seguir:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

A dependência no exemplo anterior só será válida se a compilação estiver acontecendo para o destino fornecido. O `$(TargetFramework)` na condição é uma propriedade do MSBuild que está sendo definida no projeto. Para aplicativos .NET Core mais comuns, você não precisa fazer isso.

## <a name="add-a-dependency-by-editing-the-project-file"></a>Adicionar uma dependência editando o arquivo de projeto

Para adicionar uma dependência, adicione um elemento `<PackageReference>` dentro de um elemento `<ItemGroup>`. Você pode adicionar a um `<ItemGroup>` existente ou criar um novo. O exemplo a seguir usa o projeto de aplicativo de console padrão criado por `dotnet new console`:

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

## <a name="add-a-dependency-by-using-the-cli"></a>Adicionar uma dependência usando a CLI

Para adicionar uma dependência, execute o comando [dotnet add package](dotnet-add-package.md) , conforme mostrado no exemplo a seguir:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>Remover uma dependência editando o arquivo de projeto

Para remover uma dependência, remova seu elemento `<PackageReference>` do arquivo de projeto.

## <a name="remove-a-dependency-by-using-the-cli"></a>Remover uma dependência usando a CLI

Para remover uma dependência, execute o comando [dotnet remove package](dotnet-remove-package.md) , conforme mostrado no exemplo a seguir:

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>Confira também

* [Pacotes NuGet em arquivos de projeto](../project-sdk/msbuild-props.md#nuget-packages)
* [dotnet list package comando](dotnet-remove-package.md)
