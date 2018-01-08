---
title: "Comando dotnet remove package – CLI do .NET Core"
description: "O comando dotnet remove package fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 1bc8d9cdc4db1f103b73116b43e630185a2c35de
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-remove-package"></a>dotnet remove package

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet remove package` – remove a referência de pacote de um arquivo de projeto.

## <a name="synopsis"></a>Sinopse

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet remove package` fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.

## <a name="arguments"></a>Arguments

`PROJECT`

Especifica o arquivo do projeto. Se não for especificado, o comando irá procurar um no diretório atual.

`PACKAGE_NAME`

A referência de pacote a ser removida.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

Remover o pacote NuGet `Newtonsoft.Json` de um projeto no diretório atual:

`dotnet remove package Newtonsoft.Json`
