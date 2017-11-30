---
title: 'Como: Cancelar um bloco de fluxo de dados'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4d6fbde31cd4b4b5d0c6404b8baf23230f2bda77
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="1fb00-102">Como: Cancelar um bloco de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="1fb00-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="1fb00-103">Este documento demonstra como habilitar o cancelamento em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1fb00-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="1fb00-104">Este exemplo usa o Windows Forms para mostrar onde os itens de trabalho estão ativos em um pipeline de fluxo de dados e também os efeitos de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="1fb00-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="1fb00-105">A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1fb00-105">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="1fb00-106">Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.</span><span class="sxs-lookup"><span data-stu-id="1fb00-106">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
### <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="1fb00-107">Para criar o Windows Forms de aplicativo</span><span class="sxs-lookup"><span data-stu-id="1fb00-107">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="1fb00-108">Criar um c# ou Visual Basic **aplicativo do Windows Forms** projeto.</span><span class="sxs-lookup"><span data-stu-id="1fb00-108">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="1fb00-109">As etapas a seguir, o projeto é denominado `CancellationWinForms`.</span><span class="sxs-lookup"><span data-stu-id="1fb00-109">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2.  <span data-ttu-id="1fb00-110">No designer de formulário para o formulário principal, Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), adicione um <xref:System.Windows.Forms.ToolStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="1fb00-110">On the form designer for the main form, Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3.  <span data-ttu-id="1fb00-111">Adicionar um <xref:System.Windows.Forms.ToolStripButton> o controle para o <xref:System.Windows.Forms.ToolStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="1fb00-111">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="1fb00-112">Definir o <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriedade <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> e o <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade **adicionar itens de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="1fb00-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4.  <span data-ttu-id="1fb00-113">Adicionar um segundo <xref:System.Windows.Forms.ToolStripButton> o controle para o <xref:System.Windows.Forms.ToolStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="1fb00-113">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="1fb00-114">Definir o <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriedade <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, o <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade **Cancelar**e o <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> propriedade para `False`.</span><span class="sxs-lookup"><span data-stu-id="1fb00-114">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5.  <span data-ttu-id="1fb00-115">Adicionar quatro <xref:System.Windows.Forms.ToolStripProgressBar> objetos para o <xref:System.Windows.Forms.ToolStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="1fb00-115">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="1fb00-116">Criando o Pipeline de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="1fb00-116">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="1fb00-117">Esta seção descreve como criar o pipeline de fluxo de dados que processa os itens de trabalho e atualiza as barras de progresso.</span><span class="sxs-lookup"><span data-stu-id="1fb00-117">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
#### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="1fb00-118">Para criar o Pipeline de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="1fb00-118">To Create the Dataflow Pipeline</span></span>  
  
1.  <span data-ttu-id="1fb00-119">No seu projeto, adicione uma referência a System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="1fb00-119">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="1fb00-120">Certifique-se de que Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contém o seguinte `using` instruções (`Imports` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="1fb00-120">Ensure that Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contains the following `using` statements (`Imports` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="1fb00-121">Adicionar o `WorkItem` classe como um tipo interno do `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="1fb00-121">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="1fb00-122">Adicionar os seguintes membros de dados para o `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="1fb00-122">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="1fb00-123">Adicione o seguinte método, `CreatePipeline`, para o `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="1fb00-123">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="1fb00-124">Porque o `incrementProgress` e `decrementProgress` blocos agir na interface do usuário de fluxo de dados, é importante que essas ações ocorrem no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1fb00-124">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="1fb00-125">Para fazer isso, durante a construção esses objetos cada fornecem um <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objeto que tem o <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> propriedade definida como <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1fb00-125">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1fb00-126">O <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> método cria um <xref:System.Threading.Tasks.TaskScheduler> objeto que executa o trabalho no contexto de sincronização atual.</span><span class="sxs-lookup"><span data-stu-id="1fb00-126">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="1fb00-127">Porque o `Form1` construtor é chamado do thread de interface do usuário, as ações para o `incrementProgress` e `decrementProgress` blocos de fluxo de dados também é executado no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1fb00-127">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="1fb00-128">Este exemplo define o <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> propriedade quando ele constrói os membros do pipeline.</span><span class="sxs-lookup"><span data-stu-id="1fb00-128">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="1fb00-129">Porque o <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> propriedade permanentemente cancela a execução de bloco de fluxo de dados, o pipeline todo deve ser recriado depois que o usuário cancela a operação e, em seguida, deseja adicionar mais itens de trabalho para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="1fb00-129">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="1fb00-130">Para obter um exemplo que demonstra uma maneira alternativa para cancelar um bloco de fluxo de dados para que outros trabalhos podem ser executados depois que uma operação for cancelada, consulte [passo a passo: usando o fluxo de dados em um aplicativo do Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="1fb00-130">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="1fb00-131">Conectando o Pipeline de fluxo de dados para a Interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1fb00-131">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="1fb00-132">Esta seção descreve como conectar o pipeline de fluxo de dados para a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1fb00-132">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="1fb00-133">O pipeline de criação e adição de itens de trabalho para o pipeline são controlados pelo manipulador de eventos para o **adicionar itens de trabalho** botão.</span><span class="sxs-lookup"><span data-stu-id="1fb00-133">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="1fb00-134">Cancelamento é iniciado com a **Cancelar** botão.</span><span class="sxs-lookup"><span data-stu-id="1fb00-134">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="1fb00-135">Quando o usuário clica em um desses botões, a ação apropriada é iniciada de maneira assíncrona.</span><span class="sxs-lookup"><span data-stu-id="1fb00-135">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
#### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="1fb00-136">Para conectar o Pipeline de fluxo de dados para a Interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1fb00-136">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1.  <span data-ttu-id="1fb00-137">No designer de formulário para o formulário principal, crie um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para o **adicionar itens de trabalho** botão.</span><span class="sxs-lookup"><span data-stu-id="1fb00-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2.  <span data-ttu-id="1fb00-138">Implementar o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para o **adicionar itens de trabalho** botão.</span><span class="sxs-lookup"><span data-stu-id="1fb00-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  <span data-ttu-id="1fb00-139">No designer de formulário para o formulário principal, crie um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> manipulador de eventos para o **Cancelar** botão.</span><span class="sxs-lookup"><span data-stu-id="1fb00-139">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="1fb00-140">Implementar o <xref:System.Windows.Forms.ToolStripItem.Click> manipulador de eventos para o **Cancelar** botão.</span><span class="sxs-lookup"><span data-stu-id="1fb00-140">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="1fb00-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1fb00-141">Example</span></span>  
 <span data-ttu-id="1fb00-142">O exemplo a seguir mostra o código completo para Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="1fb00-142">The following example shows the complete code for Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="1fb00-143">A ilustração a seguir mostra o aplicativo em execução.</span><span class="sxs-lookup"><span data-stu-id="1fb00-143">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="1fb00-144">![Aplicativo do Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="1fb00-144">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1fb00-145">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="1fb00-145">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb00-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1fb00-146">See Also</span></span>  
 [<span data-ttu-id="1fb00-147">Fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="1fb00-147">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
