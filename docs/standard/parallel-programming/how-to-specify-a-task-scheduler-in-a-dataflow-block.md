---
title: 'Como: especificar um agendador de tarefas em um bloco de fluxo de dados'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 681c0f1f918c8991ed2544189488d1ea25547834
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345840"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a><span data-ttu-id="11b66-102">Como: especificar um agendador de tarefas em um bloco de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="11b66-102">How to: Specify a Task Scheduler in a Dataflow Block</span></span>
<span data-ttu-id="11b66-103">Este documento demonstra como associar um agendador de tarefas específico quando você usa o fluxo de dados em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11b66-103">This document demonstrates how to associate a specific task scheduler when you use dataflow in your application.</span></span> <span data-ttu-id="11b66-104">O exemplo usa a classe <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> em um aplicativo Windows Forms para mostrar quando as tarefas do leitor estão ativas e quando uma tarefa de gravador está ativa.</span><span class="sxs-lookup"><span data-stu-id="11b66-104">The example uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> class in a Windows Forms application to show when reader tasks are active and when a writer task is active.</span></span> <span data-ttu-id="11b66-105">Ele também usa o método <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> para permitir que um bloco de fluxo de dados seja executado no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="11b66-105">It also uses the <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method to enable a dataflow block to run on the user-interface thread.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="11b66-106">Para criar o aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11b66-106">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="11b66-107">Crie um projeto de **aplicativo do Windows Forms** em C# ou em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="11b66-107">Create a Visual C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="11b66-108">Nas etapas a seguir, o projeto é denominado `WriterReadersWinForms`.</span><span class="sxs-lookup"><span data-stu-id="11b66-108">In the following steps, the project is named `WriterReadersWinForms`.</span></span>  
  
2. <span data-ttu-id="11b66-109">No designer de formulários do formulário principal, Form1.cs (Form1.vb para Visual Basic), adicione quatro controles <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="11b66-109">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add four <xref:System.Windows.Forms.CheckBox> controls.</span></span> <span data-ttu-id="11b66-110">Configure a propriedade <xref:System.Windows.Forms.Control.Text%2A> do **Leitor 1** como `checkBox1`, **Leitor 2** como `checkBox2`, **Leitor 3** como `checkBox3`, e **Gravador** como `checkBox4`.</span><span class="sxs-lookup"><span data-stu-id="11b66-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to **Reader 1** for `checkBox1`, **Reader 2** for `checkBox2`, **Reader 3** for `checkBox3`, and **Writer** for `checkBox4`.</span></span> <span data-ttu-id="11b66-111">Defina a propriedade <xref:System.Windows.Forms.Control.Enabled%2A> de cada controle como `False`.</span><span class="sxs-lookup"><span data-stu-id="11b66-111">Set the <xref:System.Windows.Forms.Control.Enabled%2A> property for each control to `False`.</span></span>  
  
3. <span data-ttu-id="11b66-112">Adicione um controle <xref:System.Windows.Forms.Timer> ao formulário.</span><span class="sxs-lookup"><span data-stu-id="11b66-112">Add a <xref:System.Windows.Forms.Timer> control to the form.</span></span> <span data-ttu-id="11b66-113">Defina a propriedade <xref:System.Windows.Forms.Timer.Interval%2A> como `2500`.</span><span class="sxs-lookup"><span data-stu-id="11b66-113">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `2500`.</span></span>  
  
## <a name="adding-dataflow-functionality"></a><span data-ttu-id="11b66-114">Adicionar funcionalidade de fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="11b66-114">Adding Dataflow Functionality</span></span>  
 <span data-ttu-id="11b66-115">Esta seção descreve como criar os blocos de fluxo de dados que participam do aplicativo e como associar cada um com um agendador de tarefas.</span><span class="sxs-lookup"><span data-stu-id="11b66-115">This section describes how to create the dataflow blocks that participate in the application and how to associate each one with a task scheduler.</span></span>  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a><span data-ttu-id="11b66-116">Para adicionar a funcionalidade de fluxo de dados ao aplicativo</span><span class="sxs-lookup"><span data-stu-id="11b66-116">To Add Dataflow Functionality to the Application</span></span>  
  
