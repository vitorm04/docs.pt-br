---
title: Como manipular exceções em uma consulta PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40b98e01d6c34fb01a1f508f2ea52309f2f7938b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668750"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="51b45-102">Como manipular exceções em uma consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="51b45-102">How to: Handle Exceptions in a PLINQ Query</span></span>
<span data-ttu-id="51b45-103">O primeiro exemplo neste tópico mostra como tratar o <xref:System.AggregateException?displayProperty=nameWithType> que pode ser gerado de uma consulta PLINQ ao ser executado.</span><span class="sxs-lookup"><span data-stu-id="51b45-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="51b45-104">O segundo exemplo mostra como colocar blocos try-catch em representantes, o mais próximo possível de onde a exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="51b45-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="51b45-105">Dessa forma, você pode capturá-los assim que eles ocorrerem e, possivelmente, continuar a execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="51b45-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="51b45-106">Quando as exceções tiverem permissão de emergirem novamente para o thread de associação, então será possível que uma consulta continue a processar alguns itens após a geração da exceção.</span><span class="sxs-lookup"><span data-stu-id="51b45-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>  
  
 <span data-ttu-id="51b45-107">Em alguns casos em que PLINQ volta à execução sequencial e ocorre uma exceção, a exceção pode ser propagada diretamente e não é encapsulada em um <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="51b45-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="51b45-108">Além disso, <xref:System.Threading.ThreadAbortException>s sempre são propagados diretamente.</span><span class="sxs-lookup"><span data-stu-id="51b45-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51b45-109">Se a opção "Apenas Meu Código" estiver habilitada, o Visual Studio interromperá na linha que gerou a exceção e exibirá a mensagem de erro "exceção não tratada pelo código do usuário".</span><span class="sxs-lookup"><span data-stu-id="51b45-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="51b45-110">Esse erro é benigno.</span><span class="sxs-lookup"><span data-stu-id="51b45-110">This error is benign.</span></span> <span data-ttu-id="51b45-111">Você pode pressionar F5 para continuar a partir daí e ver o comportamento de tratamento de exceção, demonstrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="51b45-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="51b45-112">Para impedir que o Visual Studio seja interrompido no primeiro erro, basta desmarcar a caixa de seleção "Apenas Meu Código" em **Ferramentas, Opções, Depuração, Geral**.</span><span class="sxs-lookup"><span data-stu-id="51b45-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="51b45-113">Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente.</span><span class="sxs-lookup"><span data-stu-id="51b45-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="51b45-114">Para saber mais sobre agilização, confira [Noções básicas sobre agilização no PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="51b45-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51b45-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51b45-115">Example</span></span>  
 <span data-ttu-id="51b45-116">Este exemplo mostra como colocar os blocos try-catch no código que executa a consulta para capturar quaisquer <xref:System.AggregateException?displayProperty=nameWithType>s que são gerados.</span><span class="sxs-lookup"><span data-stu-id="51b45-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 <span data-ttu-id="51b45-117">Neste exemplo, a consulta não pode continuar depois que a exceção é gerada.</span><span class="sxs-lookup"><span data-stu-id="51b45-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="51b45-118">Quando o código do aplicativo captura a exceção, PLINQ já interrompeu a consulta em todos os threads.</span><span class="sxs-lookup"><span data-stu-id="51b45-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51b45-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51b45-119">Example</span></span>  
 <span data-ttu-id="51b45-120">O exemplo a seguir mostra como inserir um bloco try-catch em um representante para que seja possível capturar uma exceção e continuar com a execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="51b45-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="51b45-121">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="51b45-121">Compiling the Code</span></span>  
  
-   <span data-ttu-id="51b45-122">Para compilar e executar esses exemplos, copie-os para o Exemplo de Dados do PLINQ e chame o método do Principal.</span><span class="sxs-lookup"><span data-stu-id="51b45-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="51b45-123">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="51b45-123">Robust Programming</span></span>  
 <span data-ttu-id="51b45-124">Não captura uma exceção, a menos que você saiba como tratá-la para que o estado do programa não sejam corrompido.</span><span class="sxs-lookup"><span data-stu-id="51b45-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b45-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51b45-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>  
- [<span data-ttu-id="51b45-126">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="51b45-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
