---
title: Manipular valores nulos em expressões de consulta
description: Como manipular valores nulos em expressões de consulta.
ms.date: 12/1/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: ecd174462ef51a6dd7b7696abb9e111fc32d9ec7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272381"
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="52590-103">Manipular valores nulos em expressões de consulta</span><span class="sxs-lookup"><span data-stu-id="52590-103">Handle null values in query expressions</span></span>

<span data-ttu-id="52590-104">Este exemplo mostra como tratar os possíveis valores nulos em coleções de origem.</span><span class="sxs-lookup"><span data-stu-id="52590-104">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="52590-105">Uma coleção de objetos, tal como uma <xref:System.Collections.Generic.IEnumerable%601>, pode conter elementos cujo valor é [null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="52590-105">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="52590-106">Se uma coleção de origem for nula ou contiver um elemento cujo valor for null e sua consulta não lidar com valores null, uma <xref:System.NullReferenceException> será gerada ao executar a consulta.</span><span class="sxs-lookup"><span data-stu-id="52590-106">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52590-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52590-107">Example</span></span>

 <span data-ttu-id="52590-108">Você pode escrever o código defensivamente para evitar uma exceção de referência nula conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="52590-108">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 <span data-ttu-id="52590-109">No exemplo anterior, a cláusula `where` filtra todos os elementos nulos na sequência de categorias.</span><span class="sxs-lookup"><span data-stu-id="52590-109">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="52590-110">Essa técnica é independente da verificação de nulos na cláusula join.</span><span class="sxs-lookup"><span data-stu-id="52590-110">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="52590-111">A expressão condicional com null nesse exemplo funciona porque `Products.CategoryID` é do tipo `int?` que é uma abreviação para `Nullable<int>`.</span><span class="sxs-lookup"><span data-stu-id="52590-111">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52590-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52590-112">Example</span></span>

 <span data-ttu-id="52590-113">Em uma cláusula join, se apenas uma das chaves de comparação for um tipo de valor que permite valor nulo, você pode converter a outra para um tipo que permite valor nulo na expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="52590-113">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="52590-114">No exemplo a seguir, suponha que `EmployeeID` é uma coluna que contém os valores do tipo `int?`:</span><span class="sxs-lookup"><span data-stu-id="52590-114">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="52590-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52590-115">See also</span></span>  
 <xref:System.Nullable%601>  
 [<span data-ttu-id="52590-116">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="52590-116">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="52590-117">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="52590-117">Nullable types</span></span>](../programming-guide/nullable-types/index.md)
