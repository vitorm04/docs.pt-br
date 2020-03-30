---
title: Bancos de dados na memória
ms.date: 12/13/2019
description: Aprenda a usar bancos de dados SQLite na memória.
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391202"
---
# <a name="in-memory-databases"></a><span data-ttu-id="3ec61-103">Bancos de dados na memória</span><span class="sxs-lookup"><span data-stu-id="3ec61-103">In-memory databases</span></span>

<span data-ttu-id="3ec61-104">Os bancos de dados de memória sqlite são bancos de dados armazenados inteiramente na memória, não em disco.</span><span class="sxs-lookup"><span data-stu-id="3ec61-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="3ec61-105">Use o nome `:memory:` de arquivo de origem de dados especial para criar um banco de dados na memória.</span><span class="sxs-lookup"><span data-stu-id="3ec61-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="3ec61-106">Quando a conexão é fechada, o banco de dados é excluído.</span><span class="sxs-lookup"><span data-stu-id="3ec61-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="3ec61-107">Ao `:memory:`usar, cada conexão cria seu próprio banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3ec61-107">When using `:memory:`, each connection creates its own database.</span></span>

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="3ec61-108">Bancos de dados de memória compartilháveis</span><span class="sxs-lookup"><span data-stu-id="3ec61-108">Shareable in-memory databases</span></span>

<span data-ttu-id="3ec61-109">Os bancos de dados na memória podem `Mode=Memory` ser `Cache=Shared` compartilhados entre várias conexões usando e na seqüência de conexões.</span><span class="sxs-lookup"><span data-stu-id="3ec61-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="3ec61-110">A `Data Source` palavra-chave é usada para dar um nome ao banco de dados na memória.</span><span class="sxs-lookup"><span data-stu-id="3ec61-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="3ec61-111">As seqüências de conexão usando o mesmo nome acessarão o mesmo banco de dados na memória.</span><span class="sxs-lookup"><span data-stu-id="3ec61-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="3ec61-112">O banco de dados persiste enquanto pelo menos uma conexão com ele permanecer aberta.</span><span class="sxs-lookup"><span data-stu-id="3ec61-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="3ec61-113">Uma [amostra](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrando isso está disponível no GitHub.</span><span class="sxs-lookup"><span data-stu-id="3ec61-113">A [sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
