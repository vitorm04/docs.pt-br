---
title: "Como manipular exceções em loops paralelos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 98e822bc148bbe5879a9ff0b7c47e9124b68e612
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="95f30-102">Como manipular exceções em loops paralelos</span><span class="sxs-lookup"><span data-stu-id="95f30-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="95f30-103">O <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> sobrecargas não tem qualquer mecanismo especial para lidar com exceções que podem ser geradas.</span><span class="sxs-lookup"><span data-stu-id="95f30-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="95f30-104">Nesse sentido, assemelham regular `for` e `foreach` loops (`For` e `For Each` no Visual Basic); uma exceção sem tratamento faz com que o loop encerrar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="95f30-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate immediately.</span></span>  
  
 <span data-ttu-id="95f30-105">Quando você adicionar sua própria lógica de tratamento de exceção para paralelo loops, tratar o caso em que exceções semelhantes podem ser geradas em vários threads ao mesmo tempo e o caso em que uma exceção lançada em um thread faz com que outra exceção seja lançada em outro thread.</span><span class="sxs-lookup"><span data-stu-id="95f30-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="95f30-106">Você pode manipular ambos os casos, quebra automática de todas as exceções de loop em um <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="95f30-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="95f30-107">O exemplo a seguir mostra uma abordagem possível.</span><span class="sxs-lookup"><span data-stu-id="95f30-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95f30-108">Quando "Apenas meu código" estiver habilitado, o Visual Studio, em alguns casos quebrar a linha que lança a exceção e exibir uma mensagem de erro que diz "exceção não tratada pelo código do usuário".</span><span class="sxs-lookup"><span data-stu-id="95f30-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="95f30-109">Esse erro é benigno.</span><span class="sxs-lookup"><span data-stu-id="95f30-109">This error is benign.</span></span> <span data-ttu-id="95f30-110">Você pode pressionar F5 para continuar a partir dele e ver o comportamento de tratamento de exceção que é demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="95f30-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="95f30-111">Para impedir que o Visual Studio quebra no primeiro erro, simplesmente desmarque a caixa de seleção "Apenas meu código" em **ferramentas, opções, depuração, geral**.</span><span class="sxs-lookup"><span data-stu-id="95f30-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95f30-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95f30-112">Example</span></span>  
 <span data-ttu-id="95f30-113">Neste exemplo, todas as exceções são detectadas e, em seguida, encapsuladas em um <xref:System.AggregateException?displayProperty=nameWithType> que é gerado.</span><span class="sxs-lookup"><span data-stu-id="95f30-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="95f30-114">O chamador pode decidir quais exceções para tratar.</span><span class="sxs-lookup"><span data-stu-id="95f30-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="95f30-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95f30-115">See Also</span></span>  
 [<span data-ttu-id="95f30-116">Paralelismo de dados</span><span class="sxs-lookup"><span data-stu-id="95f30-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="95f30-117">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="95f30-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
