---
title: "Explicação passo a passo: Criando um pipeline de fluxo de dados"
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
- dataflow pipelines, creating with TPL
- Task Parallel Library, dataflows
- TPL dataflow library, creating dataflow pipeline
ms.assetid: 69308f82-aa22-4ac5-833d-e748533b58e8
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d63fb872382bfc0a3ba3b8637c7357ab65c58fbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a>Explicação passo a passo: Criando um pipeline de fluxo de dados
Embora você possa usar o <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>, e <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> métodos para receber mensagens da origem blocos, você também pode conectar blocos de mensagens para formar um *pipeline de fluxo de dados*. Um pipeline de fluxo de dados é uma série de componentes, ou *blocos de fluxo de dados*, cada uma delas executa uma tarefa específica que contribui para um objetivo maior. Todos os blocos de fluxo de dados em um pipeline de fluxo de dados executa o trabalho quando ele recebe uma mensagem de outro bloco de fluxo de dados. Uma analogia para isso é uma linha de montagem para fabricação automóvel. Como cada veículo passa por meio da linha de assembly, uma estação monta o quadro, o outro instala o mecanismo e assim por diante. Como uma linha de montagem permite vários veículos a serem montados ao mesmo tempo, ele fornece melhor taxa de transferência que montar veículos completos um por vez.  
  
> [!TIP]
>  A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.  
  
 Este documento demonstra um pipeline de fluxo de dados que baixa o catálogo de *Ilíada de Homer* de um site da Web e pesquisas de texto para correspondência de palavras individuais com as palavras que inversa caracteres da primeira palavra. A formação do pipeline de fluxo de dados neste documento consiste das seguintes etapas:  
  
1.  Crie os blocos de fluxo de dados que participam no pipeline.  
  
2.  Conecte cada bloco de fluxo de dados para o próximo bloco no pipeline. Cada bloco recebe como entrada a saída do bloco anterior no pipeline.  
  
3.  Para cada bloco de fluxo de dados, crie uma tarefa de continuação que define o próximo bloco para o estado concluído após a conclusão do bloco anterior.  
  
4.  Enviar dados para o início do pipeline.  
  
5.  Marca o início do pipeline como concluído.  
  
6.  Aguarde até que o pipeline concluir todo o trabalho.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Leitura [fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) antes de começar este passo a passo.  
  
