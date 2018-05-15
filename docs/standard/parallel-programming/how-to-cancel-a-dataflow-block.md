---
title: 'Como: Cancelar um bloco de fluxo de dados'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eece4992deecbf30299d6e9e96fa8c2faf16d3ab
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="89364-102">Como: Cancelar um bloco de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="89364-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="89364-103">Este documento mostra como habilitar o cancelamento em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="89364-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="89364-104">Este exemplo usa o Windows Forms para mostrar onde os itens de trabalho estão ativos em um pipeline de fluxo de dados, assim como os efeitos de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="89364-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="89364-105">Para criar o aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89364-105">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="89364-106">Crie um projeto de **aplicativo do Windows Forms** no C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="89364-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="89364-107">Nas etapas a seguir, o projeto é denominado `CancellationWinForms`.</span><span class="sxs-lookup"><span data-stu-id="89364-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2.  <span data-ttu-id="89364-108">No designer de formulários do formulário principal, Form1.cs (Form1.vb para Visual Basic), adicione um controle <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="89364-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3.  <span data-ttu-id="89364-109">Adicione um controle <xref:System.Windows.Forms.ToolStripButton> ao controle <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="89364-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="89364-110">Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> como <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> e a propriedade <xref:System.Windows.Forms.ToolStripItem.Text%2A> como **Adicionar itens de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="89364-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4.  <span data-ttu-id="89364-111">Adicione um segundo controle <xref:System.Windows.Forms.ToolStripButton> ao controle <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="89364-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="89364-112">Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> como <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, a propriedade <xref:System.Windows.Forms.ToolStripItem.Text%2A> como **Cancelar** e a propriedade <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> como `False`.</span><span class="sxs-lookup"><span data-stu-id="89364-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5.  <span data-ttu-id="89364-113">Adicione quatro objetos <xref:System.Windows.Forms.ToolStripProgressBar> ao controle <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="89364-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="89364-114">Criar o Pipeline de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="89364-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="89364-115">Esta seção descreve como criar o pipeline de fluxo de dados que processa os itens de trabalho e atualiza as barras de progresso.</span><span class="sxs-lookup"><span data-stu-id="89364-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="89364-116">Para criar o pipeline de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="89364-116">To Create the Dataflow Pipeline</span></span>  
  
1.  <span data-ttu-id="89364-117">No seu projeto, adicione uma referência a System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="89364-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="89364-118">Verifique se o Form1.cs (Form1.vb para Visual Basic) contém as seguintes instruções `using` (`Imports` em Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="89364-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="89364-119">Adicione a classe `WorkItem` como um tipo interno da classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="89364-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="89364-120">Adicione os membros de dados a seguir à classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="89364-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="89364-121">Adicione o seguinte método, `CreatePipeline`, à classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="89364-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="89364-122">Como os blocos de fluxo de dados `incrementProgress` e `decrementProgress` atuam na interface do usuário, é importante que essas ações ocorram no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="89364-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="89364-123">Para isso, durante a construção cada objeto fornece um objeto <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> cuja propriedade <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> está definida como <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="89364-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="89364-124">O método <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> cria um objeto <xref:System.Threading.Tasks.TaskScheduler> que executa o trabalho no contexto de sincronização atual.</span><span class="sxs-lookup"><span data-stu-id="89364-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="89364-125">Como o construtor `Form1` é chamado do thread de interface do usuário, as ações para os blocos de fluxo de dados `incrementProgress` e `decrementProgress` também são executadas no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="89364-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="89364-126">Este exemplo define a propriedade <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> ao construir os membros do pipeline.</span><span class="sxs-lookup"><span data-stu-id="89364-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="89364-127">Como a propriedade <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> cancela permanentemente a execução do bloco de fluxo de dados, o pipeline inteiro deve ser recriado depois que o usuário cancela a operação e, em seguida, deseja adicionar mais itens de trabalho ao pipeline.</span><span class="sxs-lookup"><span data-stu-id="89364-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="89364-128">Veja um exemplo que demonstra uma maneira alternativa de cancelar um bloco de fluxo de dados para que outros trabalhos sejam executados após uma operação ser cancelada no [Passo a passo: usando o fluxo de dados em um aplicativo do Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="89364-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="89364-129">Conectar o Pipeline de fluxo de dados à interface do usuário</span><span class="sxs-lookup"><span data-stu-id="89364-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="89364-130">Esta seção descreve como conectar o pipeline de fluxo de dados à interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="89364-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="89364-131">O manipulador de eventos controla a criação do pipeline e a adição de itens de trabalho ao pipeline para o botão**Adicionar itens de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="89364-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="89364-132">O cancelamento é iniciado pelo botão **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="89364-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="89364-133">Quando o usuário clica em um desses botões, a ação apropriada é iniciada de maneira assíncrona.</span><span class="sxs-lookup"><span data-stu-id="89364-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="89364-134">Para conectar o Pipeline de fluxo de dados à interface do usuário</span><span class="sxs-lookup"><span data-stu-id="89364-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1.  <span data-ttu-id="89364-135">No designer de formulários, para o formulário principal, crie um manipulador de eventos para o evento <xref:System.Windows.Forms.ToolStripItem.Click> para o botão **Adicionar itens de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="89364-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2.  <span data-ttu-id="89364-136">Implante o evento <xref:System.Windows.Forms.ToolStripItem.Click> para o botão **Adicionar itens de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="89364-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  <span data-ttu-id="89364-137">No designer de formulários, para o formulário principal, crie um manipulador de eventos <xref:System.Windows.Forms.ToolStripItem.Click> para o botão **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="89364-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="89364-138">Implante o manipulador de eventos <xref:System.Windows.Forms.ToolStripItem.Click> para o botão **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="89364-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="89364-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89364-139">Example</span></span>  
 <span data-ttu-id="89364-140">O exemplo a seguir mostra o código completo para o Form1.cs (Form1.vb para Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="89364-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="89364-141">A ilustração a seguir mostra o aplicativo em execução.</span><span class="sxs-lookup"><span data-stu-id="89364-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="89364-142">![Aplicativo do Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="89364-142">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="89364-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89364-143">See Also</span></span>  
 [<span data-ttu-id="89364-144">Fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="89364-144">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
