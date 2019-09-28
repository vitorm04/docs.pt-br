---
title: Manipular valores nulos em expressões de consulta (LINQ em C#)
description: Saiba como manipular valores nulos em expressões de consulta LINQ em C#.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 38a5c5e4a869cc44be78f70cbf0e50166baaab16
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353328"
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="02da2-103">Manipular valores nulos em expressões de consulta</span><span class="sxs-lookup"><span data-stu-id="02da2-103">Handle null values in query expressions</span></span>

<span data-ttu-id="02da2-104">Este exemplo mostra como tratar os possíveis valores nulos em coleções de origem.</span><span class="sxs-lookup"><span data-stu-id="02da2-104">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="02da2-105">Uma coleção de objetos, tal como uma <xref:System.Collections.Generic.IEnumerable%601>, pode conter elementos cujo valor é [null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="02da2-105">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="02da2-106">Se uma coleção de origem for nula ou contiver um elemento cujo valor for null e sua consulta não lidar com valores null, uma <xref:System.NullReferenceException> será gerada ao executar a consulta.</span><span class="sxs-lookup"><span data-stu-id="02da2-106">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>

## <a name="example"></a><span data-ttu-id="02da2-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="02da2-107">Example</span></span>

<span data-ttu-id="02da2-108">Você pode escrever o código defensivamente para evitar uma exceção de referência nula conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="02da2-108">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

<span data-ttu-id="02da2-109">No exemplo anterior, a cláusula `where` filtra todos os elementos nulos na sequência de categorias.</span><span class="sxs-lookup"><span data-stu-id="02da2-109">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="02da2-110">Essa técnica é independente da verificação de nulos na cláusula join.</span><span class="sxs-lookup"><span data-stu-id="02da2-110">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="02da2-111">A expressão condicional com null nesse exemplo funciona porque `Products.CategoryID` é do tipo `int?` que é uma abreviação para `Nullable<int>`.</span><span class="sxs-lookup"><span data-stu-id="02da2-111">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>

## <a name="example"></a><span data-ttu-id="02da2-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="02da2-112">Example</span></span>

<span data-ttu-id="02da2-113">Em uma cláusula join, se apenas uma das chaves de comparação for um tipo de valor que permite valor nulo, você pode converter a outra para um tipo que permite valor nulo na expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="02da2-113">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="02da2-114">No exemplo a seguir, suponha que `EmployeeID` é uma coluna que contém os valores do tipo `int?`:</span><span class="sxs-lookup"><span data-stu-id="02da2-114">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="02da2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02da2-115">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="02da2-116">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="02da2-116">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="02da2-117">Tipos de valor anuláveis</span><span class="sxs-lookup"><span data-stu-id="02da2-117">Nullable value types</span></span>](../programming-guide/nullable-types/index.md)
