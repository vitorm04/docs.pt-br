---
title: 'Como: Implementar um formulário que usa uma operação em segundo plano'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: 9ace37b1c79ff2e5cd06fce08557dc6cdf2fcc11
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261292"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="4e634-102">Como: Implementar um formulário que usa uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="4e634-102">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="4e634-103">O programa de exemplo a seguir cria um formulário que calcula números Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="4e634-103">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="4e634-104">O cálculo é executado em um thread que está separado do thread da interface do usuário, portanto, a interface do usuário continuará a ser executado sem atrasos conforme o cálculo prossegue.</span><span class="sxs-lookup"><span data-stu-id="4e634-104">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="4e634-105">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4e634-105">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="4e634-106">Consulte também [passo a passo: Implementando um formulário que usa uma operação em segundo plano](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="4e634-106">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e634-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e634-107">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4e634-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="4e634-108">Compiling the Code</span></span>  
 <span data-ttu-id="4e634-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="4e634-109">This example requires:</span></span>  
  
-   <span data-ttu-id="4e634-110">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="4e634-110">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="4e634-111">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4e634-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4e634-112">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="4e634-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4e634-113">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="4e634-113">Robust Programming</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="4e634-114">O uso de multithreading de qualquer tipo pode expor o computador a bugs muito sérios e complexos.</span><span class="sxs-lookup"><span data-stu-id="4e634-114">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="4e634-115">Consulte as [Melhores práticas de threading gerenciado](../../../../docs/standard/threading/managed-threading-best-practices.md) antes de implementar qualquer solução que use multithreading.</span><span class="sxs-lookup"><span data-stu-id="4e634-115">Consult the [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e634-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e634-116">See also</span></span>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="4e634-117">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="4e634-117">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="4e634-118">Práticas recomendadas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="4e634-118">Managed Threading Best Practices</span></span>](../../../../docs/standard/threading/managed-threading-best-practices.md)
