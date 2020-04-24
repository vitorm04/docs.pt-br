---
title: Limitações do ADO.NET
ms.date: 12/13/2019
description: Descreve algumas das limitações do ADO.NET que você pode encontrar.
ms.openlocfilehash: 8664b73071fc859ed30080f549b05e7d6ed020f4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901260"
---
# <a name="adonet-limitations"></a><span data-ttu-id="e9563-103">Limitações do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e9563-103">ADO.NET limitations</span></span>

<span data-ttu-id="e9563-104">O Microsoft. Data. sqlite fornece implementações de muitas das abstrações ADO.NET, mas há algumas limitações.</span><span class="sxs-lookup"><span data-stu-id="e9563-104">Microsoft.Data.Sqlite provides implementations of many of the ADO.NET abstractions, but there are some limitations.</span></span>

## <a name="database-schema-information"></a><span data-ttu-id="e9563-105">Informações de esquema de banco de dados</span><span class="sxs-lookup"><span data-stu-id="e9563-105">Database schema information</span></span>

<span data-ttu-id="e9563-106">Os metadados sobre os resultados da consulta estão <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> disponíveis usando o método.</span><span class="sxs-lookup"><span data-stu-id="e9563-106">Metadata about query results is available using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method.</span></span>

<span data-ttu-id="e9563-107">`DbConnection.GetSchema()`Não está implementado.</span><span class="sxs-lookup"><span data-stu-id="e9563-107">`DbConnection.GetSchema()` isn't implemented.</span></span> <span data-ttu-id="e9563-108">Essa API não é bem definida, portanto, é recomendável recuperar os metadados do banco de dados diretamente usando as APIs do SQLite padrão, como a tabela de [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) e o [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) pragma.</span><span class="sxs-lookup"><span data-stu-id="e9563-108">This API isn't well-defined, so we recommend retrieving database metadata directly using standard SQLite APIs like the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and the [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) PRAGMA.</span></span>

<span data-ttu-id="e9563-109">Para obter mais informações, consulte [metadados](metadata.md).</span><span class="sxs-lookup"><span data-stu-id="e9563-109">For more information, see [Metadata](metadata.md).</span></span>

## <a name="systemtransactions"></a><span data-ttu-id="e9563-110">System.Transactions</span><span class="sxs-lookup"><span data-stu-id="e9563-110">System.Transactions</span></span>

<span data-ttu-id="e9563-111">Microsoft. Data. sqlite ainda não dá suporte a System. Transactions.</span><span class="sxs-lookup"><span data-stu-id="e9563-111">Microsoft.Data.Sqlite doesn't yet support System.Transactions.</span></span> <span data-ttu-id="e9563-112">Em vez disso, use transações ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="e9563-112">Use ADO.NET transactions instead.</span></span> <span data-ttu-id="e9563-113">Para obter mais informações, veja [Transações](transactions.md).</span><span class="sxs-lookup"><span data-stu-id="e9563-113">For more information, see [Transactions](transactions.md).</span></span>

<span data-ttu-id="e9563-114">Forneça comentários sobre a falta de suporte para System. Transactions no problema [#13825](https://github.com/dotnet/efcore/issues/13825).</span><span class="sxs-lookup"><span data-stu-id="e9563-114">Provide feedback about the lack of support for System.Transactions on issue [#13825](https://github.com/dotnet/efcore/issues/13825).</span></span>

## <a name="data-adapters"></a><span data-ttu-id="e9563-115">Adaptadores de dados</span><span class="sxs-lookup"><span data-stu-id="e9563-115">Data adapters</span></span>

<span data-ttu-id="e9563-116">`DbDataAdapter`Ainda não está implementado pelo Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="e9563-116">`DbDataAdapter` isn't yet implemented by Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="e9563-117">Isso significa que você só pode usar `DataSet` ADO.NET `DataTable` e carregar dados e não atualizá-los.</span><span class="sxs-lookup"><span data-stu-id="e9563-117">This means you can only use ADO.NET `DataSet` and `DataTable` to load data and not update it.</span></span>

<span data-ttu-id="e9563-118">Use o Issue [#13838](https://github.com/dotnet/efcore/issues/13838) para fornecer comentários sobre `DbDataAdapter`a implementação.</span><span class="sxs-lookup"><span data-stu-id="e9563-118">Use issue [#13838](https://github.com/dotnet/efcore/issues/13838) to provide feedback about implementing `DbDataAdapter`.</span></span>

## <a name="output-parameters"></a><span data-ttu-id="e9563-119">Parâmetros de saída</span><span class="sxs-lookup"><span data-stu-id="e9563-119">Output parameters</span></span>

<span data-ttu-id="e9563-120">O SQLite não dá suporte a parâmetros de saída.</span><span class="sxs-lookup"><span data-stu-id="e9563-120">SQLite doesn't support output parameters.</span></span>

## <a name="positional-parameters"></a><span data-ttu-id="e9563-121">Parâmetros posicionais</span><span class="sxs-lookup"><span data-stu-id="e9563-121">Positional parameters</span></span>

<span data-ttu-id="e9563-122">Microsoft. Data. sqlite só dá suporte a [parâmetros](parameters.md)nomeados.</span><span class="sxs-lookup"><span data-stu-id="e9563-122">Microsoft.Data.Sqlite only supports named [parameters](parameters.md).</span></span> <span data-ttu-id="e9563-123">Não há suporte para parâmetros posicionais.</span><span class="sxs-lookup"><span data-stu-id="e9563-123">Positional parameters aren't supported.</span></span>

## <a name="stored-procedures"></a><span data-ttu-id="e9563-124">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="e9563-124">Stored procedures</span></span>

<span data-ttu-id="e9563-125">O SQLite não dá suporte a procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="e9563-125">SQLite doesn't support stored procedures.</span></span>

## <a name="isolation-levels"></a><span data-ttu-id="e9563-126">Níveis de isolamento</span><span class="sxs-lookup"><span data-stu-id="e9563-126">Isolation levels</span></span>

<span data-ttu-id="e9563-127">Os `Chaos` níveis `Snapshot` de isolamento e não têm suporte em transações SQLite.</span><span class="sxs-lookup"><span data-stu-id="e9563-127">The `Chaos` and `Snapshot` isolation levels aren't supported in SQLite transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9563-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="e9563-128">See also</span></span>

* [<span data-ttu-id="e9563-129">Limitações assíncronas</span><span class="sxs-lookup"><span data-stu-id="e9563-129">Async limitations</span></span>](async.md)
* [<span data-ttu-id="e9563-130">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="e9563-130">Data types</span></span>](types.md)
* [<span data-ttu-id="e9563-131">Transactions</span><span class="sxs-lookup"><span data-stu-id="e9563-131">Transactions</span></span>](transactions.md)
