---
title: 'Como: Escrever mensagens em um bloco de fluxo de dados e ler mensagens de um bloco de fluxo de dados'
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
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bf609a8c350a44fc802cce0ec10693431bbf4f42
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Como: Escrever mensagens em um bloco de fluxo de dados e ler mensagens de um bloco de fluxo de dados
Este documento descreve como usar a biblioteca de fluxo de dados TPL para escrever mensagens e ler mensagens em um bloco de fluxo de dados. A biblioteca de fluxo de dados TPL fornece métodos síncronos e assíncronos para gravar mensagens para e leitura de um bloco de fluxo de dados. Este documento usa o <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> classe. O <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> classe armazena mensagens no buffer e se comporta como ambos os uma fonte de mensagem e como um destino de mensagem.  
  
> [!TIP]
>  A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Gravar e ler de um bloco de fluxo de dados de forma síncrona  
 O exemplo a seguir usa o <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> método para gravar um <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> blocos de fluxo de dados e o <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> método de leitura do mesmo objeto.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Você também pode usar o <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> método de leitura de um bloco de fluxo de dados, conforme mostrado no exemplo a seguir. O <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> método não bloqueia o thread atual e é útil quando você ocasionalmente sondar dados.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Porque o <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> método age de forma síncrona, o <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objeto nos exemplos anteriores recebe todos os dados antes do segundo loop lê os dados. O exemplo a seguir estende o primeiro exemplo usando <xref:System.Threading.Tasks.Parallel.Invoke%2A> para ler e gravar simultaneamente para o bloco de mensagens. Porque <xref:System.Threading.Tasks.Parallel.Invoke%2A> executa ações simultaneamente, os valores não são gravados para o <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objeto em qualquer ordem específica.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Gravar e ler de um bloco de fluxo de dados de forma assíncrona  
 O exemplo a seguir usa o <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> método para gravar de maneira assíncrona para um <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objeto e o <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> método assincronamente leiam o mesmo objeto. Este exemplo usa o [async](~/docs/csharp/language-reference/keywords/async.md) e [await](~/docs/csharp/language-reference/keywords/await.md) operadores ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) e [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) no Visual Basic) para enviar dados e ler de forma assíncrona dados do bloco de destino. O <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> método é útil quando você deve habilitar um bloco de fluxo de dados para adiar mensagens. O <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> método é útil quando você deseja agir sobre dados quando dados se torna disponíveis. Para obter mais informações sobre como as mensagens são propagadas entre blocos de mensagens, consulte a seção passagem de mensagens em [fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md).  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Um exemplo completo  
 O exemplo a seguir mostra o código completo para este documento.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Copie o código de exemplo e cole-o em um projeto do Visual Studio ou colá-lo em um arquivo chamado `DataflowReadWrite.cs` (`DataflowReadWrite.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), e, em seguida, execute o seguinte comando em uma janela de Prompt de comando do Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**  
  
## <a name="next-steps"></a>Próximas etapas  
 Este exemplo mostra como ler e gravar diretamente em um bloco de mensagens. Você também pode conectar os blocos de fluxo de dados para o formulário *pipelines*, que são sequências lineares dos blocos de fluxo de dados, ou *redes*, que são gráficos de blocos de fluxo de dados. Em uma rede ou pipeline, origens propagam dados assincronamente para destinos assim que os dados ficam disponíveis. Para obter um exemplo que cria um pipeline de fluxo de dados básico, consulte [passo a passo: Criando um Pipeline de fluxo de dados](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md). Para obter um exemplo que cria uma rede de fluxo de dados mais complexa, consulte [passo a passo: usando o fluxo de dados em um aplicativo do Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
