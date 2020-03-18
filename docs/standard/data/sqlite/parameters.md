---
title: parâmetros
ms.date: 12/13/2019
description: Aprenda a usar parâmetros SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400452"
---
# <a name="parameters"></a><span data-ttu-id="39fa0-103">parâmetros</span><span class="sxs-lookup"><span data-stu-id="39fa0-103">Parameters</span></span>

<span data-ttu-id="39fa0-104">Os parâmetros são usados para proteger contra ataques de injeção SQL.</span><span class="sxs-lookup"><span data-stu-id="39fa0-104">Parameters are used to protect against SQL injection attacks.</span></span> <span data-ttu-id="39fa0-105">Em vez de concatenar a entrada do usuário com instruções SQL, use parâmetros para garantir que a entrada seja tratada apenas como um valor literal e nunca executada.</span><span class="sxs-lookup"><span data-stu-id="39fa0-105">Instead of concatenating user input with SQL statements, use parameters to ensure input is only ever treated as a literal value and never executed.</span></span> <span data-ttu-id="39fa0-106">No SQLite, os parâmetros são normalmente permitidos em qualquer lugar que um literal seja permitido em declarações SQL.</span><span class="sxs-lookup"><span data-stu-id="39fa0-106">In SQLite, parameters are typically allowed anywhere a literal is allowed in SQL statements.</span></span>

<span data-ttu-id="39fa0-107">Os parâmetros podem `:`ser `@`prefixados com ou , ou `$`.</span><span class="sxs-lookup"><span data-stu-id="39fa0-107">Parameters can be prefixed with either `:`, `@`, or `$`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

<span data-ttu-id="39fa0-108">Consulte [os tipos de dados](types.md) para obter detalhes sobre como os valores .NET são mapeados para os valores do SQLite.</span><span class="sxs-lookup"><span data-stu-id="39fa0-108">See [Data types](types.md) for details about how .NET values are mapped to SQLite values.</span></span>

## <a name="truncation"></a><span data-ttu-id="39fa0-109">Truncation</span><span class="sxs-lookup"><span data-stu-id="39fa0-109">Truncation</span></span>

<span data-ttu-id="39fa0-110">Use <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> a propriedade para truncar valores de TEXTO e BLOB.</span><span class="sxs-lookup"><span data-stu-id="39fa0-110">Use the <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> property to truncate TEXT and BLOB values.</span></span>

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a><span data-ttu-id="39fa0-111">Tipos alternativos</span><span class="sxs-lookup"><span data-stu-id="39fa0-111">Alternative types</span></span>

<span data-ttu-id="39fa0-112">Às vezes, você pode querer usar um tipo SQLite alternativo.</span><span class="sxs-lookup"><span data-stu-id="39fa0-112">Sometimes, you may want to use an alternative SQLite type.</span></span> <span data-ttu-id="39fa0-113">Faça isso definindo a <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="39fa0-113">Do this by setting the <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> property.</span></span>

<span data-ttu-id="39fa0-114">Os seguintes mapeamentos de tipo alternativos podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="39fa0-114">The following alternative type mappings can be used.</span></span> <span data-ttu-id="39fa0-115">Para os mapeamentos padrão, consulte [Tipos de dados](types.md).</span><span class="sxs-lookup"><span data-stu-id="39fa0-115">For the default mappings, see [Data types](types.md).</span></span>

| <span data-ttu-id="39fa0-116">Valor</span><span class="sxs-lookup"><span data-stu-id="39fa0-116">Value</span></span>          | <span data-ttu-id="39fa0-117">SqliteType</span><span class="sxs-lookup"><span data-stu-id="39fa0-117">SqliteType</span></span> | <span data-ttu-id="39fa0-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="39fa0-118">Remarks</span></span>          |
| -------------- | ---------- | ---------------- |
| <span data-ttu-id="39fa0-119">Char</span><span class="sxs-lookup"><span data-stu-id="39fa0-119">Char</span></span>           | <span data-ttu-id="39fa0-120">Integer</span><span class="sxs-lookup"><span data-stu-id="39fa0-120">Integer</span></span>    | <span data-ttu-id="39fa0-121">UTF-16</span><span class="sxs-lookup"><span data-stu-id="39fa0-121">UTF-16</span></span>           |
| <span data-ttu-id="39fa0-122">Datetime</span><span class="sxs-lookup"><span data-stu-id="39fa0-122">DateTime</span></span>       | <span data-ttu-id="39fa0-123">Real</span><span class="sxs-lookup"><span data-stu-id="39fa0-123">Real</span></span>       | <span data-ttu-id="39fa0-124">Valor do dia de Julian</span><span class="sxs-lookup"><span data-stu-id="39fa0-124">Julian day value</span></span> |
| <span data-ttu-id="39fa0-125">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="39fa0-125">DateTimeOffset</span></span> | <span data-ttu-id="39fa0-126">Real</span><span class="sxs-lookup"><span data-stu-id="39fa0-126">Real</span></span>       | <span data-ttu-id="39fa0-127">Valor do dia de Julian</span><span class="sxs-lookup"><span data-stu-id="39fa0-127">Julian day value</span></span> |
| <span data-ttu-id="39fa0-128">Guid</span><span class="sxs-lookup"><span data-stu-id="39fa0-128">Guid</span></span>           | <span data-ttu-id="39fa0-129">Blob</span><span class="sxs-lookup"><span data-stu-id="39fa0-129">Blob</span></span>       |                  |
| <span data-ttu-id="39fa0-130">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="39fa0-130">TimeSpan</span></span>       | <span data-ttu-id="39fa0-131">Real</span><span class="sxs-lookup"><span data-stu-id="39fa0-131">Real</span></span>       | <span data-ttu-id="39fa0-132">Em dias</span><span class="sxs-lookup"><span data-stu-id="39fa0-132">In days</span></span>          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a><span data-ttu-id="39fa0-133">Parâmetros de saída</span><span class="sxs-lookup"><span data-stu-id="39fa0-133">Output parameters</span></span>

<span data-ttu-id="39fa0-134">O SQLite não suporta parâmetros de saída.</span><span class="sxs-lookup"><span data-stu-id="39fa0-134">SQLite doesn't support output parameters.</span></span> <span data-ttu-id="39fa0-135">Em vez disso, os valores de retorno nos resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="39fa0-135">Return values in the query results instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="39fa0-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="39fa0-136">See also</span></span>

* [<span data-ttu-id="39fa0-137">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="39fa0-137">Data types</span></span>](types.md)
