---
title: '{1&gt;Visão Geral&lt;1}'
ms.date: 12/13/2019
description: Uma visão geral do Microsoft. Data. sqlite
ms.openlocfilehash: a5dc1366cc0ddfcd5501e26bf2a994456bcd5d98
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447226"
---
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="0d420-103">Visão geral do Microsoft. Data. sqlite</span><span class="sxs-lookup"><span data-stu-id="0d420-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="0d420-104">Microsoft. Data. SQLite é um provedor [ADO.net](../../../framework/data/adonet/index.md) leve para SQLite.</span><span class="sxs-lookup"><span data-stu-id="0d420-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="0d420-105">O provedor de [Entity Framework Core](/ef/core/) para SQLite é criado sobre esta biblioteca.</span><span class="sxs-lookup"><span data-stu-id="0d420-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="0d420-106">No entanto, ele também pode ser usado de forma independente ou com outras bibliotecas de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="0d420-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="0d420-107">Instalação</span><span class="sxs-lookup"><span data-stu-id="0d420-107">Installation</span></span>

<span data-ttu-id="0d420-108">A versão estável mais recente está disponível no [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span><span class="sxs-lookup"><span data-stu-id="0d420-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="0d420-109">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="0d420-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="0d420-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d420-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="0d420-111">Medição de</span><span class="sxs-lookup"><span data-stu-id="0d420-111">Usage</span></span>

<span data-ttu-id="0d420-112">Essa biblioteca implementa as abstrações ADO.NET comuns para conexões, comandos, leitores de dados e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="0d420-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="0d420-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="0d420-113">See also</span></span>

* [<span data-ttu-id="0d420-114">Cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="0d420-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="0d420-115">Referência de API</span><span class="sxs-lookup"><span data-stu-id="0d420-115">API Reference</span></span>](/dotnet/api/?view=msdata-sqlite-3.0.0)
* [<span data-ttu-id="0d420-116">Sintaxe SQL</span><span class="sxs-lookup"><span data-stu-id="0d420-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
