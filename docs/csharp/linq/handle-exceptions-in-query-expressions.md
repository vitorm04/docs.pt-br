---
title: Tratar exceções em expressões de consulta (LINQ em C#)
description: Saiba como tratar exceções em expressões de consulta LINQ em C#.
ms.date: 12/1/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 344d11129814516a5ed3dcf0eba73a5ecbb96981
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37403833"
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="6bade-103">Tratar exceções em expressões de consulta</span><span class="sxs-lookup"><span data-stu-id="6bade-103">Handle exceptions in query expressions</span></span>

<span data-ttu-id="6bade-104">É possível chamar qualquer método no contexto de uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="6bade-104">It's possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="6bade-105">No entanto, é recomendável que você evite chamar qualquer método em uma expressão de consulta que possa criar um efeito colateral, como modificar o conteúdo da fonte de dados ou gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="6bade-105">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="6bade-106">Este exemplo mostra como evitar exceções ao chamar métodos em uma expressão de consulta, sem violar as diretrizes gerais sobre tratamento de exceção do .NET.</span><span class="sxs-lookup"><span data-stu-id="6bade-106">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET guidelines on exception handling.</span></span> <span data-ttu-id="6bade-107">Essas diretrizes declaram que é aceitável capturar uma exceção específica quando você entende por que ela é gerada em um determinado contexto.</span><span class="sxs-lookup"><span data-stu-id="6bade-107">Those guidelines state that it's acceptable to catch a specific exception when you understand why it's thrown in a given context.</span></span> <span data-ttu-id="6bade-108">Para obter mais informações, consulte [Melhores práticas para exceções](../../standard/exceptions/best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="6bade-108">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>

<span data-ttu-id="6bade-109">O último exemplo mostra como tratar os casos em que é necessário lançar uma exceção durante a execução de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="6bade-109">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>

## <a name="example"></a><span data-ttu-id="6bade-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6bade-110">Example</span></span>

<span data-ttu-id="6bade-111">O exemplo a seguir mostra como mover o código de tratamento de exceção para fora de uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="6bade-111">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="6bade-112">Isso só é possível quando o método não depende de nenhuma variável que seja local para a consulta.</span><span class="sxs-lookup"><span data-stu-id="6bade-112">This is only possible when the method does not depend on any variables local to the query.</span></span>

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a><span data-ttu-id="6bade-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6bade-113">Example</span></span>

<span data-ttu-id="6bade-114">Em alguns casos, a melhor resposta para uma exceção que é lançada de dentro de uma consulta poderá ser a interrupção imediata da execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="6bade-114">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="6bade-115">O exemplo a seguir mostra como tratar exceções que podem ser geradas de dentro de um corpo de consulta.</span><span class="sxs-lookup"><span data-stu-id="6bade-115">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="6bade-116">Suponha que `SomeMethodThatMightThrow` possa causar uma exceção que exija que a execução da consulta seja interrompida.</span><span class="sxs-lookup"><span data-stu-id="6bade-116">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>

<span data-ttu-id="6bade-117">Observe que o bloco `try` inclui o loop `foreach` e não a própria consulta.</span><span class="sxs-lookup"><span data-stu-id="6bade-117">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="6bade-118">Isso ocorre porque o loop `foreach` é o ponto em que a consulta é realmente executada.</span><span class="sxs-lookup"><span data-stu-id="6bade-118">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="6bade-119">Para obter mais informações, consulte [Introdução a consultas LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="6bade-119">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="6bade-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bade-120">See also</span></span>

[<span data-ttu-id="6bade-121">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="6bade-121">Language Integrated Query (LINQ)</span></span>](index.md)  
