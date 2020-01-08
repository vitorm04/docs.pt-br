---
title: Parâmetros
ms.date: 12/13/2019
description: Saiba como usar parâmetros SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447184"
---
# <a name="parameters"></a><span data-ttu-id="cc953-103">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cc953-103">Parameters</span></span>

<span data-ttu-id="cc953-104">Os parâmetros são usados para proteger contra ataques de injeção de SQL.</span><span class="sxs-lookup"><span data-stu-id="cc953-104">Parameters are used to protect against SQL injection attacks.</span></span> <span data-ttu-id="cc953-105">Em vez de concatenar a entrada do usuário com instruções SQL, use parâmetros para garantir que a entrada seja tratada apenas como um valor literal e nunca executada.</span><span class="sxs-lookup"><span data-stu-id="cc953-105">Instead of concatenating user input with SQL statements, use parameters to ensure input is only ever treated as a literal value and never executed.</span></span> <span data-ttu-id="cc953-106">No SQLite, os parâmetros são geralmente permitidos em qualquer lugar que um literal é permitido em instruções SQL.</span><span class="sxs-lookup"><span data-stu-id="cc953-106">In SQLite, parameters are typically allowed anywhere a literal is allowed in SQL statements.</span></span>

<span data-ttu-id="cc953-107">Os parâmetros podem ter como prefixo `:`, `@`ou `$`.</span><span class="sxs-lookup"><span data-stu-id="cc953-107">Parameters can be prefixed with either `:`, `@`, or `$`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

<span data-ttu-id="cc953-108">Consulte [tipos de dados](types.md) para obter detalhes sobre como os valores do .NET são mapeados para os valores do SQLite.</span><span class="sxs-lookup"><span data-stu-id="cc953-108">See [Data types](types.md) for details about how .NET values are mapped to SQLite values.</span></span>

## <a name="truncation"></a><span data-ttu-id="cc953-109">Truncamento</span><span class="sxs-lookup"><span data-stu-id="cc953-109">Truncation</span></span>

<span data-ttu-id="cc953-110">Use a propriedade <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> para truncar valores de texto e BLOB.</span><span class="sxs-lookup"><span data-stu-id="cc953-110">Use the <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> property to truncate TEXT and BLOB values.</span></span>

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a><span data-ttu-id="cc953-111">Tipos alternativos</span><span class="sxs-lookup"><span data-stu-id="cc953-111">Alternative types</span></span>

<span data-ttu-id="cc953-112">Às vezes, talvez você queira usar um tipo SQLite alternativo.</span><span class="sxs-lookup"><span data-stu-id="cc953-112">Sometimes, you may want to use an alternative SQLite type.</span></span> <span data-ttu-id="cc953-113">Faça isso definindo a propriedade <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType>.</span><span class="sxs-lookup"><span data-stu-id="cc953-113">Do this by setting the <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> property.</span></span>

<span data-ttu-id="cc953-114">Os mapeamentos de tipo alternativo a seguir podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="cc953-114">The following alternative type mappings can be used.</span></span> <span data-ttu-id="cc953-115">Para os mapeamentos padrão, consulte [tipos de dados](types.md).</span><span class="sxs-lookup"><span data-stu-id="cc953-115">For the default mappings, see [Data types](types.md).</span></span>

| <span data-ttu-id="cc953-116">Value</span><span class="sxs-lookup"><span data-stu-id="cc953-116">Value</span></span>          | <span data-ttu-id="cc953-117">Sqlitetype</span><span class="sxs-lookup"><span data-stu-id="cc953-117">SqliteType</span></span> | <span data-ttu-id="cc953-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc953-118">Remarks</span></span>          |
| -------------- | ---------- | ---------------- |
| <span data-ttu-id="cc953-119">Char</span><span class="sxs-lookup"><span data-stu-id="cc953-119">Char</span></span>           | <span data-ttu-id="cc953-120">Inteiro</span><span class="sxs-lookup"><span data-stu-id="cc953-120">Integer</span></span>    | <span data-ttu-id="cc953-121">UTF-16</span><span class="sxs-lookup"><span data-stu-id="cc953-121">UTF-16</span></span>           |
| <span data-ttu-id="cc953-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="cc953-122">DateTime</span></span>       | <span data-ttu-id="cc953-123">Real</span><span class="sxs-lookup"><span data-stu-id="cc953-123">Real</span></span>       | <span data-ttu-id="cc953-124">Valor do dia Juliano</span><span class="sxs-lookup"><span data-stu-id="cc953-124">Julian day value</span></span> |
| <span data-ttu-id="cc953-125">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="cc953-125">DateTimeOffset</span></span> | <span data-ttu-id="cc953-126">Real</span><span class="sxs-lookup"><span data-stu-id="cc953-126">Real</span></span>       | <span data-ttu-id="cc953-127">Valor do dia Juliano</span><span class="sxs-lookup"><span data-stu-id="cc953-127">Julian day value</span></span> |
| <span data-ttu-id="cc953-128">{1&gt;Guid&lt;1}</span><span class="sxs-lookup"><span data-stu-id="cc953-128">Guid</span></span>           | <span data-ttu-id="cc953-129">Blob</span><span class="sxs-lookup"><span data-stu-id="cc953-129">Blob</span></span>       |                  |
| <span data-ttu-id="cc953-130">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="cc953-130">TimeSpan</span></span>       | <span data-ttu-id="cc953-131">Real</span><span class="sxs-lookup"><span data-stu-id="cc953-131">Real</span></span>       | <span data-ttu-id="cc953-132">Em dias</span><span class="sxs-lookup"><span data-stu-id="cc953-132">In days</span></span>          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a><span data-ttu-id="cc953-133">Parâmetros de saída</span><span class="sxs-lookup"><span data-stu-id="cc953-133">Output parameters</span></span>

<span data-ttu-id="cc953-134">O SQLite não dá suporte a parâmetros de saída.</span><span class="sxs-lookup"><span data-stu-id="cc953-134">SQLite doesn't support output parameters.</span></span> <span data-ttu-id="cc953-135">Em vez disso, retorna valores nos resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="cc953-135">Return values in the query results instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc953-136">Veja também</span><span class="sxs-lookup"><span data-stu-id="cc953-136">See also</span></span>

* [<span data-ttu-id="cc953-137">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="cc953-137">Data types</span></span>](types.md)
