---
title: "Explicação passo a passo: Criando um tipo de bloco de fluxo de dados personalizado"
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
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 809b21fa6e1470890011604792d849998dd03ede
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>Explicação passo a passo: Criando um tipo de bloco de fluxo de dados personalizado
Embora a biblioteca de fluxo de dados TPL fornece vários tipos de bloco de fluxo de dados que permitem uma variedade de funcionalidade, você também pode criar tipos de bloco personalizado. Este documento descreve como criar um tipo de bloco de fluxo de dados que implementa o comportamento personalizado.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Leitura [fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) antes de ler este documento.  
  
> [!TIP]
>  A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.  
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Definindo o bloco de fluxo de janela deslizante  
 Considere um aplicativo de fluxo de dados que exige que os valores de entrada ser armazenado em buffer e, em seguida, a saída de uma maneira de janela deslizante. Por exemplo, para os valores de entrada {0, 1, 2, 3, 4, 5} e um tamanho de janela de três, um bloco de fluxo de janela deslizante produz as matrizes de saída {0, 1, 2}, {1, 2, 3}, {2, 3, 4} e {3, 4, 5}. As seções a seguir descrevem duas maneiras de criar um tipo de bloco de fluxo de dados que implementa este comportamento personalizado. A primeira técnica usa o <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> método combinar a funcionalidade de um <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objeto e um <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> bloco propagador de um objeto. A segunda técnica define uma classe que deriva de <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> e combina a funcionalidade existente para executar o comportamento personalizado.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Usando a encapsular o método para definir o bloco de fluxo de janela deslizante  
 O exemplo a seguir usa o <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> método para criar um bloco de propagador de uma origem e um destino. Um bloco de propagador permite que um bloco de origem e um bloco de destino para atuar como um destinatário e remetente de dados.  
  
 Essa técnica é útil quando você precisar de funcionalidade personalizada do fluxo de dados, mas você não precisa de um tipo que fornece os campos, propriedades ou métodos adicionais.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Derivando de IPropagatorBlock para definir o bloco de fluxo de janela deslizante  
 A exemplo a seguir mostra o `SlidingWindowBlock` classe. Essa classe é derivada de <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> para que possa agir como uma origem e um destino de dados. Como no exemplo anterior, a `SlidingWindowBlock` classe se baseia em tipos de bloco de fluxo de dados existente. No entanto, o `SlidingWindowBlock` classe também implementa os métodos necessários para o <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, e <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> interfaces. Encaminhar todos esses métodos funcionam para os membros de tipo de bloco predefinidos de fluxo de dados. Por exemplo, o `Post` método transfere o trabalho para o `m_target` membro de dados, que também é um <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> objeto.  
  
 Essa técnica é útil quando você precisar da funcionalidade de fluxo de dados personalizados e também requerem um tipo que fornece os campos, propriedades ou métodos adicionais. Por exemplo, o `SlidingWindowBlock` classe também deriva de <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> para que possa fornecer a <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> e <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> métodos. O `SlidingWindowBlock` classe também demonstra a extensibilidade, fornecendo o `WindowSize` propriedade, que recupera o número de elementos na janela deslizante.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>O Exemplo Completo  
 O exemplo a seguir mostra o código completo para este passo a passo. Ele também demonstra como usar os dois blocos de janela deslizante em um método que grava o bloco, lê-lo e imprime os resultados para o console.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Copie o código de exemplo e cole-o em um projeto do Visual Studio ou colá-lo em um arquivo chamado `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) e, em seguida, execute o seguinte comando em uma janela de Prompt de comando do Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**  
  
## <a name="next-steps"></a>Próximas etapas  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
