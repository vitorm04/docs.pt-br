---
title: "Referência csproj | Microsoft Docs"
description: "Saiba mais sobre as diferenças entre arquivos existentes e de csproj do .NET Core"
keywords: "referência, csproj, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 07/02/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
translationtype: Human Translation
ms.sourcegitcommit: 0402707f98af8b716b041ba1260162cd227918cc
ms.openlocfilehash: 98f6ced2a199bdbe2f91f46e48ffd3ac52438cf8

---

# <a name="additions-to-the-csproj-format-for-net-core"></a>Adições ao formato csproj para .NET Core

[!INCLUDE[preview-warning](../../../includes/warning.md)]

Este documento descreve as alterações adicionadas aos arquivos csproj como parte da mudança do `project.json` para `csproj` e [MSBuild](https://github.com/Microsoft/MSBuild). Para mais informações sobre a sintaxe e a referência do arquivo de projeto geral, consulte a documentação do [arquivo de projeto MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-project-file-schema-reference).  

## <a name="additions"></a>Adições

* Item PackageReference que especifica uma dependência NuGet no projeto. O atributo `Include` especifica a ID do pacote. 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

## <a name="version"></a>Versão
`Version` especifica a versão do pacote para restauração. O elemento respeita as regras do esquema de controle de versão do NuGet.

## <a name="includeassets"></a>IncludeAssets
O atributo `IncludeAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` devem ser consumidos. 

O atributo pode conter um ou mais dos seguintes valores:

* `Compile` – o conteúdo da pasta lib está disponível para compilação.
* `Runtime` – o conteúdo da pasta de tempo de execução é distribuído.
* `ContentFiles` – o conteúdo da pasta contentfiles é usado.
* `Build` – as propriedades/destinos na pasta build são usados.
* `Native` – o conteúdo de ativos nativos é copiado para a pasta de saída para o tempo de execução.
* `Analyzers` – os analisadores são usados.

Como alternativa, o atributo pode conter:

* `None` – nenhum dos ativos é usado.
* `All` – todos os ativos são usados.

## <a name="excludeassets"></a>ExcludeAssets
O atributo `ExcludeAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` não devem ser consumidos.

O atributo pode conter um ou mais dos seguintes valores:

* `Compile` – o conteúdo da pasta lib está disponível para compilação.
* `Runtime` – o conteúdo da pasta de tempo de execução é distribuído.
* `ContentFiles` – o conteúdo da pasta contentfiles é usado.
* `Build` – as propriedades/destinos na pasta build são usados.
* `Native` – o conteúdo de ativos nativos é copiado para a pasta de saída para o tempo de execução.
* `Analyzers` – os analisadores são usados.

Como alternativa, o elemento pode conter:

* `None` – nenhum dos ativos é usado.
* `All` – todos os ativos são usados.

## <a name="privateassets"></a>PrivateAssets
O atributo `PrivateAssets` especifica quais ativos que pertencem ao pacote especificado pelo `<PackageReference>` devem ser consumidos, mas que eles não devem fluir para o próximo projeto. 

> [!NOTE]
> Esse é um novo termo para o elemento `SuppressParent` project.json/xproj. 

O atributo pode conter um ou mais dos seguintes valores:

* `Compile` – o conteúdo da pasta lib está disponível para compilação.
* `Runtime` – o conteúdo da pasta de tempo de execução é distribuído.
* `ContentFiles` – o conteúdo da pasta contentfiles é usado.
* `Build` – as propriedades/destinos na pasta build são usados.
* `Native` – o conteúdo de ativos nativos é copiado para a pasta de saída para o tempo de execução.
* `Analyzers` – os analisadores são usados.

Como alternativa, o atributo pode conter:

* `None` – nenhum dos ativos é usado.
* `All` – todos os ativos são usados.

* DotnetCliToolReference O elemento do item `<DotnetCliToolReference>` especifica a ferramenta CLI que o usuário deseja restaurar no contexto do projeto. É uma substituição para o nó `tools` em `project.json`. 

```xml
<DotnetCliToolReference Include="<package-id>" Version="" />
```

## <a name="version"></a>Versão
`Version` especifica a versão do pacote para restauração. O atributo respeita as regras do esquema de controle de versão do NuGet.

* RuntimeIdentifiers O elemento `<RuntimeIdentifiers>` permite especificar uma lista delimitada por ponto e vírgula de [RIDs (Identificadores de Tempo de Execução)](../../rid-catalog.md) para o projeto. Os RIDs permitem publicar uma implantação autocontida. 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```


* RuntimeIdentifier O elemento `<RuntieIdentifier>` permite especificar somente um [Identificador de Tempo de Execução (RID)](../../rid-catalog.md) para o projeto. Os RIDs permitem publicar implantações autocontidas. 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```


* PackageTargetFallback O elemento `<PackageTargetFallback>` permite especificar um conjunto de destinos compatíveis a serem usados ao restaurar os pacotes. Ele foi criado para permitir que os pacotes que usam o dotnet TxM operem com pacotes que não declarem um dotnet TxM. Se seu projeto usa o dotnet TxM, todos os pacotes dos quais você depende também devem ter um dotnet TxM, a menos que você adicione o `<PackageTargetFallback>` ao seu projeto para permitir que plataformas que não sejam dotnet sejam compatíveis com dotnet. 

O exemplo a seguir fornece os fallbacks para todos os destinos em seu projeto: 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

O exemplo a seguir especifica os fallbacks apenas para o destino `netcoreapp1.0`:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a>Propriedades de metadados do NuGet
Com a mudança para o MSbuild, mudamos os metadados de entrada que são usados ao criar um pacote do NuGet do project.json para arquivos csproj. As entradas são propriedades do MSBuild. A seguir está a lista de propriedades que são usadas como entradas para o processo de empacotamento ao usar o comando `dotnet pack` ou o destino do MSBuild `Pack` que faz parte do SDK. 

* IsPackable
* PackageVersion
* PackageId
* Título
* Autores
* Descrição
* Copyright
* PackageRequireLicenseAcceptance
* PackageLicenseUrl
* PackageProjectUrl
* PackageIconUrl
* PackageReleaseNotes
* PackageTags
* PackageOutputPath
* IncludeSymbols
* IncludeSource
* PackageTypes
* IsTool
* RepositoryUrl
* RepositoryType
* NoPackageAnalysis
* MinClientVersion
* IncludeBuildOutput
* IncludeContentInPack
* BuildOutputTargetFolder
* ContentTargetFolders
* NuspecFile
* NuspecBasePath
* NuspecProperties


<!--HONumber=Feb17_HO2-->


