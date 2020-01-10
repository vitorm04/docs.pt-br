---
title: Palavras-chave de consulta – Referência de C#
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 3c08c2b6ecdaa4b875f118531e7e77f7164dd784
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713151"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="e8ad9-102">Palavras-chave de consulta (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e8ad9-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="e8ad9-103">Esta seção contém as palavras-chave contextuais usadas em expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="e8ad9-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e8ad9-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e8ad9-104">In this section</span></span>

|<span data-ttu-id="e8ad9-105">Cláusula</span><span class="sxs-lookup"><span data-stu-id="e8ad9-105">Clause</span></span>|<span data-ttu-id="e8ad9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8ad9-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="e8ad9-107">from</span><span class="sxs-lookup"><span data-stu-id="e8ad9-107">from</span></span>](from-clause.md)|<span data-ttu-id="e8ad9-108">Especifica uma fonte de dados e uma variável de intervalo (semelhante a uma variável de iteração).</span><span class="sxs-lookup"><span data-stu-id="e8ad9-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="e8ad9-109">where</span><span class="sxs-lookup"><span data-stu-id="e8ad9-109">where</span></span>](where-clause.md)|<span data-ttu-id="e8ad9-110">Filtra elementos de origem baseados em uma ou mais expressões boolianas separadas por operadores AND e OR lógicos ( `&&` ou <code>&#124;&#124;</code> ).</span><span class="sxs-lookup"><span data-stu-id="e8ad9-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="e8ad9-111">select</span><span class="sxs-lookup"><span data-stu-id="e8ad9-111">select</span></span>](select-clause.md)|<span data-ttu-id="e8ad9-112">Especifica o tipo e a forma que os elementos na sequência retornada terão quando a consulta for executada.</span><span class="sxs-lookup"><span data-stu-id="e8ad9-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="e8ad9-113">group</span><span class="sxs-lookup"><span data-stu-id="e8ad9-113">group</span></span>](group-clause.md)|<span data-ttu-id="e8ad9-114">Agrupa os resultados da consulta de acordo com um valor de chave especificado.</span><span class="sxs-lookup"><span data-stu-id="e8ad9-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="e8ad9-115">into</span><span class="sxs-lookup"><span data-stu-id="e8ad9-115">into</span></span>](into.md)|<span data-ttu-id="e8ad9-116">Fornece um identificador que pode funcionar como uma referência aos resultados de uma cláusula join, group ou select.</span><span class="sxs-lookup"><span data-stu-id="e8ad9-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="e8ad9-117">orderby</span><span class="sxs-lookup"><span data-stu-id="e8ad9-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="e8ad9-118">Classifica os resultados da consulta em ordem crescente ou decrescente com base no comparador padrão para o tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="e8ad9-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="e8ad9-119">join</span><span class="sxs-lookup"><span data-stu-id="e8ad9-119">join</span></span>](join-clause.md)|<span data-ttu-id="e8ad9-120">Une duas fontes de dados com base em uma comparação de igualdade entre dois critérios de correspondência especificados.</span><span class="sxs-lookup"><span data-stu-id="e8ad9-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="e8ad9-121">let</span><span class="sxs-lookup"><span data-stu-id="e8ad9-121">let</span></span>](let-clause.md)|<span data-ttu-id="e8ad9-122">Introduz uma variável de intervalo para armazenar os resultados de subexpressão em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="e8ad9-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="e8ad9-123">in</span><span class="sxs-lookup"><span data-stu-id="e8ad9-123">in</span></span>](in.md)|<span data-ttu-id="e8ad9-124">Palavra-chave contextual em uma cláusula [join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e8ad9-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="e8ad9-125">on</span><span class="sxs-lookup"><span data-stu-id="e8ad9-125">on</span></span>](on.md)|<span data-ttu-id="e8ad9-126">Palavra-chave contextual em uma cláusula [join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e8ad9-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="e8ad9-127">equals</span><span class="sxs-lookup"><span data-stu-id="e8ad9-127">equals</span></span>](equals.md)|<span data-ttu-id="e8ad9-128">Palavra-chave contextual em uma cláusula [join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e8ad9-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="e8ad9-129">by</span><span class="sxs-lookup"><span data-stu-id="e8ad9-129">by</span></span>](by.md)|<span data-ttu-id="e8ad9-130">Palavra-chave contextual em uma cláusula [group](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e8ad9-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="e8ad9-131">ascending</span><span class="sxs-lookup"><span data-stu-id="e8ad9-131">ascending</span></span>](ascending.md)|<span data-ttu-id="e8ad9-132">Palavra-chave contextual em uma cláusula [ordery](orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e8ad9-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="e8ad9-133">descending</span><span class="sxs-lookup"><span data-stu-id="e8ad9-133">descending</span></span>](descending.md)|<span data-ttu-id="e8ad9-134">Palavra-chave contextual em uma cláusula [ordery](orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e8ad9-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e8ad9-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="e8ad9-135">See also</span></span>

- [<span data-ttu-id="e8ad9-136">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="e8ad9-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e8ad9-137">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="e8ad9-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="e8ad9-138">LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="e8ad9-138">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="e8ad9-139">Introdução a LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="e8ad9-139">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
