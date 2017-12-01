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
# <a name="how-to-cancel-a-dataflow-block"></a>Como: Cancelar um bloco de fluxo de dados
Este documento demonstra como habilitar o cancelamento em seu aplicativo. Este exemplo usa o Windows Forms para mostrar onde os itens de trabalho estão ativos em um pipeline de fluxo de dados e também os efeitos de cancelamento.  
  
> [!TIP]
>  A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.  
  
### <a name="to-create-the-windows-forms-application"></a>Para criar o Windows Forms de aplicativo  
  
1.  Criar um c# ou Visual Basic **aplicativo do Windows Forms** projeto. As etapas a seguir, o projeto é denominado `CancellationWinForms`.  
  
2.  No designer de formulário para o formulário principal, Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), adicione um <xref:System.Windows.Forms.ToolStrip> controle.  
  
3.  Adicionar um <xref:System.Windows.Forms.ToolStripButton> o controle para o <xref:System.Windows.Forms.ToolStrip> controle. Definir o <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriedade <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> e o <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade **adicionar itens de trabalho**.  
  
4.  Adicionar um segundo <xref:System.Windows.Forms.ToolStripButton> o controle para o <xref:System.Windows.Forms.ToolStrip> controle. Definir o <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriedade <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, o <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade **Cancelar**e o <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> propriedade para `False`.  
  
5.  Adicionar quatro <xref:System.Windows.Forms.ToolStripProgressBar> objetos para o <xref:System.Windows.Forms.ToolStrip> controle.  
  
## <a name="creating-the-dataflow-pipeline"></a>Criando o Pipeline de fluxo de dados  
 Esta seção descreve como criar o pipeline de fluxo de dados que processa os itens de trabalho e atualiza as barras de progresso.  
  
#### <a name="to-create-the-dataflow-pipeline"></a>Para criar o Pipeline de fluxo de dados  
  
1.  No seu projeto, adicione uma referência a System.Threading.Tasks.Dataflow.dll.  
  
2.  Certifique-se de que Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contém o seguinte `using` instruções (`Imports` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  Adicionar o `WorkItem` classe como um tipo interno do `Form1` classe.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  Adicionar os seguintes membros de dados para o `Form1` classe.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  Adicione o seguinte método, `CreatePipeline`, para o `Form1` classe.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Porque o `incrementProgress` e `decrementProgress` blocos agir na interface do usuário de fluxo de dados, é importante que essas ações ocorrem no thread da interface do usuário. Para fazer isso, durante a construção esses objetos cada fornecem um <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objeto que tem o <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> propriedade definida como <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. O <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> método cria um <xref:System.Threading.Tasks.TaskScheduler> objeto que executa o trabalho no contexto de sincronização atual. Porque o `Form1` construtor é chamado do thread de interface do usuário, as ações para o `incrementProgress` e `decrementProgress` blocos de fluxo de dados também é executado no thread da interface do usuário.  
  
 Este exemplo define o <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> propriedade quando ele constrói os membros do pipeline. Porque o <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> propriedade permanentemente cancela a execução de bloco de fluxo de dados, o pipeline todo deve ser recriado depois que o usuário cancela a operação e, em seguida, deseja adicionar mais itens de trabalho para o pipeline. Para obter um exemplo que demonstra uma maneira alternativa para cancelar um bloco de fluxo de dados para que outros trabalhos podem ser executados depois que uma operação for cancelada, consulte [passo a passo: usando o fluxo de dados em um aplicativo do Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Conectando o Pipeline de fluxo de dados para a Interface do usuário  
 Esta seção descreve como conectar o pipeline de fluxo de dados para a interface do usuário. O pipeline de criação e adição de itens de trabalho para o pipeline são controlados pelo manipulador de eventos para o **adicionar itens de trabalho** botão. Cancelamento é iniciado com a **Cancelar** botão. Quando o usuário clica em um desses botões, a ação apropriada é iniciada de maneira assíncrona.  
  
#### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Para conectar o Pipeline de fluxo de dados para a Interface do usuário  
  
1.  No designer de formulário para o formulário principal, crie um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para o **adicionar itens de trabalho** botão.  
  
2.  Implementar o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para o **adicionar itens de trabalho** botão.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  No designer de formulário para o formulário principal, crie um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> manipulador de eventos para o **Cancelar** botão.  
  
4.  Implementar o <xref:System.Windows.Forms.ToolStripItem.Click> manipulador de eventos para o **Cancelar** botão.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o código completo para Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 A ilustração a seguir mostra o aplicativo em execução.  
  
 ![Aplicativo do Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  
  
## <a name="robust-programming"></a>Programação robusta  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
