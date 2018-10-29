---
title: Comando dotnet nuget delete – CLI do .NET Core
description: O comando dotnet-nuget-delete exclui ou retira da lista um pacote do servidor.
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: f4aa027a465c4adea1de13853063d03e8e295411
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180869"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet nuget delete` – Exclui ou retira da lista um pacote do servidor.

## <a name="synopsis"></a>Sinopse

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a>Descrição

O comando `dotnet nuget delete` exclui ou retira da lista um pacote do servidor. Para [nuget.org](https://www.nuget.org/), a ação é remover o pacote da lista.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Nome/ID do pacote a ser excluído.

`PACKAGE_VERSION`

Versão do pacote a ser excluído.

## <a name="options"></a>Opções

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--force-english-output`

 Força a execução do aplicativo usando uma cultura invariável com base em inglês.

`-h|--help`

Imprime uma ajuda breve para o comando.

`-k|--api-key <API_KEY>`

A chave da API para o servidor.

`--no-service-endpoint` Não acrescenta "api/v2/package" à URL de origem.

`--non-interactive`

Não solicita entrada do usuário ou confirmações.

`-s|--source <SOURCE>`

Especifica a URL do servidor. URLs com suporte para nuget.org incluem `https://www.nuget.org`, `https://www.nuget.org/api/v3` e `https://www.nuget.org/api/v2/package`. Para feeds privados, substitua o nome do host (por exemplo, `%hostname%/api/v3`).

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--force-english-output`

 Força a execução do aplicativo usando uma cultura invariável com base em inglês.

`-h|--help`

Imprime uma ajuda breve para o comando.

`-k|--api-key <API_KEY>`

A chave da API para o servidor.

`--non-interactive`

Não solicita entrada do usuário ou confirmações.

`-s|--source <SOURCE>`

Especifica a URL do servidor. URLs com suporte para nuget.org incluem `https://www.nuget.org`, `https://www.nuget.org/api/v3` e `https://www.nuget.org/api/v2/package`. Para feeds privados, substitua o nome do host (por exemplo, `%hostname%/api/v3`).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--force-english-output`

 Força a execução do aplicativo usando uma cultura invariável com base em inglês.

`-h|--help`

Imprime uma ajuda breve para o comando.

`-k|--api-key <API_KEY>`

A chave da API para o servidor.

`--non-interactive`

Não solicita entrada do usuário ou confirmações.

`-s|--source <SOURCE>`

Especifica a URL do servidor. URLs com suporte para nuget.org incluem `https://www.nuget.org`, `https://www.nuget.org/api/v3` e `https://www.nuget.org/api/v2/package`. Para feeds privados, substitua o nome do host (por exemplo, `%hostname%/api/v3`).

---

## <a name="examples"></a>Exemplos

Exclui a versão 1.0 do pacote `Microsoft.AspNetCore.Mvc`:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

Exclui a versão 1.0 do pacote `Microsoft.AspNetCore.Mvc`, não solicita ao usuário credenciais ou outra entrada:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
