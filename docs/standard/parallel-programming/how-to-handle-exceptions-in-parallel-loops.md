---
title: 'Como: Tratar exceções em loops paralelos'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ffc522b2ab13ae2098c01e6716e00aef5bef8e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962493"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="ad039-102">Como: Tratar exceções em loops paralelos</span><span class="sxs-lookup"><span data-stu-id="ad039-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="ad039-103">As sobrecargas <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> não têm nenhum mecanismo especial para lidar com exceções que podem ocorrer.</span><span class="sxs-lookup"><span data-stu-id="ad039-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="ad039-104">Nesse sentido, elas se assemelham aos loops `for` e `foreach` regulares (`For` e `For Each` no Visual Basic); uma exceção sem tratamento causa o encerramento imediato do loop.</span><span class="sxs-lookup"><span data-stu-id="ad039-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate immediately.</span></span>  
  
 <span data-ttu-id="ad039-105">Quando você adiciona sua própria lógica de tratamento de exceção a loops paralelos, trate o caso em que exceções semelhantes podem ser geradas em vários threads ao mesmo tempo e o caso em que uma exceção lançada em um thread faz com que outra exceção seja lançada em outro thread.</span><span class="sxs-lookup"><span data-stu-id="ad039-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="ad039-106">Você pode manipular ambos os casos encapsulando todas as exceções do loop em um <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ad039-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ad039-107">O exemplo a seguir mostra uma abordagem possível.</span><span class="sxs-lookup"><span data-stu-id="ad039-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad039-108">Se a opção "Apenas Meu Código" estiver habilitada, o Visual Studio em alguns casos interromperá na linha que lança a exceção e exibirá uma mensagem de erro que diz "exceção não tratada pelo código do usuário".</span><span class="sxs-lookup"><span data-stu-id="ad039-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="ad039-109">Esse erro é benigno.</span><span class="sxs-lookup"><span data-stu-id="ad039-109">This error is benign.</span></span> <span data-ttu-id="ad039-110">Você pode pressionar F5 para continuar a partir daí e ver o comportamento de tratamento de exceção, demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ad039-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="ad039-111">Para impedir que o Visual Studio seja interrompido no primeiro erro, basta desmarcar a caixa de seleção "Apenas Meu Código" em **Ferramentas, Opções, Depuração, Geral**.</span><span class="sxs-lookup"><span data-stu-id="ad039-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad039-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ad039-112">Example</span></span>  
 <span data-ttu-id="ad039-113">Neste exemplo, todas as exceções são detectadas e, em seguida, encapsuladas em uma <xref:System.AggregateException?displayProperty=nameWithType> gerada.</span><span class="sxs-lookup"><span data-stu-id="ad039-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="ad039-114">O chamador pode decidir quais exceções tratar.</span><span class="sxs-lookup"><span data-stu-id="ad039-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="ad039-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad039-115">See also</span></span>

- [<span data-ttu-id="ad039-116">Paralelismo de dados</span><span class="sxs-lookup"><span data-stu-id="ad039-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="ad039-117">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="ad039-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
