---
title: 'Como: Desvincular blocos de fluxo de dados'
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
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41f1b83fab6ff44e69ac2f010f70e6e254341f5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-unlink-dataflow-blocks"></a>Como: Desvincular blocos de fluxo de dados
Este documento descreve como desvincular um bloco de fluxo de dados de destino de sua origem.  
  
> [!TIP]
>  A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria três <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objetos, cada um dos que chama o `TrySolution` método para calcular um valor. Este exemplo requer apenas o resultado da primeira chamada para `TrySolution` para concluir.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Para receber o valor do primeiro <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objeto termina, este exemplo define o `ReceiveFromAny(T)` método. O `ReceiveFromAny(T)` método aceita uma matriz de <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objetos e links de cada um desses objetos para um <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objeto. Quando você usa o <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> método para vincular um bloco de fluxo de dados de origem para um bloco de destino, a origem propaga mensagens para o destino, conforme os dados ficarão disponíveis. Porque o <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> classe aceita somente a primeira mensagem que é oferecida, o `ReceiveFromAny(T)` método produz o resultado ao chamar o <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> método. Isso produz a primeira mensagem é oferecida para o <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objeto. O <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> método tem uma versão sobrecarregada que leva um <xref:System.Boolean> parâmetro `unlinkAfterOne` que, quando ele é definido como `True`, instrui o bloco de código-fonte para desvincular de destino depois que o destino recebe uma mensagem da fonte de. É importante para o <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objeto para desvincular de suas fontes porque a relação entre a matriz de fontes e o <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objeto não é mais necessário após a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objeto recebe uma mensagem.  
  
 Para habilitar as chamadas restantes para `TrySolution` termine depois que um deles computa um valor, o `TrySolution` leva um <xref:System.Threading.CancellationToken> objeto cancelado após a chamada a `ReceiveFromAny(T)` retorna. O <xref:System.Threading.SpinWait.SpinUntil%2A> método retorna quando isso <xref:System.Threading.CancellationToken> objeto é cancelado.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Copie o código de exemplo e cole-o em um projeto do Visual Studio ou colá-lo em um arquivo chamado `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), e, em seguida, execute o seguinte comando em uma janela de Prompt de comando do Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**  
  
## <a name="robust-programming"></a>Programação robusta  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
