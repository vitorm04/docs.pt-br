---
title: Comando dotnet-add package - CLI do .NET Core | Microsoft Docs
description: "O comando de pacote dotnet-add fornece uma opção conveniente para adicionar uma referência de pacote NuGet a um projeto."
keywords: dotnet-add, CLI, comando da CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 88e0da69-a5ea-46cc-8b46-5493242b7af9
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 41b46e879056d385ceb3abaec27db974cab812e3
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-add-package"></a>Pacote dotnet-add

## <a name="name"></a>Nome

`dotnet-add package` – adiciona uma referência de pacote a um arquivo de projeto.

## <a name="synopsis"></a>Sinopse

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory] [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet add package` fornece uma opção conveniente para adicionar uma referência de pacote a um arquivo de projeto. Depois de executar o comando, há uma verificação de compatibilidade para garantir que o pacote seja compatível com as estruturas do projeto. Se for aprovado na verificação, um elemento `<PackageReference>` será adicionado ao arquivo de projeto e [dotnet restore](dotnet-restore.md) será executada.

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

O arquivo *ToDo.csproj* agora contém um elemento [`<PackageReference>`](https://docs.microsoft.com/nuget/consume-packages/package-references-in-project-files) para o pacote referenciado.

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a>Arguments

`PROJECT`

Especifica o arquivo do projeto. Se não for especificado, o comando pesquisará um no diretório atual.

`PACKAGE_NAME`

A referência de pacote a ser adicionada.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

`-v|--version <VERSION>`

Versão do pacote.

`-f|--framework <FRAMEWORK>`

Adiciona uma referência de pacote somente quando há uma [estrutura](../../standard/frameworks.md) específica como destino.

`-n|--no-restore`

Adiciona uma referência de pacote sem executar a visualização de restauração e a verificação de compatibilidade.

`-s|--source <SOURCE>`

Usa uma fonte de pacote NuGet específica durante a operação de restauração.

`--package-directory <PACKAGE_DIRECTORY>`

Restaura o pacote no diretório especificado.

## <a name="examples"></a>Exemplos

Adicionar um pacote NuGet `Newtonsoft.Json` a um projeto:

`dotnet add package Newtonsoft.Json`

Adicionar uma versão específica de um pacote a um projeto:

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

Adicionar um pacote usando uma fonte específica do NuGet:

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`

