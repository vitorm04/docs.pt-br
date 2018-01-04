---
title: "Como implementar um formulário que use uma operação em segundo plano"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2172611fc92257490cfe4ed0b020270aefb3638
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="202fa-102">Como implementar um formulário que use uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="202fa-102">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="202fa-103">O programa de exemplo a seguir cria um formulário que calcula números Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="202fa-103">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="202fa-104">O cálculo é executado em um thread que está separado do thread da interface do usuário, para que a interface do usuário continuará a ser executado sem atrasos conforme o cálculo prossegue.</span><span class="sxs-lookup"><span data-stu-id="202fa-104">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="202fa-105">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="202fa-105">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="202fa-106">Consulte também [passo a passo: Implementando um formulário que usa uma operação em segundo plano](http://msdn.microsoft.com/library/b2zk6580\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="202fa-106">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](http://msdn.microsoft.com/library/b2zk6580\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="202fa-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="202fa-107">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="202fa-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="202fa-108">Compiling the Code</span></span>  
 <span data-ttu-id="202fa-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="202fa-109">This example requires:</span></span>  
  
-   <span data-ttu-id="202fa-110">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="202fa-110">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="202fa-111">Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="202fa-111">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="202fa-112">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="202fa-112">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="202fa-113">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="202fa-113">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="202fa-114">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="202fa-114">Robust Programming</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="202fa-115">O uso de multithreading de qualquer tipo pode expor o computador a bugs muito sérios e complexos.</span><span class="sxs-lookup"><span data-stu-id="202fa-115">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="202fa-116">Consulte as [Melhores práticas de threading gerenciado](../../../../docs/standard/threading/managed-threading-best-practices.md) antes de implementar qualquer solução que use multithreading.</span><span class="sxs-lookup"><span data-stu-id="202fa-116">Consult the [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="202fa-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="202fa-117">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [<span data-ttu-id="202fa-118">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="202fa-118">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="202fa-119">Práticas recomendadas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="202fa-119">Managed Threading Best Practices</span></span>](../../../../docs/standard/threading/managed-threading-best-practices.md)
