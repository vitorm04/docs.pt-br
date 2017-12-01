---
title: "Como: Executar ações quando um bloco de fluxo de dados recebe dados"
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
- TPL dataflow library, receiving data
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d049d20f5e685096a72857cd18a89688633883c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Como: Executar ações quando um bloco de fluxo de dados recebe dados
*Bloco de fluxo de execução* tipos de chamar um representante fornecido pelo usuário ao receber dados. O <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, e <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> classes são tipos de bloco de fluxo de dados de execução. Você pode usar o `delegate` palavra-chave (`Sub` na [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), <xref:System.Action%601>, <xref:System.Func%602>, ou uma expressão lambda ao fornecer uma função de trabalho para um bloco de fluxo de dados de execução. Este documento descreve como usar <xref:System.Func%602> e as expressões lambda para executar a ação em blocos de execução.  
  
> [!TIP]
>  A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o fluxo de dados para ler um arquivo do disco e calcula o número de bytes no arquivo que são iguais a zero. Ele usa <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> para ler o arquivo e o número de zero bytes de computação e <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> para imprimir o número de zero bytes para o console. O <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objeto Especifica uma <xref:System.Func%602> objeto para executar o trabalho quando os blocos de recebem dados. O <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto usa uma expressão lambda para o número de zero bytes de leitura de impressão para o console.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Embora você possa fornecer uma expressão lambda para uma <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> do objeto, este exemplo usa <xref:System.Func%602> para habilitar outro código usar o `CountBytes` método. O <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto usa uma expressão lambda porque o trabalho a ser executada é específico para essa tarefa e não é provavelmente serão úteis de outro código. Para obter mais informações sobre como as expressões lambda funcionam na biblioteca de tarefas paralelas, consulte [expressões Lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 A seção Resumo de tipos delegar no [fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) documento resume os tipos de delegado que você pode fornecer aos <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, e <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objetos. A tabela também especifica se o tipo de delegado opera de forma síncrona ou assíncrona.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Copie o código de exemplo e cole-o em um projeto do Visual Studio ou colá-lo em um arquivo chamado `DataflowExecutionBlocks.cs` (`DataflowExecutionBlocks.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), e, em seguida, execute o seguinte comando em uma janela de Prompt de comando do Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.vb**  
  
## <a name="robust-programming"></a>Programação robusta  
 Este exemplo fornece um delegado do tipo <xref:System.Func%602> para o <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objeto para executar a tarefa do bloco de fluxo de dados de forma síncrona. Para habilitar o bloco de fluxo de dados para se comportar de forma assíncrona, fornecer um representante do tipo <xref:System.Func%601> para o bloco de fluxo de dados. Quando um bloco de fluxo de dados se comporta de forma assíncrona, a tarefa do bloco de fluxo de dados é concluído somente quando retornado <xref:System.Threading.Tasks.Task%601> objeto for concluída. O exemplo a seguir modifica o `CountBytes` método e usa o [async](~/docs/csharp/language-reference/keywords/async.md) e [await](~/docs/csharp/language-reference/keywords/await.md) operadores ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) e [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) para computar de forma assíncrona o número total de bytes que são zero em que o arquivo fornecido. O <xref:System.IO.FileStream.ReadAsync%2A> método executa operações de leitura do arquivo de forma assíncrona.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Você também pode usar expressões lambda assíncronas para executar a ação em um bloco de fluxo de dados de execução. O exemplo a seguir modifica o <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objeto que é usado no exemplo anterior para que ele usa uma expressão lambda para executar o trabalho de forma assíncrona.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
