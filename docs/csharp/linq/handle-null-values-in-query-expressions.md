---
title: "Manipular valores nulos em expressões de consulta"
description: "Como manipular valores nulos em expressões de consulta."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: d16256e31b073a599504ffef6501ed34430a7694
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="717e2-104">Manipular valores nulos em expressões de consulta</span><span class="sxs-lookup"><span data-stu-id="717e2-104">Handle null values in query expressions</span></span>

<span data-ttu-id="717e2-105">Este exemplo mostra como tratar os possíveis valores nulos em coleções de origem.</span><span class="sxs-lookup"><span data-stu-id="717e2-105">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="717e2-106">Uma coleção de objetos, tal como uma <xref:System.Collections.Generic.IEnumerable%601>, pode conter elementos cujo valor é [null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="717e2-106">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="717e2-107">Se uma coleção de origem for nula ou contiver um elemento cujo valor for null e sua consulta não lidar com valores null, uma <xref:System.NullReferenceException> será gerada ao executar a consulta.</span><span class="sxs-lookup"><span data-stu-id="717e2-107">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="717e2-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="717e2-108">Example</span></span>

 <span data-ttu-id="717e2-109">Você pode escrever o código defensivamente para evitar uma exceção de referência nula conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="717e2-109">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 <span data-ttu-id="717e2-110">No exemplo anterior, a cláusula `where` filtra todos os elementos nulos na sequência de categorias.</span><span class="sxs-lookup"><span data-stu-id="717e2-110">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="717e2-111">Essa técnica é independente da verificação de nulos na cláusula join.</span><span class="sxs-lookup"><span data-stu-id="717e2-111">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="717e2-112">A expressão condicional com null nesse exemplo funciona porque `Products.CategoryID` é do tipo `int?` que é uma abreviação para `Nullable<int>`.</span><span class="sxs-lookup"><span data-stu-id="717e2-112">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="717e2-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="717e2-113">Example</span></span>

 <span data-ttu-id="717e2-114">Em uma cláusula join, se apenas uma das chaves de comparação for um tipo de valor que permite valor nulo, você pode converter a outra para um tipo que permite valor nulo na expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="717e2-114">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="717e2-115">No exemplo a seguir, suponha que `EmployeeID` é uma coluna que contém os valores do tipo `int?`:</span><span class="sxs-lookup"><span data-stu-id="717e2-115">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="717e2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="717e2-116">See also</span></span>  
 <xref:System.Nullable%601>  
 [<span data-ttu-id="717e2-117">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="717e2-117">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="717e2-118">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="717e2-118">Nullable types</span></span>](../programming-guide/nullable-types/index.md)
