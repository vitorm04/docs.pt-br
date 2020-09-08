---
title: Limitações assíncronas
ms.date: 09/04/2020
description: Explica as limitações das APIs assíncronas e algumas alternativas que você pode usar em vez disso.
ms.openlocfilehash: 8b14fcfeb12d331d8d43ca6d77332007a12ae5dc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89515989"
---
# <a name="async-limitations"></a><span data-ttu-id="77130-103">Limitações assíncronas</span><span class="sxs-lookup"><span data-stu-id="77130-103">Async limitations</span></span>

<span data-ttu-id="77130-104">SQLite não dá suporte a e/s assíncrona.</span><span class="sxs-lookup"><span data-stu-id="77130-104">SQLite doesn't support asynchronous I/O.</span></span> <span data-ttu-id="77130-105">Os métodos Async ADO.NET serão executados de forma síncrona em Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="77130-105">Async ADO.NET methods will execute synchronously in Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="77130-106">Evite chamá-los.</span><span class="sxs-lookup"><span data-stu-id="77130-106">Avoid calling them.</span></span>

<span data-ttu-id="77130-107">Em vez disso, use um [cache compartilhado](connection-strings.md#cache) e um [log write-ahead](https://www.sqlite.org/wal.html) para melhorar o desempenho e a simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="77130-107">Instead, use a [shared cache](connection-strings.md#cache) and [write-ahead logging](https://www.sqlite.org/wal.html) to improve performance and concurrency.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> <span data-ttu-id="77130-108">O registro em log write-ahead é habilitado por padrão em bancos de dados criados usando [Entity Framework Core](/ef/core/).</span><span class="sxs-lookup"><span data-stu-id="77130-108">Write-ahead logging is enabled by default on databases created using [Entity Framework Core](/ef/core/).</span></span>
