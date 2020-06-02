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
ms.openlocfilehash: 87405425e85ed16d10b3e8b382c6e414fff10ddf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278526"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="34fbe-102">Como: Tratar exceções em loops paralelos</span><span class="sxs-lookup"><span data-stu-id="34fbe-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="34fbe-103">As sobrecargas <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> não têm nenhum mecanismo especial para lidar com exceções que podem ocorrer.</span><span class="sxs-lookup"><span data-stu-id="34fbe-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="34fbe-104">Nesse sentido, eles se assemelham a regulares `for` e `foreach` loops ( `For` e `For Each` em Visual Basic); uma exceção sem tratamento faz com que o loop seja encerrado assim que todas as iterações em execução no momento sejam concluídas.</span><span class="sxs-lookup"><span data-stu-id="34fbe-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate as soon as all currently running iterations finish.</span></span>
  
 <span data-ttu-id="34fbe-105">Quando você adiciona sua própria lógica de tratamento de exceção a loops paralelos, trate o caso em que exceções semelhantes podem ser geradas em vários threads ao mesmo tempo e o caso em que uma exceção lançada em um thread faz com que outra exceção seja lançada em outro thread.</span><span class="sxs-lookup"><span data-stu-id="34fbe-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="34fbe-106">Você pode manipular ambos os casos encapsulando todas as exceções do loop em um <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="34fbe-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="34fbe-107">O exemplo a seguir mostra uma abordagem possível.</span><span class="sxs-lookup"><span data-stu-id="34fbe-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34fbe-108">Se a opção "Apenas Meu Código" estiver habilitada, o Visual Studio em alguns casos interromperá na linha que lança a exceção e exibirá uma mensagem de erro que diz "exceção não tratada pelo código do usuário".</span><span class="sxs-lookup"><span data-stu-id="34fbe-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="34fbe-109">Esse erro é benigno.</span><span class="sxs-lookup"><span data-stu-id="34fbe-109">This error is benign.</span></span> <span data-ttu-id="34fbe-110">Você pode pressionar F5 para continuar a partir daí e ver o comportamento de tratamento de exceção, demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="34fbe-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="34fbe-111">Para impedir que o Visual Studio seja interrompido no primeiro erro, basta desmarcar a caixa de seleção "Apenas Meu Código" em **Ferramentas, Opções, Depuração, Geral**.</span><span class="sxs-lookup"><span data-stu-id="34fbe-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34fbe-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34fbe-112">Example</span></span>  
 <span data-ttu-id="34fbe-113">Neste exemplo, todas as exceções são detectadas e, em seguida, encapsuladas em uma <xref:System.AggregateException?displayProperty=nameWithType> gerada.</span><span class="sxs-lookup"><span data-stu-id="34fbe-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="34fbe-114">O chamador pode decidir quais exceções tratar.</span><span class="sxs-lookup"><span data-stu-id="34fbe-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="34fbe-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="34fbe-115">See also</span></span>

- [<span data-ttu-id="34fbe-116">Paralelismo de dados</span><span class="sxs-lookup"><span data-stu-id="34fbe-116">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="34fbe-117">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="34fbe-117">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
