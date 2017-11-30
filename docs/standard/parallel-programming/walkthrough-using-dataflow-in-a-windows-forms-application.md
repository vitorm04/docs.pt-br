---
title: "Explicação passo a passo: Usando um fluxo de dados em um Aplicativo do Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d2775cc99020fd99d6e7d79cdf3e1ffcc3219146
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>Explicação passo a passo: Usando um fluxo de dados em um Aplicativo do Windows Forms
Este documento demonstra como criar uma rede de blocos de fluxo de dados que executam o processamento de imagem em um aplicativo do Windows Forms.  
  
 Este exemplo carrega arquivos de imagem da pasta especificada, cria uma imagem composta e exibe o resultado. O exemplo usa o modelo de fluxo de dados para imagens de rota por meio da rede. No modelo de fluxo de dados, componentes independentes de um programa se comunicar uns com os outros enviando mensagens. Quando um componente recebe uma mensagem, ele executa uma ação e, em seguida, passa o resultado para outro componente. Compare isso com o modelo de fluxo de controle, em que um aplicativo usa estruturas de controle, por exemplo, instruções condicionais, loops e assim por diante, para controlar a ordem das operações em um programa.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Leitura [fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) antes de começar este passo a passo.  
  
> [!TIP]
>  A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.  
 
  
## <a name="sections"></a>Seções  
 Este passo a passo contém as seguintes seções:  
  
