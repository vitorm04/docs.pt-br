---
title: 'Como: adicionar instruções de rastreamento ao código de um aplicativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 626e9823bbf7d379a21ae353a9189485259f3c42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948018"
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="102dc-102">Como: adicionar instruções de rastreamento ao código de um aplicativo</span><span class="sxs-lookup"><span data-stu-id="102dc-102">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="102dc-103">Os métodos usados com mais frequência para rastreamento são os métodos para gravar a saída em ouvintes: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**e **Fail**.</span><span class="sxs-lookup"><span data-stu-id="102dc-103">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="102dc-104">Esses métodos podem ser divididos em duas categorias: **Grave**, **WriteLine**e reprovam toda a saída de emissão incondicionalmente, enquanto **WriteIf**, **WriteLineIf**e **Assert** testam uma condição booliana e gravam ou não gravam com base no valor da condição.</span><span class="sxs-lookup"><span data-stu-id="102dc-104">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="102dc-105">**WriteIf** e **WriteLineIf** emitirão a saída se a condição for `true` e **Assert** emitirá a saída se a condição for `false`.</span><span class="sxs-lookup"><span data-stu-id="102dc-105">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="102dc-106">Ao criar sua estratégia de rastreamento e depuração, pense em como você deseja que a saída se assemelhe.</span><span class="sxs-lookup"><span data-stu-id="102dc-106">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="102dc-107">Várias instruções **Write** preenchidas com informações não relacionadas criarão um log que é difícil de ser lido.</span><span class="sxs-lookup"><span data-stu-id="102dc-107">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="102dc-108">Por outro lado, o uso de **WriteLine** para colocar instruções relacionadas em linhas separadas pode tornar difícil distinguir quais informações pertencem juntas.</span><span class="sxs-lookup"><span data-stu-id="102dc-108">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="102dc-109">Em geral, use várias instruções **Write** quando desejar combinar informações de várias fontes para criar uma única mensagem informativa e use a instrução **WriteLine** quando desejar criar uma única mensagem completa.</span><span class="sxs-lookup"><span data-stu-id="102dc-109">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="102dc-110">Para gravar uma linha completa</span><span class="sxs-lookup"><span data-stu-id="102dc-110">To write a complete line</span></span>  
  
1. <span data-ttu-id="102dc-111">Chame o método <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A>.</span><span class="sxs-lookup"><span data-stu-id="102dc-111">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="102dc-112">Um retorno de carro é acrescentado ao final da mensagem retornada por esse método, de modo que a próxima mensagem retornada por **Write**, **WriteIf**, **WriteLine** ou **WriteLineIf** comece na seguinte linha:</span><span class="sxs-lookup"><span data-stu-id="102dc-112">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,   
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="102dc-113">Para gravar uma linha parcial</span><span class="sxs-lookup"><span data-stu-id="102dc-113">To write a partial line</span></span>  
  
1. <span data-ttu-id="102dc-114">Chame o método <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A>.</span><span class="sxs-lookup"><span data-stu-id="102dc-114">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="102dc-115">A próxima mensagem colocada por uma instrução **Write**, **WriteIf**, **WriteLine** ou **WriteLineIf** começará na mesma linha da mensagem colocada pela instrução **Write** ou **WriteIf**:</span><span class="sxs-lookup"><span data-stu-id="102dc-115">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,   
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="102dc-116">Para verificar se certas condições existem antes ou depois de executar um método</span><span class="sxs-lookup"><span data-stu-id="102dc-116">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1. <span data-ttu-id="102dc-117">Chame o método <xref:System.Diagnostics.Trace.Assert%2A>.</span><span class="sxs-lookup"><span data-stu-id="102dc-117">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="102dc-118">Use **Assert** com o rastreamento e a depuração.</span><span class="sxs-lookup"><span data-stu-id="102dc-118">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="102dc-119">Este exemplo gera a pilha de chamadas para qualquer ouvinte da coleção **Listeners**.</span><span class="sxs-lookup"><span data-stu-id="102dc-119">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="102dc-120">Para obter mais informações, consulte [Declarações em código gerenciado](/visualstudio/debugger/assertions-in-managed-code) e <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="102dc-120">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="102dc-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="102dc-121">See also</span></span>

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="102dc-122">Rastreando e instrumentando aplicativos</span><span class="sxs-lookup"><span data-stu-id="102dc-122">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="102dc-123">Como: Criar, inicializar e configurar opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="102dc-123">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="102dc-124">Opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="102dc-124">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="102dc-125">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="102dc-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
