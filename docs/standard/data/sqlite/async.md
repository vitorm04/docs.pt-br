---
title: Limitações assíncronas
ms.date: 12/13/2019
description: Explica as limitações das APIs assíncronas e algumas alternativas que você pode usar em vez disso.
ms.openlocfilehash: 350237dc5c03023f60e9680e8b9c94aabb62606f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447079"
---
# <a name="async-limitations"></a><span data-ttu-id="0a443-103">Limitações assíncronas</span><span class="sxs-lookup"><span data-stu-id="0a443-103">Async limitations</span></span>

<span data-ttu-id="0a443-104">SQLite não dá suporte a e/s assíncrona.</span><span class="sxs-lookup"><span data-stu-id="0a443-104">SQLite doesn't support asynchronous I/O.</span></span> <span data-ttu-id="0a443-105">Os métodos Async ADO.NET serão executados de forma síncrona em Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="0a443-105">Async ADO.NET methods will execute synchronously in Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="0a443-106">Evite chamá-los.</span><span class="sxs-lookup"><span data-stu-id="0a443-106">Avoid calling them.</span></span>

<span data-ttu-id="0a443-107">Em vez disso, use o [log write-ahead](https://www.sqlite.org/wal.html) para melhorar o desempenho e a simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="0a443-107">Instead, use [write-ahead logging](https://www.sqlite.org/wal.html) to improve performance and concurrency.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> <span data-ttu-id="0a443-108">O registro em log write-ahead é habilitado por padrão em bancos de dados criados usando [Entity Framework Core](/ef/core/).</span><span class="sxs-lookup"><span data-stu-id="0a443-108">Write-ahead logging is enabled by default on databases created using [Entity Framework Core](/ef/core/).</span></span>
