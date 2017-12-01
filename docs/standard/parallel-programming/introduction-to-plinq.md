---
title: "Introdução ao PLINQ"
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
helpviewer_keywords: PLINQ queries, introduction to
ms.assetid: eaa720d8-8999-4eb7-8df5-3c19ca61cad0
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db9c3e16d4a8073fbce636f37490f719dbd93e4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-plinq"></a>Introdução ao PLINQ
## <a name="what-is-a-parallel-query"></a>O que é uma Consulta Paralela?  
 A LINQ (Consulta Integrada à Linguagem) foi introduzida no [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].  Ele apresenta um modelo unificado para consultar qualquer <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> fonte de dados de uma maneira de tipo seguro. Objetos LINQ to é o nome para consultas LINQ que são executados em relação a coleções na memória, como <xref:System.Collections.Generic.List%601> e matrizes. Este artigo pressupõe que você tenha uma compreensão básica de LINQ. Para saber mais, veja [LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 PLINQ (Parallel LINQ) é uma implementação paralela da LINQ padrão. Uma consulta PLINQ, em muitas formas, é semelhante a uma consulta não paralela de LINQ to Objects. Consultas PLINQ, assim como sequencial [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] consultas, operar em qualquer na memória <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601> dados de origem e adiaram execução, o que significa que eles não começar a execução até que a consulta é enumerada. A principal diferença é que a PLINQ tenta fazer uso integral de todos os processadores no sistema. Ela faz isso particionando a fonte de dados em segmentos e então executando a consulta em cada segmento em threads de trabalho separados em paralelo em vários processadores. Em muitos casos, a execução paralela significa que a consulta é executada de forma significativamente mais rápida.  
  
 Por meio da execução paralela, PLINQ pode obter melhorias significativas de desempenho sobre o código herdado para determinados tipos de consultas, geralmente simplesmente adicionando o <xref:System.Linq.ParallelEnumerable.AsParallel%2A> operação à fonte de dados de consulta. No entanto, o paralelismo pode apresentar suas próprias complexidades e nem todas as operações de consulta são executadas mais rapidamente na PLINQ. Na verdade, a paralelização realmente atrasa determinadas consultas. Portanto, você deve compreender como problemas como a classificação afetam consultas paralelas. Para saber mais, veja [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
> [!NOTE]
>  Esta documentação usa expressões lambda para definir representantes na PLINQ. Se você não estiver familiarizado com expressões lambda no C# ou no Visual Basic, veja [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 O restante deste artigo fornece uma visão geral das principais classes PLINQ e discute como criar consultas PLINQ. Cada seção contém links para mais informações e exemplos de código.  
  
## <a name="the-parallelenumerable-class"></a>A Classe ParallelEnumerable  
 O <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> classe expõe quase todas as funcionalidades do PLINQ.  Ele e o restante do <xref:System.Linq?displayProperty=nameWithType> tipos de namespace são compilados no assembly System.Core.dll. Os projetos padrão de C# e do Visual Basic no Visual Studio fazem referência ao assembly e importam o namespace.  
  
 <xref:System.Linq.ParallelEnumerable>inclui implementações de todos os operadores de consulta padrão LINQ para objetos com suporte, embora não haja a tentativa paralelizar a cada um. Se você não estiver familiarizado com a [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)], veja [Introdução a LINQ](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e).  
  
 Além dos operadores de consulta padrão, o <xref:System.Linq.ParallelEnumerable> classe contém um conjunto de métodos que permitem comportamentos específicos para execução paralela. Esses métodos específicos de PLINQ são listados na tabela a seguir.  
  
|Operador ParallelEnumerable|Descrição|  
|---------------------------------|-----------------|  
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|O ponto de entrada para PLINQ. Especifica que o restante da consulta deverá ser paralelizado, se possível.|  
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Especifica que o restante da consulta deve ser executado em sequência, como uma consulta LINQ não paralela.|  
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|Especifica que a PLINQ deve preservar a ordenação da sequência de origem para o restante da consulta, ou até que a ordenação seja alterada, por exemplo, pelo uso de uma cláusula orderby (Order By no Vlsual Basic).|  
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|Especifica que a PLINQ para o restante da consulta não precisa preservar a ordenação da sequência de origem.|  
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|Especifica que a PLINQ deve monitorar periodicamente o estado do token de cancelamento fornecido e cancelar a execução se isso for solicitado.|  
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|Especifica o número máximo de processadores que a PLINQ deve usar para paralelizar a consulta.|  
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|Fornece uma dica sobre como a PLINQ deve, se possível, mesclar resultados paralelos novamente em apenas uma sequência no segmento de consumo.|  
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|Especifica se a PLINQ deve paralelizar a consulta mesmo quando o comportamento padrão for executá-la em sequência.|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Um método de enumeração multithread que, ao contrário de iterar sobre os resultados da consulta, permite que os resultados sejam processados em paralelo sem primeiro mesclar de volta para o thread de consumidor.|  
|sobrecarga de <xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Uma sobrecarga que é exclusiva da PLINQ e permite agregação intermediária em partições de thread local, além de uma função de agregação final para combinar os resultados de todas as partições.|  
  
## <a name="the-opt-in-model"></a>O Modelo de Aceite  
 Quando você escreve uma consulta, escolha PLINQ invocando o <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> método de extensão na fonte de dados, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
 [!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]  
  
 O <xref:System.Linq.ParallelEnumerable.AsParallel%2A> método de extensão associa os operadores de consulta subsequente, nesse caso, `where` e `select`, para o <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> implementações.  
  
## <a name="execution-modes"></a>Modos de Execução  
 Por padrão, a PLINQ é conservadora. Em tempo de execução, a infraestrutura da PLINQ analisa a estrutura geral da consulta. Se for provável que a consulta produza aumentos de velocidade por paralelização, a PLINQ particionará a sequência de origem em tarefas que podem ser executadas simultaneamente. Se não for seguro a paralelização de uma consulta, a PLINQ apenas executa a consulta em sequência. Se a PLINQ tiver a opção de escolher entre um algoritmo paralelo potencialmente caro ou um algoritmo sequencial barato, ela escolherá o algoritmo sequencial, por padrão. Você pode usar o <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> método e o <xref:System.Linq.ParallelExecutionMode?displayProperty=nameWithType> enumeração para instruir o PLINQ para selecionar o algoritmo em paralelo. Isso é útil quando você sabe por meio de testes e medidas que uma determinada consulta é executada mais rapidamente em paralelo. Para saber mais, veja [Como especificar o modo de execução em PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
## <a name="degree-of-parallelism"></a>Grau de Paralelismo  
 Por padrão, o PLINQ usa todos os processadores no computador host. Você pode instruir o PLINQ usar não mais do que um número especificado de processadores usando a <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A> método. Isso é útil quando você deseja certificar-se de que outros processos em execução no computador receberão um determinado período de tempo de CPU. O trecho a seguir limita a consulta ao utilizar no máximo dois processadores.  
  
 [!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
 [!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]  
  
 Em casos onde uma consulta esteja executando uma quantidade significativa de trabalho associado a computação, como E/S de Arquivo, pode ser útil especificar um grau de paralelismo maior do que o número de núcleos no computador.  
  
## <a name="ordered-versus-unordered-parallel-queries"></a>Consultas Paralelas Ordenadas Contra Não Ordenadas  
 Em algumas consultas, um operador de consulta deve produzir resultados que preservem a ordenação da sequência de origem. PLINQ fornece o <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operador para essa finalidade. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>é diferente do <xref:System.Linq.ParallelEnumerable.AsSequential%2A>. Um <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> sequência ainda é processada em paralelo, mas os resultados são armazenados em buffer e classificados. Porque um trabalho extra, normalmente envolve a preservação da ordem um <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> sequência pode ser processada mais lentamente do que o padrão <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> sequência. Se uma determinada operação paralela ordenada será mais rápida do que uma versão sequencial da operação, isso dependerá de vários fatores.  
  
 O exemplo de código a seguir mostra como aceitar a preservação da ordem.  
  
 [!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
 [!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]  
  
 Para saber mais, veja [Preservação da ordem em PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
## <a name="parallel-vs-sequential-queries"></a>Consultas paralelas versus sequenciais  
 Algumas operações exigem que os dados de origem sejam entregue de forma sequencial. O <xref:System.Linq.ParallelEnumerable> consulta operadores volte para o modo sequencial automaticamente quando necessário. Operadores de consulta definidas pelo usuário e delegados de usuário que exigem execução sequencial, PLINQ fornece o <xref:System.Linq.ParallelEnumerable.AsSequential%2A> método. Quando você usa <xref:System.Linq.ParallelEnumerable.AsSequential%2A>, todos os operadores subsequentes na consulta são executados sequencialmente até <xref:System.Linq.ParallelEnumerable.AsParallel%2A> é chamado novamente. Para saber mais, veja [Como combinar consultas LINQ paralelas e sequenciais](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md).  
  
## <a name="options-for-merging-query-results"></a>Opções para Mesclar Resultados da Consulta  
 Quando uma consulta PLINQ é executada em paralelo, seus resultados de cada thread de trabalho devem ser mesclados de volta para o thread principal para consumo de um loop `foreach` (`For Each` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) ou inserção em uma lista ou matriz. Em alguns casos, ela pode ser útil para especificar um determinado tipo de operação de mesclagem, por exemplo, para começar a produzir resultados mais rapidamente. Para essa finalidade, o PLINQ oferece suporte a <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> método e o <xref:System.Linq.ParallelMergeOptions> enumeração. Para saber mais, veja [Opções de mesclagem em PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
## <a name="the-forall-operator"></a>O Operador ForAll  
 Em sequencial [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] consultas de execução é adiada até que a consulta é enumerada em uma `foreach` (`For Each` na [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) loop ou por invocação de um método como <xref:System.Linq.ParallelEnumerable.ToList%2A> , <xref:System.Linq.ParallelEnumerable.ToArray%2A> , ou <xref:System.Linq.ParallelEnumerable.ToDictionary%2A>. Na PLINQ, você também pode usar `foreach` para executar a consulta e percorrer os resultados. No entanto, `foreach` em si não é executada em paralelo e, portanto, requer que a saída de todas as tarefas paralelas seja mesclada de volta ao thread que está executando o loop. Na PLINQ, você pode usar `foreach` quando tiver de preservar a ordenação final dos resultados da consulta e também sempre que estiver processando os resultados de forma serial, por exemplo, quando estiver chamando `Console.WriteLine` para cada elemento. Para mais rápido execução da consulta quando a preservação da ordem não é necessária e quando o processamento dos resultados poderá próprio paralelização, use o <xref:System.Linq.ParallelEnumerable.ForAll%2A> método para executar uma consulta PLINQ. <xref:System.Linq.ParallelEnumerable.ForAll%2A>não execute esta etapa de mesclagem final. O exemplo de código a seguir mostra como usar o <xref:System.Linq.ParallelEnumerable.ForAll%2A> método. <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>é usado aqui porque ele é otimizado para vários threads simultaneamente adicionando sem tentar remover todos os itens.  
  
 [!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
 [!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]  
  
 A ilustração a seguir mostra a diferença entre `foreach` e <xref:System.Linq.ParallelEnumerable.ForAll%2A> em relação a execução da consulta.  
  
 ![ForAll vs. ForEach](../../../docs/standard/parallel-programming/media/vs-isvnt-allvseach.png "VS_ISVNT_ALLvsEACH")  
  
## <a name="cancellation"></a>Cancelamento  
 A PLINQ é integrada aos tipos de cancelamento em [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. (Para saber mais, veja [Cancelamento em threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md)). Portanto, ao contrário das consultas sequenciais da LINQ to Objects, as consultas PLINQ podem ser canceladas. Para criar uma consulta PLINQ anulável, use o <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> operador na consulta e fornecer um <xref:System.Threading.CancellationToken> instância como argumento. Quando o <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriedade no token é definida como true, PLINQ Observe-lo, pare o processamento de todos os threads e lançar um <xref:System.OperationCanceledException>.  
  
 É possível que uma consulta PLINQ possa continuar a processar alguns elementos depois que o token de cancelamento é definido.  
  
 Para maior capacidade de resposta, você também pode responder a solicitações de cancelamento em representantes do usuário de longa duração. Para saber mais, veja [Como cancelar uma consulta PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="exceptions"></a>Exceções  
 Quando uma consulta PLINQ é executada, várias exceções podem ser geradas de diversos threads simultaneamente. Além disso, o código para tratar a exceção pode estar em um thread diferente do código que gerou a exceção. PLINQ usa o <xref:System.AggregateException> digite para encapsular todas as exceções que foram geradas por uma consulta e empacotar essas exceções para o thread de chamada. No thread de chamada, apenas um bloco try-catch é necessário. No entanto, você pode iterar por todas as exceções que são encapsuladas no <xref:System.AggregateException> e detectar qualquer um que você pode recuperar com segurança de. Em casos raros, algumas exceções podem ser geradas que não são encapsuladas em um <xref:System.AggregateException>, e <xref:System.Threading.ThreadAbortException>s também não são encapsulados.  
  
 Quando as exceções tiverem permissão de emergirem novamente para o thread de associação, então será possível que uma consulta continue a processar alguns itens após a geração da exceção.  
  
 Para saber mais, veja [Como tratar exceções em uma consulta PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="custom-partitioners"></a>Particionadores Personalizados  
 Em alguns casos, você pode melhorar o desempenho da consulta escrevendo um particionador personalizado que aproveite algumas características da fonte de dados. Na consulta, o particionador personalizado em si é o objeto enumerável que será consultado.  
  
 [!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
 [!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]  
  
 A PLINQ oferece suporte a um número fixo de partições (embora os dados possam ser dinamicamente reatribuídos a essas partições durante o tempo de execução para balanceamento de carga.). <xref:System.Threading.Tasks.Parallel.For%2A>e <xref:System.Threading.Tasks.Parallel.ForEach%2A> suporte somente o particionamento dinâmico, o que significa que o número de partições alterações em tempo de execução. Para saber mais, veja [Particionadores personalizados para PLINQ e TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="measuring-plinq-performance"></a>Medindo Desempenho PLINQ  
 Em muitos casos, uma consulta pode ser paralelizada, mas a sobrecarga de configuração de consulta paralela supera o benefício de desempenho obtido. Se uma consulta não gerar muita computação ou se a fonte de dados for pequena, uma consulta PLINQ poderá ser mais lenta do que uma consulta sequencial LINQ to Objects. Você pode usar o Analisador de Desempenho Paralelo no Visual Studio Team Server para comparar o desempenho de várias consultas, para localizar afunilamentos de processamento e para determinar se a consulta está em execução em paralelo ou sequencialmente. Para saber mais, veja [Visualizador de Simultaneidade](/visualstudio/profiling/concurrency-visualizer) e [Como medir o Desempenho da Consulta PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## <a name="see-also"></a>Consulte também  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Noções básicas sobre agilização no PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)