1. <span data-ttu-id="11b66-117">No seu projeto, adicione uma referência a System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="11b66-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="11b66-118">Verifique se o Form1.cs (Form1.vb para Visual Basic) contém as seguintes instruções `using` (`Imports` em Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="11b66-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. <span data-ttu-id="11b66-119">Adicione um membro de dados <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> à classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="11b66-119">Add a <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> data member to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. <span data-ttu-id="11b66-120">No construtor `Form1`, após a chamada para `InitializeComponent`, crie um objeto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> que alterna o estado de objetos <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="11b66-120">In the `Form1` constructor, after the call to `InitializeComponent`, create an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that toggles the state of <xref:System.Windows.Forms.CheckBox> objects.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. <span data-ttu-id="11b66-121">No construtor `Form1`, crie um objeto <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> e quatro objetos <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, um objeto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> para cada objeto <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="11b66-121">In the `Form1` constructor, create a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object and four <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objects, one <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object for each <xref:System.Windows.Forms.CheckBox> object.</span></span> <span data-ttu-id="11b66-122">Para cada objeto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, especifique um objeto <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> que tenha a propriedade <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> definida na propriedade <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> para os leitores e a propriedade <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> para o gravador.</span><span class="sxs-lookup"><span data-stu-id="11b66-122">For each <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object, specify a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> property for the readers, and the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> property for the writer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. <span data-ttu-id="11b66-123">No construtor `Form1`, inicie o objeto <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="11b66-123">In the `Form1` constructor, start the <xref:System.Windows.Forms.Timer> object.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. <span data-ttu-id="11b66-124">No designer de formulários, para o formulário principal, crie um manipulador de eventos para o evento <xref:System.Windows.Forms.Timer.Tick> para o temporizador.</span><span class="sxs-lookup"><span data-stu-id="11b66-124">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
8. <span data-ttu-id="11b66-125">Implemente o evento <xref:System.Windows.Forms.Timer.Tick> para o temporizador.</span><span class="sxs-lookup"><span data-stu-id="11b66-125">Implement the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 <span data-ttu-id="11b66-126">Como o bloco de fluxo de dados `toggleCheckBox` atua na interface do usuário, é importante que essa ação ocorra no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="11b66-126">Because the `toggleCheckBox` dataflow block acts on the user interface, it is important that this action occur on the user-interface thread.</span></span> <span data-ttu-id="11b66-127">Para isso, durante a construção, esse objeto fornece um objeto <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> que possui a propriedade <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> definida para <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="11b66-127">To accomplish this, during construction this object provides a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="11b66-128">O método <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> cria um objeto <xref:System.Threading.Tasks.TaskScheduler> que executa o trabalho no contexto de sincronização atual.</span><span class="sxs-lookup"><span data-stu-id="11b66-128">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="11b66-129">Como o construtor `Form1` é chamado do thread de interface do usuário, as ações para os blocos de fluxo de dados `toggleCheckBox` também são executadas no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="11b66-129">Because the `Form1` constructor is called from the user-interface thread, the action for the `toggleCheckBox` dataflow block also runs on the user-interface thread.</span></span>  
  
 <span data-ttu-id="11b66-130">Este exemplo também usa a classe <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> para permitir que alguns blocos de fluxo de dados atuem simultaneamente e outro bloco de fluxo de dados atue de forma exclusiva em relação a todos os outros blocos de fluxo de dados que são executados no mesmo objeto <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>.</span><span class="sxs-lookup"><span data-stu-id="11b66-130">This example also uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> class to enable some dataflow blocks to act concurrently, and another dataflow block to act exclusive with respect to all other dataflow blocks that run on the same <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object.</span></span> <span data-ttu-id="11b66-131">Essa técnica é útil quando vários blocos de fluxo de dados compartilham um recurso e alguns exigem acesso exclusivo a esse recurso, pois elimina o requisito de sincronizar manualmente o acesso a esse recurso.</span><span class="sxs-lookup"><span data-stu-id="11b66-131">This technique is useful when multiple dataflow blocks share a resource and some require exclusive access to that resource, because it eliminates the requirement to manually synchronize access to that resource.</span></span> <span data-ttu-id="11b66-132">A eliminação da sincronização manual pode tornar o código mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="11b66-132">The elimination of manual synchronization can make code more efficient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11b66-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="11b66-133">Example</span></span>  
 <span data-ttu-id="11b66-134">O exemplo a seguir mostra o código completo para o Form1.cs (Form1.vb para Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="11b66-134">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="11b66-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11b66-135">See also</span></span>

- [<span data-ttu-id="11b66-136">Fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="11b66-136">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