-   [Criando o aplicativo Windows Forms](#winforms)  
  
-   [Criar a rede de fluxo de dados](#network)  
  
-   [Conectar-se a rede de fluxo de dados para a Interface do usuário](#ui)  
  
-   [O exemplo completo](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a>Criando o aplicativo Windows Forms  
 Esta seção descreve como criar o aplicativo de Windows Forms básico e adicionar controles ao formulário principal.  
  
#### <a name="to-create-the-windows-forms-application"></a>Para criar o Windows Forms de aplicativo  
  
1.  Em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], crie um [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] ou Visual Basic **aplicativo do Windows Forms** projeto. Neste documento, o projeto é denominado `CompositeImages`.  
  
2.  No designer de formulário para o formulário principal, Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), adicione um <xref:System.Windows.Forms.ToolStrip> controle.  
  
3.  Adicionar um <xref:System.Windows.Forms.ToolStripButton> o controle para o <xref:System.Windows.Forms.ToolStrip> controle. Definir o <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriedade <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> e o <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade **escolher a pasta**.  
  
4.  Adicionar um segundo <xref:System.Windows.Forms.ToolStripButton> o controle para o <xref:System.Windows.Forms.ToolStrip> controle. Definir o <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriedade <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, o <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade **Cancelar**e o <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> propriedade para `False`.  
  
5.  Adicionar uma <xref:System.Windows.Forms.PictureBox> objeto para o formulário principal. Defina a propriedade <xref:System.Windows.Forms.Control.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Fill>.  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>Criar a rede de fluxo de dados  
 Esta seção descreve como criar a rede de fluxo de dados que executa o processamento de imagem.  
  
#### <a name="to-create-the-dataflow-network"></a>Para criar a rede de fluxo de dados  
  
1.  Adicione uma referência a System.Threading.Tasks.Dataflow.dll ao seu projeto.  
  
2.  Certifique-se de que Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contém o seguinte `using` (`Using` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) instruções:  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3.  Adicionar os seguintes membros de dados para o `Form1` classe:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4.  Adicione o seguinte método, `CreateImageProcessingNetwork`, para o `Form1` classe. Esse método cria a rede de processamento de imagem.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5.  Implementar o método de `LoadBitmaps` .  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6.  Implementar o método de `CreateCompositeBitmap` .  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  A versão c# do `CreateCompositeBitmap` método usa ponteiros para habilitar o processamento eficiente do <xref:System.Drawing.Bitmap?displayProperty=nameWithType> objetos. Portanto, você deve habilitar o **permitir código inseguro** opção em seu projeto para usar o [unsafe](~/docs/csharp/language-reference/keywords/unsafe.md) palavra-chave. Para obter mais informações sobre como habilitar o código não seguro em um [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] de projeto, consulte [página de compilação, Designer de projeto (c#)] https://msdn.microsoft.com/library/kb4wyys2).  
  
 A tabela a seguir descreve os membros da rede.  
  
|Membro|Tipo|Descrição|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Usa um caminho de pasta como entrada e produz uma coleção de <xref:System.Drawing.Bitmap> objetos como saída.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Usa uma coleção de <xref:System.Drawing.Bitmap> objetos como entrada e produz um bitmap composto como saída.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Exibe o bitmap composto no formulário.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Exibe uma imagem para indicar que a operação será cancelada e permite que o usuário selecione outra pasta.|  
  
 Para conectar os blocos de fluxo de dados para formar uma rede, este exemplo usa o <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> método. O <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> método contém uma versão sobrecarregada que leva um <xref:System.Predicate%601> objeto que determina se o bloco de destino aceita ou rejeita uma mensagem. Esse mecanismo de filtragem permite que os blocos de mensagens receber apenas determinados valores. Neste exemplo, a rede pode ramificar em uma das duas maneiras. A ramificação principal carrega as imagens de disco, cria uma composição de imagens e exibe essa imagem no formulário. A ramificação alternativa cancela a operação atual. O <xref:System.Predicate%601> objetos permitem que os blocos de fluxo de dados ao longo da ramificação principal para alternar para a ramificação alternativa rejeitando determinadas mensagens. Por exemplo, se o usuário cancela a operação, o bloco de fluxo de dados `createCompositeBitmap` produz `null` (`Nothing` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) como sua saída. O bloco de fluxo de dados `displayCompositeBitmap` rejeita `null` valores de entrada e, portanto, a mensagem é oferecido para `operationCancelled`. O bloco de fluxo de dados `operationCancelled` aceita todas as mensagens e, portanto, exibe uma imagem para indicar que a operação foi cancelada.  
  
 A ilustração a seguir mostra a rede de processamento de imagem.  
  
 ![A rede de processamento de imagem](../../../docs/standard/parallel-programming/media/dataflowwinforms.png "DataflowWinForms")  
  
 Porque o `displayCompositeBitmap` e `operationCancelled` blocos agir na interface do usuário de fluxo de dados, é importante que essas ações ocorrem no thread da interface do usuário. Para fazer isso, durante a construção, esses objetos fornecem um <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objeto que tem o <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> propriedade definida como <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. O <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> método cria um <xref:System.Threading.Tasks.TaskScheduler> objeto que executa o trabalho no contexto de sincronização atual. Porque o `CreateImageProcessingNetwork` método é chamado de manipulador do **Escolher pasta** botão, que é executado na interface do usuário do thread, as ações para o `displayCompositeBitmap` e `operationCancelled` também executar blocos de fluxo de dados no thread de interface do usuário.  
  
 Este exemplo usa um token de cancelamento compartilhados em vez de configuração o <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> propriedade porque o <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> propriedade permanentemente cancela a execução de bloco de fluxo de dados. Um token de cancelamento permite que esse exemplo de reutilizar a mesma rede de fluxo de dados várias vezes, mesmo quando o usuário cancela uma ou mais operações. Para obter um exemplo que usa <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> para cancelar permanentemente a execução de um bloco de fluxo de dados, consulte [como: Cancelar um Dataflow Block](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Conectar-se a rede de fluxo de dados para a Interface do usuário  
 Esta seção descreve como conectar-se a rede de fluxo de dados para a interface do usuário. A criação de uma composição de imagens e o cancelamento da operação iniciadas a partir de **Escolher pasta** e **Cancelar** botões. Quando o usuário escolhe um desses botões, a ação apropriada é iniciada de maneira assíncrona.  
  
#### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Para conectar-se a rede de fluxo de dados para a Interface do usuário  
  
1.  No designer de formulário para o formulário principal, crie um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para o **Escolher pasta** botão.  
  
2.  Implementar o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para o **Escolher pasta** botão.  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3.  No designer de formulário para o formulário principal, crie um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para o **Cancelar** botão.  
  
4.  Implementar o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para o **Cancelar** botão.  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>O Exemplo Completo  
 O exemplo a seguir mostra o código completo para este passo a passo.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 A ilustração a seguir mostra a saída típica para a pasta \Sample Pictures\ comuns.  
  
 ![Aplicativo do Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  
  
## <a name="next-steps"></a>Próximas etapas  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
