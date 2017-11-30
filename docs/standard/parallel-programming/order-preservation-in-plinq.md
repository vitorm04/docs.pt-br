---
title: "Preservação da ordem em PLINQ"
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
helpviewer_keywords: PLINQ queries, order preservation
ms.assetid: 10d202bc-19e1-4b5c-bbf1-9a977322a9ca
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 060459cf8f408e40ddc394fbcda6a022ec6379de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="order-preservation-in-plinq"></a>Preservação da ordem em PLINQ
Em PLINQ, a meta é maximizar o desempenho, mantendo a exatidão. Uma consulta deve executar mais rápido possível, mas ainda produzir os resultados corretos. Em alguns casos, a correção requer a ordem da sequência de origem a serem preservados; No entanto, a ordenação pode ser dispendiosa. Portanto, por padrão, o PLINQ não preserva a ordem da sequência de origem. Nesse sentido, PLINQ semelhante [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)], mas é diferente de LINQ para objetos, que preserva a ordenação.  
  
 Para substituir o comportamento padrão, você pode ativar preservação da ordem usando o <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operador na sequência de origem. Em seguida, você pode desativar a preservação da ordem mais tarde na consulta usando o <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> método. Nos dois métodos, a consulta é processada com base na heurística que determinar se deseja executar a consulta como paralelo ou sequenciais. Para saber mais, veja [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
 O exemplo a seguir mostra uma consulta paralela não ordenada que filtra todos os elementos que correspondem a uma condição, sem tentar ordenar os resultados de qualquer forma.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 Esta consulta não geram necessariamente as primeiras 1000 cidades na sequência de origem que atendem à condição, mas em vez disso, alguns conjuntos de 1000 cidades que atendem à condição. Operadores de consulta PLINQ particionam a sequência de origem em vários subsequências que são processados como as tarefas simultâneas. Se a preservação da ordem não for especificada, os resultados de cada partição são enviados para a próxima fase da consulta em uma ordem arbitrária. Além disso, uma partição pode resultar em um subconjunto de seus resultados antes de continuar a processar os elementos restantes. A ordem resultante pode ser diferente cada vez. O aplicativo não pode controlar isso porque depende de como o sistema operacional agenda os threads.  
  
 O exemplo a seguir substitui o comportamento padrão usando o <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operador na sequência de origem. Isso garante que o <xref:System.Linq.ParallelEnumerable.Take%2A> método retorna as primeiros 1000 cidades na sequência de origem que atendem à condição.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 No entanto, essa consulta provavelmente não executar tão rápida quanto a versão não ordenada porque ele deve controlar a ordem original em toda as partições e em tempo de mesclagem, verifique se a ordenação é consistente. Portanto, é recomendável que você use <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> somente quando necessário e apenas para as partes da consulta que a exigem. Quando a preservação da ordem não é mais necessária, use <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> para desativá-lo. O exemplo a seguir realiza isso pela composição de duas consultas.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 Observe que o PLINQ preserva a ordenação de uma sequência produzida por operadores de impor a ordem para o restante da consulta. Em outras palavras, operadores, como <xref:System.Linq.ParallelEnumerable.OrderBy%2A> e <xref:System.Linq.ParallelEnumerable.ThenBy%2A> são tratados como se eles foram seguidos por uma chamada para <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
## <a name="query-operators-and-ordering"></a>Operadores de consulta e a ordenação  
 Os operadores de consulta a seguir apresentam a preservação da ordem em todas as demais operações em uma consulta, ou até que <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> é chamado:  
  
-   <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 Os seguintes operadores de consulta PLINQ podem, em alguns casos, exigem sequências ordenadas de origem para produzir resultados corretos:  
  
-   <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Alguns operadores de consulta PLINQ se comportam de forma diferente, dependendo se a sequência de origem é ordenada ou desordenada. A tabela a seguir lista esses operadores.  
  
|Operador|Quando a sequência de origem é ordenada de resultados|Resultado quando a sequência de origem não está classificada|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Saída não determinística para operações nonassociative ou noncommutative|Saída não determinística para operações nonassociative ou noncommutative|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Não aplicável|Não aplicável|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Não aplicável|Não aplicável|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Não aplicável|Não aplicável|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Saída não determinística para operações nonassociative ou noncommutative|Saída não determinística para operações nonassociative ou noncommutative|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Resultados ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Resultados ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Não aplicável|Não aplicável|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Não aplicável|Não aplicável|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Resultados ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Retorna o elemento especificado|Elemento arbitrário|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Retorna o elemento especificado|Elemento arbitrário|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Resultados não ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Retorna o elemento especificado|Elemento arbitrário|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Retorna o elemento especificado|Elemento arbitrário|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Executa de forma não determinística em paralelo|Executa de forma não determinística em paralelo|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Resultados ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Resultados ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Resultados ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Resultados ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Retorna o elemento especificado|Elemento arbitrário|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Retorna o elemento especificado|Elemento arbitrário|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Não aplicável|Não aplicável|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Não aplicável|Não aplicável|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Reorganiza a sequência|Inicia novas ordenados seção|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Reorganiza a sequência|Inicia novas ordenados seção|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Não aplicável (mesmo padrão como <xref:System.Linq.ParallelEnumerable.AsParallel%2A> )|Não aplicável|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Não aplicável (mesmo padrão como <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Não aplicável|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Inverte|Não agir|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Resultados ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>(indexada)|Resultados ordenados|Resultado não ordenado.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Resultados ordenados.|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>(indexada)|Resultados ordenados.|Resultado não ordenado.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Comparação ordenada|Comparação não ordenada|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Não aplicável|Não aplicável|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Não aplicável|Não aplicável|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Ignora o primeiro  *n*  elementos|Ignora qualquer  *n*  elementos|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Resultados ordenados.|Não determinístico. Executa SkipWhile na ordem arbitrária atual|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Saída não determinística para operações nonassociative ou noncommutative|Saída não determinística para operações nonassociative ou noncommutative|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Leva primeiro `n` elementos|Usa qualquer `n` elementos|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Resultados ordenados|Não determinístico. Executa TakeWhile na ordem arbitrária atual|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Suplementos`OrderBy`|Suplementos`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Suplementos`OrderBy`|Suplementos`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Resultados ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Não aplicável|Não aplicável|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Resultados ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Resultados ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Resultados ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Resultados ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>(indexada)|Resultados ordenados|Resultados não ordenados|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Resultados ordenados|Resultados não ordenados|  
  
 Não ordenada de resultados não são ativamente embaralhados; simplesmente não têm qualquer lógica de ordenação especial aplicada a eles. Em alguns casos, uma consulta não ordenada pode manter a ordem da sequência de origem. Para consultas que usam o operador Select indexado, PLINQ garante que os elementos de saída se sairá na ordem crescente índices, mas faz nenhuma garantia sobre quais índices será atribuída aos quais elementos.  
  
## <a name="see-also"></a>Consulte também  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)
