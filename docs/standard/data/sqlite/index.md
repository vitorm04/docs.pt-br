---
title: Visão geral
ms.date: 12/13/2019
description: Uma visão geral do Microsoft. Data. sqlite
ms.openlocfilehash: e84c68f0615f187e8dea7ab87ac917c0ad796a1c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543593"
---
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="42a31-103">Visão geral do Microsoft. Data. sqlite</span><span class="sxs-lookup"><span data-stu-id="42a31-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="42a31-104">Microsoft. Data. SQLite é um provedor [ADO.net](../../../framework/data/adonet/index.md) leve para SQLite.</span><span class="sxs-lookup"><span data-stu-id="42a31-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="42a31-105">O provedor de [Entity Framework Core](/ef/core/) para SQLite é criado sobre esta biblioteca.</span><span class="sxs-lookup"><span data-stu-id="42a31-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="42a31-106">No entanto, ele também pode ser usado de forma independente ou com outras bibliotecas de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="42a31-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="42a31-107">Instalação</span><span class="sxs-lookup"><span data-stu-id="42a31-107">Installation</span></span>

<span data-ttu-id="42a31-108">A versão estável mais recente está disponível no [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span><span class="sxs-lookup"><span data-stu-id="42a31-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="42a31-109">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="42a31-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[<span data-ttu-id="42a31-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="42a31-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="42a31-111">Uso</span><span class="sxs-lookup"><span data-stu-id="42a31-111">Usage</span></span>

<span data-ttu-id="42a31-112">Essa biblioteca implementa as abstrações ADO.NET comuns para conexões, comandos, leitores de dados e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="42a31-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="42a31-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="42a31-113">See also</span></span>

* [<span data-ttu-id="42a31-114">Cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="42a31-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="42a31-115">Referência de API</span><span class="sxs-lookup"><span data-stu-id="42a31-115">API Reference</span></span>](/dotnet/api/?view=msdata-sqlite-3.0)
* [<span data-ttu-id="42a31-116">Sintaxe SQL</span><span class="sxs-lookup"><span data-stu-id="42a31-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