## <a name="creating-a-console-application"></a>Criando um aplicativo de Console  
 Em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], crie um [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] ou [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] o projeto de aplicativo de Console. Adicione uma referência a System.Threading.Tasks.Dataflow.dll.  
  
 Como alternativa, crie um arquivo e nomeie- `ReverseWords.cs` (`ReverseWords.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), e, em seguida, execute o seguinte comando em uma janela de Prompt de comando do Visual Studio para compilar o projeto.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll ReverseWords.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll ReverseWords.vb**  
  
 Adicione o seguinte código ao seu projeto para criar o aplicativo básico.  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a>Criar blocos de fluxo de dados  
 Adicione o seguinte código para o `Main` método para criar os blocos de fluxo de dados que participam no pipeline. A tabela a seguir resume a função de cada membro do pipeline.  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|Membro|Tipo|Descrição|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Baixa o texto de catálogo da Web.|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Separa o texto de catálogo em uma matriz de palavras.|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Remove a palavras curtas da palavra de matriz, pedidos as palavras resultantes em ordem alfabética e removem duplicatas.|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|Localiza todas as palavras da coleção de matriz de word filtrado cujo inverso também ocorre na matriz de word.|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Exibe palavras e o inverso correspondente para o console.|  
  
 Embora você pode combinar várias etapas no pipeline de fluxo de dados neste exemplo em uma única etapa, o exemplo ilustra o conceito de composição de várias tarefas de fluxo de dados independente para executar uma tarefa maior. O exemplo usa <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> para habilitar cada membro do pipeline executar uma operação em seus dados de entrada e enviar os resultados para a próxima etapa no pipeline. O `findReversedWords` membro do pipeline é um <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> porque ele produz várias saídas independentes para cada entrada. A parte final do pipeline, `printReversedWords`, é um <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> porque ele executa uma ação em sua entrada e produz um resultado.  
  
## <a name="forming-the-pipeline"></a>Cria o Pipeline  
 Adicione o código a seguir para se conectar a cada bloco para o próximo bloco no pipeline.  
  
 Quando você chama o <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> método para se conectar a um bloco de fluxo de dados de origem para um bloco de fluxo de dados de destino, o bloco de fluxo de dados de origem propaga dados para o bloco de destino, como os dados ficarão disponíveis.  
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="creating-the-completion-tasks"></a>Criando as tarefas de conclusão  
 Adicione o código a seguir para habilitar cada bloco de fluxo de dados executar uma ação final após processar todos os dados.  
  
 [!code-csharp[TPLDataflow_Palindromes#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#5)]
 [!code-vb[TPLDataflow_Palindromes#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#5)]  
  
 Para propagar conclusão por meio do pipeline, cada tarefa de conclusão define o próximo bloco de fluxo de dados para o estado concluído. Por exemplo, quando o início do pipeline é definido para o estado concluído, processa quaisquer mensagens em buffer restantes e, em seguida, executa sua tarefa de conclusão, que define o segundo membro de pipeline para o estado concluído. O segundo membro de pipeline por sua vez processa quaisquer mensagens em buffer restantes e, em seguida, executa sua tarefa de conclusão, que define o terceiro membro do pipeline para o estado concluído. Esse processo continua até que todos os membros do pipeline de conclusão. Este exemplo usa o `delegate` palavra-chave (`Function` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) para definir as tarefas de continuação.  
  
## <a name="posting-data-to-the-pipeline"></a>Enviar dados para o Pipeline  
 Adicione o seguinte código para postar a URL do catálogo de *Ilíada de Homer* para o início do pipeline de fluxo de dados.  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 Este exemplo usa <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> de forma síncrona enviar dados para o início do pipeline. Use o <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> método quando você assincronamente deve enviar dados para um nó de fluxo de dados.  
  
## <a name="completing-pipeline-activity"></a>Concluir a atividade de Pipeline  
 Adicione o seguinte código para marcar o início do pipeline como concluído. O início do pipeline executa sua tarefa de continuação após processar em buffer todas as mensagens. Esta tarefa de continuação propaga o estado concluído por meio do pipeline.  
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 Este exemplo envia uma URL por meio do pipeline de fluxo de dados a ser processado. Se você enviar mais de uma entrada por meio de um pipeline, chame o <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> método depois que você enviar todas as entradas. Você pode omitir essa etapa se seu aplicativo não tem nenhum ponto bem definido em que dados não estão mais disponíveis ou o aplicativo não precisa aguardar o término do pipeline.  
  
## <a name="waiting-for-the-pipeline-to-finish"></a>Aguardando o término do Pipeline  
 Adicione o seguinte código para aguardar o término do pipeline. Como este exemplo usa as tarefas de continuação para propagar conclusão por meio do pipeline, a operação geral é concluída quando a conclusão da parte final do pipeline.  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 Você pode aguardar a conclusão do fluxo de dados de qualquer thread ou de vários threads ao mesmo tempo.  
  
## <a name="the-complete-example"></a>O Exemplo Completo  
 O exemplo a seguir mostra o código completo para este passo a passo.  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a>Próximas etapas  
 Este exemplo envia uma URL para processar por meio do pipeline de fluxo de dados. Se você enviar mais de um valor de entrada por meio de um pipeline, você pode introduzir um formulário de paralelismo em seu aplicativo que é semelhante a como partes podem percorrer uma fábrica de automóvel. Quando o primeiro membro do pipeline envia o resultado para o segundo membro, que pode processar outro item em paralelo, como o segundo membro processa o primeiro resultado.  
  
 O paralelismo é obtido usando pipelines de fluxo de dados é conhecido como *paralelismo em blocos* porque normalmente ele consiste em tarefas maior menor. Você também pode usar uma mais *paralelismo refinado* de tarefas menores de curta execução em um pipeline de fluxo de dados. Neste exemplo, o `findReversedWords` membro do pipeline usa o <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> método para processar vários itens na lista de trabalho em paralelo. O uso de paralelismo refinado em um pipeline de alta granularidade pode melhorar o desempenho geral.  
  
 Você também pode conectar um bloco de fluxo de dados de origem para múltiplos blocos de destino para criar um *rede de fluxo de dados*. A versão sobrecarregada do <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> leva um <xref:System.Predicate%601> objeto que define se o bloco de destino aceita cada mensagem com base em seu valor. A maioria dos tipos de bloco fluxo de dados que agem como fontes de oferecem mensagens para todos os blocos de destino conectados, na ordem em que estavam conectados, até que um dos blocos de aceita essa mensagem. Usando o mecanismo de filtragem, você pode criar sistemas de blocos de fluxo de dados conectada que direcionam determinados dados por meio de um caminho e outros dados por meio de outro caminho. Para obter um exemplo que usa a filtragem para criar uma rede de fluxo de dados, consulte [passo a passo: usando o fluxo de dados em um aplicativo do Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
