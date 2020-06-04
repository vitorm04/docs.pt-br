---
title: Cláusula Order By
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
ms.openlocfilehash: 63f454064e88bc18f252940f3abd8e59b8900e5b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359742"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="f41f9-102">Cláusula Order By (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f41f9-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="f41f9-103">Especifica a ordem de classificação para um resultado de consulta.</span><span class="sxs-lookup"><span data-stu-id="f41f9-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f41f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f41f9-104">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="f41f9-105">Partes</span><span class="sxs-lookup"><span data-stu-id="f41f9-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="f41f9-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="f41f9-106">Required.</span></span> <span data-ttu-id="f41f9-107">Um ou mais campos do resultado da consulta atual que identificam como ordenar os valores retornados.</span><span class="sxs-lookup"><span data-stu-id="f41f9-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="f41f9-108">Os nomes de campo devem ser separados por vírgulas (,).</span><span class="sxs-lookup"><span data-stu-id="f41f9-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="f41f9-109">Você pode identificar cada campo como classificado em ordem crescente ou decrescente usando as `Ascending` `Descending` palavras-chave ou.</span><span class="sxs-lookup"><span data-stu-id="f41f9-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="f41f9-110">Se nenhuma `Ascending` `Descending` palavra-chave ou for especificada, a ordem de classificação padrão será crescente.</span><span class="sxs-lookup"><span data-stu-id="f41f9-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="f41f9-111">Os campos de ordem de classificação recebem precedência da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="f41f9-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f41f9-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="f41f9-112">Remarks</span></span>  
 <span data-ttu-id="f41f9-113">Você pode usar a `Order By` cláusula para classificar os resultados de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="f41f9-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="f41f9-114">A `Order By` cláusula só pode classificar um resultado com base na variável de intervalo para o escopo atual.</span><span class="sxs-lookup"><span data-stu-id="f41f9-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="f41f9-115">Por exemplo, a `Select` cláusula apresenta um novo escopo em uma expressão de consulta com novas variáveis de iteração para esse escopo.</span><span class="sxs-lookup"><span data-stu-id="f41f9-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="f41f9-116">Variáveis de intervalo definidas antes de uma `Select` cláusula em uma consulta não estão disponíveis após a `Select` cláusula.</span><span class="sxs-lookup"><span data-stu-id="f41f9-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="f41f9-117">Portanto, se você quiser ordenar os resultados por um campo que não está disponível na `Select` cláusula, deverá colocar a `Order By` cláusula antes da `Select` cláusula.</span><span class="sxs-lookup"><span data-stu-id="f41f9-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="f41f9-118">Um exemplo de quando você precisa fazer isso é quando deseja classificar sua consulta por campos que não são retornados como parte do resultado.</span><span class="sxs-lookup"><span data-stu-id="f41f9-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="f41f9-119">Ordem crescente e decrescente para um campo é determinada pela implementação da <xref:System.IComparable> interface para o tipo de dados do campo.</span><span class="sxs-lookup"><span data-stu-id="f41f9-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="f41f9-120">Se o tipo de dados não implementar a <xref:System.IComparable> interface, a ordem de classificação será ignorada.</span><span class="sxs-lookup"><span data-stu-id="f41f9-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f41f9-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f41f9-121">Example</span></span>  
 <span data-ttu-id="f41f9-122">A expressão de consulta a seguir usa uma `From` cláusula para declarar uma variável `book` de intervalo para a `books` coleção.</span><span class="sxs-lookup"><span data-stu-id="f41f9-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="f41f9-123">A `Order By` cláusula classifica o resultado da consulta por preço em ordem crescente (o padrão).</span><span class="sxs-lookup"><span data-stu-id="f41f9-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="f41f9-124">Os livros com o mesmo preço são classificados por título em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="f41f9-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="f41f9-125">A `Select` cláusula seleciona as `Title` `Price` Propriedades e como os valores retornados pela consulta.</span><span class="sxs-lookup"><span data-stu-id="f41f9-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="f41f9-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f41f9-126">Example</span></span>  
 <span data-ttu-id="f41f9-127">A expressão de consulta a seguir usa a `Order By` cláusula para classificar o resultado da consulta por preço em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="f41f9-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="f41f9-128">Os livros com o mesmo preço são classificados por título em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="f41f9-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="f41f9-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f41f9-129">Example</span></span>  
 <span data-ttu-id="f41f9-130">A expressão de consulta a seguir usa uma `Select` cláusula para selecionar o título do livro, o preço, a data de publicação e o autor.</span><span class="sxs-lookup"><span data-stu-id="f41f9-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="f41f9-131">Em seguida, ele preenche `Title` os `Price` campos,, `PublishDate` e `Author` da variável de intervalo para o novo escopo.</span><span class="sxs-lookup"><span data-stu-id="f41f9-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="f41f9-132">A `Order By` cláusula ordena a nova variável de intervalo por nome do autor, título do livro e, em seguida, Price.</span><span class="sxs-lookup"><span data-stu-id="f41f9-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="f41f9-133">Cada coluna é classificada na ordem padrão (em ordem crescente).</span><span class="sxs-lookup"><span data-stu-id="f41f9-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="f41f9-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="f41f9-134">See also</span></span>

- [<span data-ttu-id="f41f9-135">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f41f9-135">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="f41f9-136">Consultas</span><span class="sxs-lookup"><span data-stu-id="f41f9-136">Queries</span></span>](index.md)
- [<span data-ttu-id="f41f9-137">Cláusula SELECT</span><span class="sxs-lookup"><span data-stu-id="f41f9-137">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="f41f9-138">Cláusula from</span><span class="sxs-lookup"><span data-stu-id="f41f9-138">From Clause</span></span>](from-clause.md)
