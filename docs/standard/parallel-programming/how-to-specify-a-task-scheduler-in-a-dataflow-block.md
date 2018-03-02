---
title: 'Como: Especificar um agendador de tarefas em um bloco de fluxo de dados'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 592b6c5c92a2c752fa0d2694cdb477423b15eb0d
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Como: Especificar um agendador de tarefas em um bloco de fluxo de dados
Este documento demonstra como associar um agendador de tarefas específico quando você usa o fluxo de dados em seu aplicativo. O exemplo usa a classe <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> em um aplicativo Windows Forms para mostrar quando as tarefas do leitor estão ativas e quando uma tarefa de gravador está ativa. Ele também usa o método <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> para permitir que um bloco de fluxo de dados seja executado no thread da interface do usuário.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Para criar o aplicativo do Windows Forms  
  
1.  Crie um projeto [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] ou Visual Basic  **para o aplicativo Windows Forms**. Nas etapas a seguir, o projeto é denominado `WriterReadersWinForms`.  
  
2.  No designer de formulários para o formulário principal, Form1.cs (Form1.vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), adicione quatro controles <xref:System.Windows.Forms.CheckBox>. Configure a propriedade <xref:System.Windows.Forms.Control.Text%2A> do **Leitor 1** como `checkBox1`, **Leitor 2** como `checkBox2`, **Leitor 3** como `checkBox3`, e **Gravador** como `checkBox4`. Defina a propriedade <xref:System.Windows.Forms.Control.Enabled%2A> de cada controle como `False`.  
  
3.  Adicione um controle <xref:System.Windows.Forms.Timer> ao formulário. Defina a propriedade <xref:System.Windows.Forms.Timer.Interval%2A> como `2500`.  
  
## <a name="adding-dataflow-functionality"></a>Adicionar funcionalidade de fluxo de dados  
 Esta seção descreve como criar os blocos de fluxo de dados que participam do aplicativo e como associar cada um com um agendador de tarefas.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Para adicionar a funcionalidade de fluxo de dados ao aplicativo  
  
1.  No seu projeto, adicione uma referência a System.Threading.Tasks.Dataflow.dll.  
  
2.  O Form1 (Form1.vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) deve conter as seguintes instruções `using` (`Imports` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3.  Adicione um membro de dados <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> à classe `Form1`.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4.  No construtor `Form1`, após a chamada para `InitializeComponent`, crie um objeto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> que alterna o estado de objetos <xref:System.Windows.Forms.CheckBox>.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5.  No construtor `Form1`, crie um objeto <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> e quatro objetos <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, um objeto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> para cada objeto <xref:System.Windows.Forms.CheckBox>. Para cada objeto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, especifique um objeto <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> que tenha a propriedade <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> definida na propriedade <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> para os leitores e a propriedade <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> para o gravador.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6.  No construtor `Form1`, inicie o objeto <xref:System.Windows.Forms.Timer>.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7.  No designer de formulários, para o formulário principal, crie um manipulador de eventos para o evento <xref:System.Windows.Forms.Timer.Tick> para o temporizador.  
  
8.  Implemente o evento <xref:System.Windows.Forms.Timer.Tick> para o temporizador.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Como o bloco de fluxo de dados `toggleCheckBox` atua na interface do usuário, é importante que essa ação ocorra no thread da interface do usuário. Para isso, durante a construção, esse objeto fornece um objeto <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> que possui a propriedade <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> definida para <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. O método <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> cria um objeto <xref:System.Threading.Tasks.TaskScheduler> que executa o trabalho no contexto de sincronização atual. Como o construtor `Form1` é chamado do thread de interface do usuário, as ações para os blocos de fluxo de dados `toggleCheckBox` também são executadas no thread da interface do usuário.  
  
 Este exemplo também usa a classe <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> para permitir que alguns blocos de fluxo de dados atuem simultaneamente e outro bloco de fluxo de dados atue de forma exclusiva em relação a todos os outros blocos de fluxo de dados que são executados no mesmo objeto <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>. Essa técnica é útil quando vários blocos de fluxo de dados compartilham um recurso e alguns exigem acesso exclusivo a esse recurso, pois elimina o requisito de sincronizar manualmente o acesso a esse recurso. A eliminação da sincronização manual pode tornar o código mais eficiente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o código completo para Form1.cs (Form1.vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
