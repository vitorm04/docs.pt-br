---
title: Visão geral
ms.date: 12/13/2019
description: Uma visão geral do Microsoft. Data. sqlite
ms.openlocfilehash: 7c952848f7e7ea04f11fe9340f77a1f376a1be07
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552434"
---
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="82f3b-103">Visão geral do Microsoft. Data. sqlite</span><span class="sxs-lookup"><span data-stu-id="82f3b-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="82f3b-104">Microsoft. Data. SQLite é um provedor [ADO.net](../../../framework/data/adonet/index.md) leve para SQLite.</span><span class="sxs-lookup"><span data-stu-id="82f3b-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="82f3b-105">O provedor de [Entity Framework Core](/ef/core/) para SQLite é criado sobre esta biblioteca.</span><span class="sxs-lookup"><span data-stu-id="82f3b-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="82f3b-106">No entanto, ele também pode ser usado de forma independente ou com outras bibliotecas de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="82f3b-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="82f3b-107">Instalação</span><span class="sxs-lookup"><span data-stu-id="82f3b-107">Installation</span></span>

<span data-ttu-id="82f3b-108">A versão estável mais recente está disponível no [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span><span class="sxs-lookup"><span data-stu-id="82f3b-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="82f3b-109">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="82f3b-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[<span data-ttu-id="82f3b-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="82f3b-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="82f3b-111">Uso</span><span class="sxs-lookup"><span data-stu-id="82f3b-111">Usage</span></span>

<span data-ttu-id="82f3b-112">Essa biblioteca implementa as abstrações ADO.NET comuns para conexões, comandos, leitores de dados e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="82f3b-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="82f3b-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="82f3b-113">See also</span></span>

* [<span data-ttu-id="82f3b-114">Cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="82f3b-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="82f3b-115">Referência da API</span><span class="sxs-lookup"><span data-stu-id="82f3b-115">API Reference</span></span>](../../../../api/index.md?view=msdata-sqlite-3.0)
* [<span data-ttu-id="82f3b-116">Sintaxe SQL</span><span class="sxs-lookup"><span data-stu-id="82f3b-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
