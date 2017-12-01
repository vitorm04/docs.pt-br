---
title: "Como: Usar JoinBlock para ler dados de várias fontes"
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
- TPL dataflow library, joining blocks in
- dataflow blocks, joining in TPL
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41445e4874b94809840ecf9ebda6f27ccc955c9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Como: Usar JoinBlock para ler dados de várias fontes
Este documento explica como usar o <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> classe para executar uma operação quando os dados estão disponíveis de várias fontes. Ele também demonstra como usar o modo não greedy para habilitar vários blocos de junção compartilhar uma fonte de dados com mais eficiência.  
  
> [!TIP]
>  A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define três tipos de recursos, `NetworkResource`, `FileResource`, e `MemoryResource`e executa operações quando os recursos estiverem disponíveis. Este exemplo requer uma `NetworkResource` e `MemoryResource` par para realizar a primeira operação e um `FileResource` e `MemoryResource` par para realizar a operação de segundo. Para habilitar essas operações ocorrem quando todos os recursos necessários estão disponíveis, este exemplo usa o <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> classe. Quando um <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objeto recebe dados de todas as origens, ele propaga esses dados ao destino, que neste exemplo é um <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto. Ambos <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> leem objetos de um pool compartilhado de `MemoryResource` objetos.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Para habilitar o uso eficiente do pool compartilhado de `MemoryResource` objetos, este exemplo especifica um <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> objeto que tem o <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> propriedade definida como `False` criar <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objetos que atuam no modo não greedy. Um bloco de junção não greedy adia todas as mensagens recebidas até que um esteja disponível em cada origem. Se qualquer uma das mensagens adiadas foram aprovados pelo outro bloco, bloco de junção reinicia o processo. Modo não greedy permite que os blocos de junção que compartilham um ou mais blocos de código-fonte para acelerar o andamento enquanto esperam os outros blocos de dados. Neste exemplo, se um `MemoryResource` objeto é adicionado para o `memoryResources` pool, a primeira associação bloco para receber sua segunda fonte de dados pode tornar o progresso. Se usar o modo greedy neste exemplo, o que é o padrão, um bloco de junção pode levar a `MemoryResource` do objeto e aguarde até que o segundo recurso se torne disponível. No entanto, se o bloco de junção tem sua segunda fonte de dados disponível, ele não pode fazer progresso de porque o `MemoryResource` objeto tiver sido tomado por outro bloco de junção.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Copie o código de exemplo e cole-o em um projeto do Visual Studio ou colá-lo em um arquivo chamado `DataflowNonGreedyJoin.cs` (`DataflowNonGreedyJoin.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), e, em seguida, execute o seguinte comando em uma janela de Prompt de comando do Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.vb**  
  
## <a name="robust-programming"></a>Programação robusta  
 O uso de junções não greedy também pode ajudar a evitar o deadlock em seu aplicativo. Em um aplicativo de software, *deadlock* ocorre quando dois ou mais processos cada mantenha um recurso e mutuamente Aguarde até que outro processo liberar algum outro recurso. Considere um aplicativo que define duas <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objetos. Os dois objetos leem dados de dois blocos de código-fonte compartilhado. No modo greedy, se lê de um bloco de junção da primeira fonte e o segundo bloco de junção lê da fonte de segundo, o aplicativo pode bloqueio porque ambos os blocos de junção mutuamente Aguarde até que o outro para liberar seus recursos. No modo não greedy, cada bloco de junção leituras de suas fontes somente quando todos os dados estão disponíveis e, portanto, o risco de deadlock é eliminado.  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
