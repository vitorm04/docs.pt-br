---
title: Comando dotnet-nuget-delete | Microsoft Docs
description: O comando dotnet-nuget-delete exclui ou retira da lista um pacote do servidor.
keywords: dotnet-nuget-delete, CLI, comando da CLI, .NET Core
author: karann-msft
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 6ddffde4-c789-4e90-990e-d35f6a6565d4
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 2ce157e3f32f3e899245e38bb4520b17be3e0b32
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-nuget-delete"></a>dotnet-nuget-delete

## <a name="name"></a>Nome

`dotnet-nuget-delete` – Exclui ou retira da lista um pacote do servidor. 

## <a name="synopsis"></a>Sinopse

```
dotnet nuget delete [<package_name> <package_version>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet nuget delete` exclui ou retira da lista um pacote do servidor. Para NuGet.org, a ação é remover o pacote da lista.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-s|--source <SOURCE>`

Especifica a URL do servidor. URLs com suporte para nuget.org incluem `http://www.nuget.org`, `http://www.nuget.org/api/v3` e `http://www.nuget.org/api/v2/package`. Para feeds privados, substitua o nome do host (por exemplo, `%hostname%/api/v3`).

`--non-interactive`

Não solicita entrada do usuário ou confirmações.

`-k|--api-key <API_KEY>`

A chave da API para o servidor.

`--force-english-output`

Faz com que a saída de linha de comando esteja em inglês.

## <a name="examples"></a>Exemplos

Exclui a versão 1.0 do pacote MyPackage:

`dotnet nuget delete MyPackage 1.0` 

Exclui a versão 1.0 do pacote MyPackage, não solicita ao usuário credenciais ou outra entrada:

`dotnet nuget delete MyPackage 1.0 --non-interactive`

