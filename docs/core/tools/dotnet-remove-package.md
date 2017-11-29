---
title: "Comando dotnet remove package – CLI do .NET Core"
description: "O comando dotnet remove package fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 4167f5465571259975572669e27f20c586b910da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
