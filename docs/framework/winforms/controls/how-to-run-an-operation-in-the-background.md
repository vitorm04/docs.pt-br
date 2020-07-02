---
title: Como executar uma operação no plano de fundo
description: Saiba como usar a classe BackgroundWorker para executar uma operação de Windows Forms demorada em segundo plano.
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
ms.openlocfilehash: 6b2a97f5acf1e906dfe141aee62e99a4e50dca9f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621568"
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="794c9-103">Como executar uma operação no plano de fundo</span><span class="sxs-lookup"><span data-stu-id="794c9-103">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="794c9-104">Se você tiver uma operação que levará muito tempo para ser concluída e não quiser causar atrasos na interface do usuário, poderá usar a <xref:System.ComponentModel.BackgroundWorker> classe para executar a operação em outro thread.</span><span class="sxs-lookup"><span data-stu-id="794c9-104">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="794c9-105">O exemplo de código a seguir mostra como executar uma operação demorada em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="794c9-105">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="794c9-106">O formulário tem botões **Iniciar** e **Cancelar** .</span><span class="sxs-lookup"><span data-stu-id="794c9-106">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="794c9-107">Clique no botão **Iniciar** para executar uma operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="794c9-107">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="794c9-108">Clique no botão **Cancelar** para interromper uma operação assíncrona em execução.</span><span class="sxs-lookup"><span data-stu-id="794c9-108">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="794c9-109">O resultado de cada operação é exibido em um <xref:System.Windows.Forms.MessageBox> .</span><span class="sxs-lookup"><span data-stu-id="794c9-109">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="794c9-110">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="794c9-110">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="794c9-111">Consulte também [a explicação: executando uma operação em segundo plano](walkthrough-running-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="794c9-111">Also see [Walkthrough: Running an Operation in the Background](walkthrough-running-an-operation-in-the-background.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="794c9-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="794c9-112">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="794c9-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="794c9-113">Compiling the Code</span></span>  
 <span data-ttu-id="794c9-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="794c9-114">This example requires:</span></span>  
  
- <span data-ttu-id="794c9-115">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="794c9-115">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="794c9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="794c9-116">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="794c9-117">Como implementar um formulário que usa uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="794c9-117">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="794c9-118">Componente BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="794c9-118">BackgroundWorker Component</span></span>](backgroundworker-component.md)
