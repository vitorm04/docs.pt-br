---
title: Cláusula Order By (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: 1c84a4cdb4a149154d459ca4d9c290ed360d1772
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835005"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="986f2-102">Cláusula Order By (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="986f2-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="986f2-103">Especifica a ordem de classificação para um resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="986f2-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="986f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="986f2-104">Syntax</span></span>  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="986f2-105">Partes</span><span class="sxs-lookup"><span data-stu-id="986f2-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="986f2-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="986f2-106">Required.</span></span> <span data-ttu-id="986f2-107">Um ou mais campos do resultado da consulta atual que identificam como ordenar os valores retornados.</span><span class="sxs-lookup"><span data-stu-id="986f2-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="986f2-108">Os nomes de campo devem ser separados por vírgulas (,).</span><span class="sxs-lookup"><span data-stu-id="986f2-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="986f2-109">Você pode identificar cada campo como classificados em ordem crescente ou decrescente, usando o `Ascending` ou `Descending` palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="986f2-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="986f2-110">Se nenhum `Ascending` ou `Descending` palavra-chave for especificada, a ordem de classificação padrão é crescente.</span><span class="sxs-lookup"><span data-stu-id="986f2-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="986f2-111">Os campos de ordem de classificação terá precedência da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="986f2-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="986f2-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="986f2-112">Remarks</span></span>  
 <span data-ttu-id="986f2-113">Você pode usar o `Order By` cláusula para classificar os resultados de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="986f2-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="986f2-114">O `Order By` cláusula só pode classificar um resultado com base na variável de intervalo para o escopo atual.</span><span class="sxs-lookup"><span data-stu-id="986f2-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="986f2-115">Por exemplo, o `Select` cláusula introduz um novo escopo em uma expressão de consulta com novas variáveis de iteração para esse escopo.</span><span class="sxs-lookup"><span data-stu-id="986f2-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="986f2-116">Intervalo de variáveis definidas antes de uma `Select` cláusula em uma consulta não estão disponíveis após o `Select` cláusula.</span><span class="sxs-lookup"><span data-stu-id="986f2-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="986f2-117">Portanto, se você quiser ordenar os resultados por um campo que não está disponível na `Select` cláusula, você deve colocar o `Order By` cláusula antes do `Select` cláusula.</span><span class="sxs-lookup"><span data-stu-id="986f2-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="986f2-118">Um exemplo de quando você teria de fazer isso é quando você deseja classificar por campos não são retornadas como parte do resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="986f2-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="986f2-119">Ordem crescente e decrescente para um campo é determinado pela implementação do <xref:System.IComparable> interface para o tipo de dados do campo.</span><span class="sxs-lookup"><span data-stu-id="986f2-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="986f2-120">Se o tipo de dados não implementa o <xref:System.IComparable> interface, a ordem de classificação é ignorado.</span><span class="sxs-lookup"><span data-stu-id="986f2-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="986f2-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="986f2-121">Example</span></span>  
 <span data-ttu-id="986f2-122">A seguinte consulta de expressão usa uma `From` cláusula para declarar uma variável de intervalo `book` para o `books` coleção.</span><span class="sxs-lookup"><span data-stu-id="986f2-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="986f2-123">O `Order By` cláusula classifica o resultado da consulta por preço em ordem (o padrão) crescente.</span><span class="sxs-lookup"><span data-stu-id="986f2-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="986f2-124">Livros com o mesmo preço são classificados por título em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="986f2-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="986f2-125">O `Select` cláusula seleciona o `Title` e `Price` propriedades como valores retornados pela consulta.</span><span class="sxs-lookup"><span data-stu-id="986f2-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="986f2-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="986f2-126">Example</span></span>  
 <span data-ttu-id="986f2-127">A seguinte consulta de expressão usa o `Order By` cláusula para classificar o resultado da consulta por preço em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="986f2-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="986f2-128">Livros com o mesmo preço são classificados por título em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="986f2-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="986f2-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="986f2-129">Example</span></span>  
 <span data-ttu-id="986f2-130">A seguinte consulta de expressão usa um `Select` cláusula para selecionar o título do livro, preço, data da publicação e autor.</span><span class="sxs-lookup"><span data-stu-id="986f2-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="986f2-131">Em seguida, ele preenche os `Title`, `Price`, `PublishDate`, e `Author` campos da variável de intervalo para o novo escopo.</span><span class="sxs-lookup"><span data-stu-id="986f2-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="986f2-132">O `Order By` cláusula ordena a nova variável de intervalo pelo nome do autor, título do livro e preço.</span><span class="sxs-lookup"><span data-stu-id="986f2-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="986f2-133">Cada coluna é classificada na ordem padrão (crescente).</span><span class="sxs-lookup"><span data-stu-id="986f2-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="986f2-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="986f2-134">See also</span></span>

- [<span data-ttu-id="986f2-135">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="986f2-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="986f2-136">Consultas</span><span class="sxs-lookup"><span data-stu-id="986f2-136">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="986f2-137">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="986f2-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="986f2-138">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="986f2-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
