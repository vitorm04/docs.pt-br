---
title: Bancos de dados na memória
ms.date: 12/13/2019
description: Saiba como usar bancos de dados do SQLite na memória.
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391202"
---
# <a name="in-memory-databases"></a><span data-ttu-id="9ece9-103">Bancos de dados na memória</span><span class="sxs-lookup"><span data-stu-id="9ece9-103">In-memory databases</span></span>

<span data-ttu-id="9ece9-104">Os bancos de dados na memória do SQLite são bancos de dados armazenados inteiramente na memória, não no disco.</span><span class="sxs-lookup"><span data-stu-id="9ece9-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="9ece9-105">Use o nome de arquivo `:memory:` de fonte de dados especial para criar um banco de dado na memória.</span><span class="sxs-lookup"><span data-stu-id="9ece9-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="9ece9-106">Quando a conexão é fechada, o banco de dados é excluído.</span><span class="sxs-lookup"><span data-stu-id="9ece9-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="9ece9-107">Ao usar `:memory:`o, cada conexão cria seu próprio banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9ece9-107">When using `:memory:`, each connection creates its own database.</span></span>

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="9ece9-108">Bancos de dados compartilhados na memória</span><span class="sxs-lookup"><span data-stu-id="9ece9-108">Shareable in-memory databases</span></span>

<span data-ttu-id="9ece9-109">Os bancos de dados na memória podem ser compartilhados entre várias conexões usando `Mode=Memory` e `Cache=Shared` na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="9ece9-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="9ece9-110">A `Data Source` palavra-chave é usada para fornecer um nome ao banco de dados na memória.</span><span class="sxs-lookup"><span data-stu-id="9ece9-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="9ece9-111">As cadeias de conexão que usam o mesmo nome acessarão o mesmo banco de dados na memória.</span><span class="sxs-lookup"><span data-stu-id="9ece9-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="9ece9-112">O banco de dados persiste, desde que pelo menos uma conexão permaneça aberta.</span><span class="sxs-lookup"><span data-stu-id="9ece9-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="9ece9-113">Um [exemplo](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) que demonstra isso está disponível no github.</span><span class="sxs-lookup"><span data-stu-id="9ece9-113">A [sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
