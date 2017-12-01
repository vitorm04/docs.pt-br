---
title: 'Como: Especificar o grau de paralelismo em um bloco de fluxo de dados'
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
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1ccd64a9acbc75a30984719671af2dc7dda6922
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Como: Especificar o grau de paralelismo em um bloco de fluxo de dados
Este documento descreve como definir o <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> propriedade para habilitar um bloco de fluxo de dados de execução processar mais de uma mensagem de uma vez. Isso é útil quando você tiver um bloco de fluxo de dados que executa um cálculo de longa duração e pode se beneficiar de processamento de mensagens em paralelo. Este exemplo usa o <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> de classe para executar várias operações de fluxo de dados simultaneamente; no entanto, você pode especificar o grau máximo de paralelismo em qualquer um dos tipos de bloco de execução predefinido que fornece a biblioteca de fluxo de dados TPL, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, e <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.  
  
> [!TIP]
>  A biblioteca de fluxo de dados TPL (o <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir executa dois cálculos de fluxo de dados e imprime o tempo decorrido que é necessário para cada cálculo. O primeiro cálculo Especifica um grau máximo de paralelismo de 1, que é o padrão. Um grau máximo de paralelismo de 1 faz com que o bloco de fluxo de dados processar mensagens em série. A computação da segunda lembra primeiro, exceto que ela especifica um grau máximo de paralelismo é igual ao número de processadores disponíveis. Isso permite que o bloco de fluxo de dados executar várias operações em paralelo.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Copie o código de exemplo e cole-o em um projeto do Visual Studio ou colá-lo em um arquivo chamado `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), e, em seguida, execute o seguinte comando em uma janela de Prompt de comando do Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**  
  
## <a name="robust-programming"></a>Programação robusta  
 Por padrão, cada bloco de fluxo de dados predefinidos propaga mensagens na ordem em que as mensagens são recebidas.  Embora várias mensagens são processadas simultaneamente quando você especificar um grau máximo de paralelismo é maior que 1, eles ainda são propagados na ordem em que são recebidos.  
  
 Porque o <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> propriedade representa o grau máximo de paralelismo, o bloco de fluxo de dados pode executar com um grau de paralelismo menor do que você especificar. O bloco de fluxo de dados pode usar o menor grau de paralelismo para atender aos seus requisitos funcionais ou devido a uma falta de recursos do sistema disponíveis. Um bloco de fluxo de dados nunca escolhe um maior grau de paralelismo que você especificar.  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
