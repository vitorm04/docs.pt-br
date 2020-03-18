---
title: Palavras-chave de consulta – Referência de C#
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 01134eda540c5141afbd11b2c89ff779da495a9a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173517"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="37c81-102">Palavras-chave de consulta (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="37c81-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="37c81-103">Esta seção contém as palavras-chave contextuais usadas em expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="37c81-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="37c81-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="37c81-104">In this section</span></span>

|<span data-ttu-id="37c81-105">Cláusula</span><span class="sxs-lookup"><span data-stu-id="37c81-105">Clause</span></span>|<span data-ttu-id="37c81-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="37c81-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="37c81-107">De</span><span class="sxs-lookup"><span data-stu-id="37c81-107">from</span></span>](from-clause.md)|<span data-ttu-id="37c81-108">Especifica uma fonte de dados e uma variável de intervalo (semelhante a uma variável de iteração).</span><span class="sxs-lookup"><span data-stu-id="37c81-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="37c81-109">Onde</span><span class="sxs-lookup"><span data-stu-id="37c81-109">where</span></span>](where-clause.md)|<span data-ttu-id="37c81-110">Filtra elementos de origem baseados em uma ou mais expressões boolianas separadas por operadores AND e OR lógicos ( `&&` ou <code>&#124;&#124;</code> ).</span><span class="sxs-lookup"><span data-stu-id="37c81-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="37c81-111">Selecione</span><span class="sxs-lookup"><span data-stu-id="37c81-111">select</span></span>](select-clause.md)|<span data-ttu-id="37c81-112">Especifica o tipo e a forma que os elementos na sequência retornada terão quando a consulta for executada.</span><span class="sxs-lookup"><span data-stu-id="37c81-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="37c81-113">grupo</span><span class="sxs-lookup"><span data-stu-id="37c81-113">group</span></span>](group-clause.md)|<span data-ttu-id="37c81-114">Agrupa os resultados da consulta de acordo com um valor de chave especificado.</span><span class="sxs-lookup"><span data-stu-id="37c81-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="37c81-115">Em</span><span class="sxs-lookup"><span data-stu-id="37c81-115">into</span></span>](into.md)|<span data-ttu-id="37c81-116">Fornece um identificador que pode funcionar como uma referência aos resultados de uma cláusula join, group ou select.</span><span class="sxs-lookup"><span data-stu-id="37c81-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="37c81-117">Orderby</span><span class="sxs-lookup"><span data-stu-id="37c81-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="37c81-118">Classifica os resultados da consulta em ordem crescente ou decrescente com base no comparador padrão para o tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="37c81-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="37c81-119">Juntar</span><span class="sxs-lookup"><span data-stu-id="37c81-119">join</span></span>](join-clause.md)|<span data-ttu-id="37c81-120">Une duas fontes de dados com base em uma comparação de igualdade entre dois critérios de correspondência especificados.</span><span class="sxs-lookup"><span data-stu-id="37c81-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="37c81-121">Deixe</span><span class="sxs-lookup"><span data-stu-id="37c81-121">let</span></span>](let-clause.md)|<span data-ttu-id="37c81-122">Introduz uma variável de intervalo para armazenar os resultados de subexpressão em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="37c81-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="37c81-123">Em</span><span class="sxs-lookup"><span data-stu-id="37c81-123">in</span></span>](in.md)|<span data-ttu-id="37c81-124">Palavra-chave contextual em uma cláusula [join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="37c81-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="37c81-125">Em</span><span class="sxs-lookup"><span data-stu-id="37c81-125">on</span></span>](on.md)|<span data-ttu-id="37c81-126">Palavra-chave contextual em uma cláusula [join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="37c81-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="37c81-127">Equals</span><span class="sxs-lookup"><span data-stu-id="37c81-127">equals</span></span>](equals.md)|<span data-ttu-id="37c81-128">Palavra-chave contextual em uma cláusula [join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="37c81-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="37c81-129">Por</span><span class="sxs-lookup"><span data-stu-id="37c81-129">by</span></span>](by.md)|<span data-ttu-id="37c81-130">Palavra-chave contextual em uma cláusula [group](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="37c81-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="37c81-131">Crescente</span><span class="sxs-lookup"><span data-stu-id="37c81-131">ascending</span></span>](ascending.md)|<span data-ttu-id="37c81-132">Palavra-chave contextual em uma cláusula [ordery](orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="37c81-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="37c81-133">Descendente</span><span class="sxs-lookup"><span data-stu-id="37c81-133">descending</span></span>](descending.md)|<span data-ttu-id="37c81-134">Palavra-chave contextual em uma cláusula [ordery](orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="37c81-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="37c81-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="37c81-135">See also</span></span>

- [<span data-ttu-id="37c81-136">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="37c81-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="37c81-137">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="37c81-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="37c81-138">LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="37c81-138">LINQ in C#</span></span>](../../linq/index.md)
