---
title: "Tratar exceções em expressões de consulta"
description: "Como tratar exceções em expressões de consulta."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 376bd461bfeb51653471fd374a2215aa15872976
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="6cf9c-104">Tratar exceções em expressões de consulta</span><span class="sxs-lookup"><span data-stu-id="6cf9c-104">Handle exceptions in query expressions</span></span>

<span data-ttu-id="6cf9c-105">É possível chamar qualquer método no contexto de uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-105">It is possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="6cf9c-106">No entanto, é recomendável que você evite chamar qualquer método em uma expressão de consulta que possa criar um efeito colateral, como modificar o conteúdo da fonte de dados ou gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-106">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="6cf9c-107">Este exemplo mostra como evitar gerar exceções ao chamar métodos em uma expressão de consulta, sem violar as diretrizes gerais sobre tratamento de exceção do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-107">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET Framework guidelines on exception handling.</span></span> <span data-ttu-id="6cf9c-108">Essas diretrizes declaram que é aceitável capturar uma exceção específica quando você entende por que ela será lançada em um determinado contexto.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-108">Those guidelines state that it is acceptable to catch a specific exception when you understand why it will be thrown in a given context.</span></span> <span data-ttu-id="6cf9c-109">Para obter mais informações, consulte [Melhores práticas para exceções](../../standard/exceptions/best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="6cf9c-109">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>  
  
 <span data-ttu-id="6cf9c-110">O último exemplo mostra como tratar os casos em que é necessário lançar uma exceção durante a execução de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-110">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cf9c-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6cf9c-111">Example</span></span>  

 <span data-ttu-id="6cf9c-112">O exemplo a seguir mostra como mover o código de tratamento de exceção para fora de uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-112">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="6cf9c-113">Isso só é possível quando o método não depende de nenhuma variável que seja local para a consulta.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-113">This is only possible when the method does not depend on any variables local to the query.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="6cf9c-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6cf9c-114">Example</span></span> 

 <span data-ttu-id="6cf9c-115">Em alguns casos, a melhor resposta para uma exceção que é lançada de dentro de uma consulta poderá ser a interrupção imediata da execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-115">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="6cf9c-116">O exemplo a seguir mostra como tratar exceções que podem ser geradas de dentro de um corpo de consulta.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-116">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="6cf9c-117">Suponha que `SomeMethodThatMightThrow` possa causar uma exceção que exija que a execução da consulta seja interrompida.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-117">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>  
  
 <span data-ttu-id="6cf9c-118">Observe que o bloco `try` inclui o loop `foreach` e não a própria consulta.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-118">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="6cf9c-119">Isso ocorre porque o loop `foreach` é o ponto em que a consulta é realmente executada.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-119">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="6cf9c-120">Para obter mais informações, consulte [Introdução a consultas LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="6cf9c-120">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="6cf9c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cf9c-121">See Also</span></span>  
 [<span data-ttu-id="6cf9c-122">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="6cf9c-122">LINQ query expressions</span></span>](index.md)
