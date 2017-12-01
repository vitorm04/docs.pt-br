---
title: 'Como: Especificar um agendador de tarefas em um bloco de fluxo de dados'
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
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 20faebc8bda3b50c4f762615d84b7a449ae61c6f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Como: Especificar um agendador de tarefas em um bloco de fluxo de dados
Este documento demonstra como associar um agendador de tarefas específica quando você usa o fluxo de dados em seu aplicativo. O exemplo usa o <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> classe em um aplicativo do Windows Forms para mostrar quando as tarefas de leitor estão ativas e quando uma tarefa de gravador está ativa. Ele também usa o <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> método para permitir que um bloco de fluxo de dados ser executado no thread da interface do usuário.  
  
> [!TIP]
>  A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.  
  
### <a name="to-create-the-windows-forms-application"></a>Para criar o Windows Forms de aplicativo  
  
1.  Criar um [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] ou Visual Basic **aplicativo do Windows Forms** projeto. As etapas a seguir, o projeto é denominado `WriterReadersWinForms`.  
  
2.  No designer de formulário para o formulário principal, Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), adicionar quatro <xref:System.Windows.Forms.CheckBox> controles. Definir o <xref:System.Windows.Forms.Control.Text%2A> propriedade **leitor 1** para `checkBox1`, **Reader 2** para `checkBox2`, **leitor 3** para `checkBox3`, e  **Gravador** para `checkBox4`. Definir o <xref:System.Windows.Forms.Control.Enabled%2A> propriedade para cada controle `False`.  
  
3.  Adicionar um <xref:System.Windows.Forms.Timer> controle no formulário. Defina a propriedade <xref:System.Windows.Forms.Timer.Interval%2A> como `2500`.  
  
## <a name="adding-dataflow-functionality"></a>Adicionando funcionalidade de fluxo de dados  
 Esta seção descreve como criar os blocos de fluxo de dados que participam no aplicativo e como associar cada um com um agendador de tarefas.  
  
#### <a name="to-add-dataflow-functionality-to-the-application"></a>Para adicionar a funcionalidade de fluxo de dados para o aplicativo  
  
1.  No seu projeto, adicione uma referência a System.Threading.Tasks.Dataflow.dll.  
  
2.  Certifique-se de que Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contém o seguinte `using` instruções (`Imports` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3.  Adicionar um <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> membro de dados para o `Form1` classe.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4.  No `Form1` construtor, após a chamada a `InitializeComponent`, crie um <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> que alterna o estado do objeto <xref:System.Windows.Forms.CheckBox> objetos.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5.  No `Form1` construtor, criar um <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objeto e quatro <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objetos, um <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto para cada <xref:System.Windows.Forms.CheckBox> objeto. Para cada <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> de objeto, especifique um <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objeto que tem o <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> propriedade definida como o <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> propriedade para os leitores e o <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> propriedade para o gravador.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6.  No `Form1` construtor, iniciar o <xref:System.Windows.Forms.Timer> objeto.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7.  No designer de formulário para o formulário principal, crie um manipulador de eventos para o <xref:System.Windows.Forms.Timer.Tick> evento para o temporizador.  
  
8.  Implementar o <xref:System.Windows.Forms.Timer.Tick> evento para o temporizador.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Porque o `toggleCheckBox` atos de bloco de fluxo de dados na interface do usuário, é importante que essa ação ocorre no thread da interface do usuário. Para fazer isso, durante a construção esse objeto fornece um <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objeto que tem o <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> propriedade definida como <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. O <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> método cria um <xref:System.Threading.Tasks.TaskScheduler> objeto que executa o trabalho no contexto de sincronização atual. Porque o `Form1` construtor é chamado do thread de interface do usuário, a ação para o `toggleCheckBox` bloco de fluxo de dados também é executado no thread da interface do usuário.  
  
 Este exemplo também usa o <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> classe para habilitar alguns blocos de fluxo de dados funcione simultaneamente e outro bloco de fluxo de dados para atuar exclusivo em relação a todos os outros blocos de fluxo de dados que são executados no mesmo <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objeto. Essa técnica é útil quando um recurso de compartilhamento de vários blocos de fluxo de dados e alguns exigem acesso exclusivo para esse recurso, pois elimina a necessidade de sincronizar manualmente o acesso a esse recurso. A eliminação de sincronização manual pode tornar o código mais eficiente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o código completo para Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
