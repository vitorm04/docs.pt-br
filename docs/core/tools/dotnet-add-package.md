---
title: Comando de pacote dotnet-add | Microsoft Docs
description: "O comando de pacote dotnet-add fornece uma opção conveniente para adicionar uma referência de pacote NuGet a um projeto."
keywords: dotnet-add, CLI, comando da CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 88e0da69-a5ea-46cc-8b46-5493242b7af9
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 806f4383452cb250f302dc30ab2d59f7e4772026
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-add-package"></a>Pacote dotnet-add

## <a name="name"></a>Nome

`dotnet-add package` – adiciona uma referência de pacote a um arquivo de projeto.

## <a name="synopsis"></a>Sinopse

```
dotnet add [project] package <package_name> [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory]
dotnet add package [-h|--help]
```

## <a name="description"></a>Descrição

O `dotnet add package` fornece uma opção conveniente para adicionar uma referência de pacote a um arquivo de projeto. Depois de executar o comando, há uma verificação de compatibilidade para garantir que o pacote que está tentando ser adicionado é compatível com todas as estruturas do projeto. Se ele for aprovado na verificação, uma [restauração](dotnet-restore.md) será executada e o fragmento `<PackageReference>` será adicionado ao arquivo de projeto.

Por exemplo, a adição de `Newtonsoft.Json` a *ToDo.csproj* produz uma saída semelhante à seguinte:

```
Microsoft (R) Build Engine version 15.1.545.13942
Copyright (C) Microsoft Corporation. All rights reserved.

  Writing /var/folders/gj/1mgg_4jx7mbdqbhw1kgcpcjr0000gn/T/tmpm0kTMD.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'ToDo.csproj'.
log  : Restoring packages for ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 119ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/9.0.1/newtonsoft.json.9.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/9.0.1/newtonsoft.json.9.0.1.nupkg 27ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '9.0.1' added to file 'ToDo.csproj'.
```

O arquivo *ToDo.csproj* agora contém um fragmento [`<PackageReference>`](https://docs.microsoft.com/nuget/consume-packages/package-references-in-project-files) para o pacote referenciado.

```xml
<PackageReference Include="Newtonsoft.Json">
  <Version>9.0.1</Version>
</PackageReference>
```

## <a name="arguments"></a>Arguments

`project`

O arquivo de projeto no qual operar. Se não for especificado, o comando pesquisará um no diretório atual.

`package_name`

A referência de pacote a ser adicionada.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

`-v|--version <VERSION>`

Versão do pacote.

`-f|--framework <FRAMEWORK>`

Adiciona uma referência de pacote somente quando há uma estrutura específica como destino.

`-n|--no-restore`

Adiciona uma referência de pacote sem executar a visualização de restauração e a verificação de compatibilidade.

`-s|--source <SOURCE>`

Usa uma fonte de pacote NuGet específica a ser usada durante a operação de restauração.

`--package-directory <PACKAGE_DIRECTORY>`

Restaura o pacote no diretório especificado.

## <a name="examples"></a>Exemplos

Adicionar um pacote NuGet `Newtonsoft.Json` a um projeto:

`dotnet add package Newtonsoft.Json`

Adicionar uma versão específica de um pacote a um projeto:

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

Adicionar um pacote usando uma fonte específica do NuGet:

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`

