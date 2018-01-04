---
title: "Como executar uma operação na tela de fundo"
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
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9a92427310dc36392b35f22e39c1d4ae101db74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="d3ed1-102">Como executar uma operação na tela de fundo</span><span class="sxs-lookup"><span data-stu-id="d3ed1-102">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="d3ed1-103">Se você tiver uma operação que levará algum tempo para ser concluída, e você não deseja causar atrasos em sua interface de usuário, você pode usar o <xref:System.ComponentModel.BackgroundWorker> classe para executar a operação em outro thread.</span><span class="sxs-lookup"><span data-stu-id="d3ed1-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="d3ed1-104">O exemplo de código a seguir mostra como executar uma operação demorada em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d3ed1-104">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="d3ed1-105">O formulário tem **iniciar** e **Cancelar** botões.</span><span class="sxs-lookup"><span data-stu-id="d3ed1-105">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="d3ed1-106">Clique o **iniciar** botão para executar uma operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="d3ed1-106">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="d3ed1-107">Clique o **Cancelar** botão para parar uma operação assíncrona em execução.</span><span class="sxs-lookup"><span data-stu-id="d3ed1-107">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="d3ed1-108">O resultado de cada operação é exibido em um <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="d3ed1-108">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="d3ed1-109">Há um suporte abrangente para esta tarefa em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3ed1-109">There is extensive support for this task in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="d3ed1-110">Consulte também [passo a passo: executando uma operação em segundo plano](http://msdn.microsoft.com/library/ms233672\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="d3ed1-110">Also see [Walkthrough: Running an Operation in the Background](http://msdn.microsoft.com/library/ms233672\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3ed1-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3ed1-111">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d3ed1-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="d3ed1-112">Compiling the Code</span></span>  
 <span data-ttu-id="d3ed1-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="d3ed1-113">This example requires:</span></span>  
  
-   <span data-ttu-id="d3ed1-114">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="d3ed1-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="d3ed1-115">Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d3ed1-115">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="d3ed1-116">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="d3ed1-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="d3ed1-117">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="d3ed1-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ed1-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3ed1-118">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [<span data-ttu-id="d3ed1-119">Como implementar um formulário que usa uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="d3ed1-119">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="d3ed1-120">Componente BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="d3ed1-120">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
