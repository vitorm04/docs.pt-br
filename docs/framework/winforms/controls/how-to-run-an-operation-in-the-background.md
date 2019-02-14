---
title: 'Como: Executar uma operação em segundo plano'
ms.date: 03/30/2017
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
ms.openlocfilehash: 9702728631f794c0cc8f69a1117da69bc15a0836
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261759"
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="98735-102">Como: Executar uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="98735-102">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="98735-103">Se você tiver uma operação que levará muito tempo para ser concluída, e você não deseja causar atrasos na interface do usuário, você pode usar o <xref:System.ComponentModel.BackgroundWorker> classe para executar a operação em outro thread.</span><span class="sxs-lookup"><span data-stu-id="98735-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="98735-104">O exemplo de código a seguir mostra como executar uma operação demorada em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="98735-104">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="98735-105">O formulário tem **inicie** e **Cancelar** botões.</span><span class="sxs-lookup"><span data-stu-id="98735-105">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="98735-106">Clique o **iniciar** botão para executar uma operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="98735-106">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="98735-107">Clique o **Cancelar** botão para parar uma operação assíncrona em execução.</span><span class="sxs-lookup"><span data-stu-id="98735-107">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="98735-108">O resultado de cada operação é exibido em um <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="98735-108">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="98735-109">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="98735-109">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="98735-110">Consulte também [passo a passo: Executando uma operação em segundo plano](walkthrough-running-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="98735-110">Also see [Walkthrough: Running an Operation in the Background](walkthrough-running-an-operation-in-the-background.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98735-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98735-111">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="98735-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="98735-112">Compiling the Code</span></span>  
 <span data-ttu-id="98735-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="98735-113">This example requires:</span></span>  
  
-   <span data-ttu-id="98735-114">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="98735-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="98735-115">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="98735-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="98735-116">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="98735-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98735-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98735-117">See also</span></span>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="98735-118">Como: Implementar um formulário que usa uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="98735-118">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="98735-119">Componente BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="98735-119">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
