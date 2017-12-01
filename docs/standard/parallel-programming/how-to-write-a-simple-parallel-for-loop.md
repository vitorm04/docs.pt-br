---
title: Como escrever um loop Parallel.For simples
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
- Parallel.For, How to Write
- for loop, parallel construction in .NET
- parallel for loops, how to use
ms.assetid: 9029ba7f-a9d1-4526-8c84-c88716dba5d4
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ed621f41e76addde777b974732470fcfbc903563
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Como escrever um loop Parallel.For simples
Este tópico contém dois exemplos que ilustram o <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> método. O primeiro usa o <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> sobrecarga de método e o segundo usa a <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> sobrecarga, as duas sobrecargas mais simples do <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> método. Você pode usar essas duas sobrecargas do <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> método quando você não precisa cancelar o loop, dividir as iterações do loop ou manter o estado de qualquer local de thread.  
  
> [!NOTE]
>  Esta documentação usa expressões lambda para definir delegados na TLP. Se você não estiver familiarizado com expressões lambda no C# ou no Visual Basic, veja [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 O primeiro exemplo calcula o tamanho dos arquivos em um único diretório. A segunda calcula o produto de duas matrizes.  
  
## <a name="example"></a>Exemplo  
 Este exemplo é um utilitário de linha de comando simples que calcula o tamanho total dos arquivos em um diretório. Ele espera um caminho de diretório único como um argumento e informa o número e o tamanho total dos arquivos no diretório. Depois de verificar se o diretório já existe, ele usa o <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> método para enumerar os arquivos no diretório e determinar os tamanhos de arquivo. Cada tamanho de arquivo é adicionado para o `totalSize` variável. Observe que a adição é realizada chamando o <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> para que a adição é executada como uma operação atômica. Caso contrário, várias tarefas podem tentar atualizar o `totalSize` variável simultaneamente.  
  
 [!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
 [!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> método para calcular o produto de duas matrizes. Ele também mostra como usar o <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> classe para comparar o desempenho de um loop paralelo com um loop paralelo não. Observe que, porque pode gerar um grande volume de saída, o exemplo permite que a saída para ser redirecionado para um arquivo.  
  
 [!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
 [!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]  
  
 Ao paralelizar qualquer código, incluindo loops, uma meta importante é utilizar os processadores tanto quanto possíveis sem sobre paralelizar para o ponto em que a sobrecarga de processamento paralelo nega qualquer benefícios de desempenho. Nesse exemplo específico, somente o loop externo é paralelizado porque não há muito trabalho realizado no loop interno. A combinação de uma pequena quantidade de trabalho e os efeitos de cache indesejável pode resultar em degradação do desempenho em loops paralelos aninhadas. Portanto, a paralelização do loop externo é apenas a melhor forma de maximizar os benefícios de simultaneidade na maioria dos sistemas.  
  
## <a name="the-delegate"></a>O representante  
 O terceiro parâmetro dessa sobrecarga de <xref:System.Threading.Tasks.Parallel.For%2A> for um representante do tipo `Action<int>` em c# ou `Action(Of Integer)` no Visual Basic. Um `Action` delegado, se ele tem zero, um ou parâmetros de tipo dezesseis, sempre retorna void. No Visual Basic, o comportamento de um `Action` está definida com um `Sub`. O exemplo usa uma expressão lambda para criar o delegado, mas você pode criar o delegado de outras formas também. Para obter mais informações, consulte [expressões Lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="the-iteration-value"></a>O valor de iteração  
 O representante usa um único parâmetro de entrada cujo valor é a iteração atual. Esse valor de iteração é fornecido pelo tempo de execução e seu valor inicial é o índice do primeiro elemento no segmento (partição) de origem que está sendo processada no thread atual.  
  
 Se você precisar de mais controle sobre o nível de simultaneidade, use uma das sobrecargas que usa um <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> parâmetro de entrada, como: <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>.  
  
## <a name="return-value-and-exception-handling"></a>Valor de retorno e tratamento de exceção  
 <xref:System.Threading.Tasks.Parallel.For%2A>Retorna um <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> quando tem concluído a todos os threads do objeto. Esse valor de retorno é útil quando você estiver parando ou separação de iteração de loop manualmente, porque o <xref:System.Threading.Tasks.ParallelLoopResult> armazena informações como a última iteração executou até a conclusão. Se uma ou mais exceções ocorrem em um dos threads, um <xref:System.AggregateException?displayProperty=nameWithType> será lançada.  
  
 O código neste exemplo, o valor de retorno <xref:System.Threading.Tasks.Parallel.For%2A> não é usado.  
  
## <a name="analysis-and-performance"></a>Análise e desempenho  
 Você pode usar o Assistente de desempenho para exibir o uso da CPU no computador. Como uma experiência, aumente o número de colunas e linhas de matrizes. Quanto maior as matrizes, quanto maior a diferença de desempenho entre as versões paralelas e sequenciais da computação. Quando a matriz é pequena, a versão sequencial será executado mais rapidamente devido à sobrecarga de configurar o loop paralelo.  
  
 Chamadas síncronas a recursos compartilhados, como o Console ou o sistema de arquivos, significativamente prejudicará o desempenho de um loop paralelo. Ao medir o desempenho, tente evitar chamadas como <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> dentro do loop.  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Copie e cole esse código em um projeto do Visual Studio 2010.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Tasks.Parallel.For%2A>  
 <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
 [Paralelismo de dados](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)
