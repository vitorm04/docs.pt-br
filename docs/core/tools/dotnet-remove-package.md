---
title: Comando de pacote dotnet-remove | Microsoft Docs
description: "O comando de pacote dotnet-remove fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto."
keywords: dotnet-remove, CLI, comando da CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 2fcc8d37-16b3-4581-8038-832160e72d36
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 87c80ad193df9cc3e0feabc41bb58f1d8dda23cd
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-remove-package"></a>Pacote dotnet-remove

## <a name="name"></a>Nome

`dotnet-remove package` – remove a referência de pacote de um arquivo de projeto.

## <a name="synopsis"></a>Sinopse

```
dotnet remove [project] package <package_name>
dotnet remove package [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet remove package` fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.

## <a name="arguments"></a>Arguments

`project`

Arquivo de projeto no qual operar. Se não for especificado, o comando irá procurar um no diretório atual.

`package_name`

A referência de pacote a ser removida.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

Remover o pacote NuGet `Newtonsoft.Json` de um projeto no diretório atual:

`dotnet remove package Newtonsoft.Json`
