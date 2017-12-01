---
title: "Como: Implementar um padrão de fluxo de dados de produtor-consumidor"
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
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1aba08e8364d8a21f70ab480d58041115a4849e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Como: Implementar um padrão de fluxo de dados de produtor-consumidor
Este documento descreve como usar a biblioteca de fluxo de dados TPL para implementar um padrão de produtor-consumidor. Nesse padrão, o *produtor* envia mensagens para um bloco de mensagens e o *consumidor* lê mensagens esse bloco.  
  
> [!TIP]
>  A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra um modelo básico de produtor-consumidor que usa o fluxo de dados. O `Produce` método grava matrizes que contêm aleatórios bytes de dados para um <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> objeto e o `Consume` método lê bytes de um <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> objeto. Ao agir no <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> e <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfaces, em vez de seus tipos derivados, você pode escrever o código reutilizável que pode agir em uma variedade de tipos de bloco de fluxo de dados. Este exemplo usa o <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> classe. Porque o <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> classe atua como uma fonte ambos os blocos e como um bloco de destino, o produtor e consumidor podem usar um objeto compartilhado para transferir dados.  
  
 O `Produce` chamadas de método de <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> método em um loop de forma síncrona gravar dados para o bloco de destino. Após o `Produce` método grava todos os dados para o bloco de destino, ele chama o <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> método para indicar que o bloco nunca terá dados adicionais disponíveis. O `Consume` método usa o [async](~/docs/csharp/language-reference/keywords/async.md) e [await](~/docs/csharp/language-reference/keywords/await.md) operadores ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) e [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) para computar de forma assíncrona o número total de bytes recebidos do <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objeto. Para agir de forma assíncrona, o `Consume` chamadas de método de <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> método para receber uma notificação quando o bloco de origem tem dados disponíveis e quando o bloco de código-fonte nunca terá dados adicionais disponíveis.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Copie o código de exemplo e cole-o em um projeto do Visual Studio ou colá-lo em um arquivo chamado `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), e, em seguida, execute o seguinte comando em uma janela de Prompt de comando do Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**  
  
## <a name="robust-programming"></a>Programação robusta  
 Este exemplo usa apenas um consumidor para processar os dados de origem. Se você tiver vários consumidores em seu aplicativo, use o <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> método para ler dados do bloco de código-fonte, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 O <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> método retorna `False` quando não há dados disponíveis. Quando vários consumidores devem acessar simultaneamente o bloco de código-fonte, esse mecanismo garante que dados ainda estão disponíveis após a chamada a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
