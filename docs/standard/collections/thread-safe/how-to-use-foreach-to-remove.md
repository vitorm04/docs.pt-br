---
title: Como usar ForEach para remover itens de uma BlockingCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44b71ed726af585259b015c608e49d8c81e4e22a
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49120955"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Como usar ForEach para remover itens de uma BlockingCollection
Além de extrair itens de uma <xref:System.Collections.Concurrent.BlockingCollection%601> usando o método <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> e <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A>, também é possível usar um [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) em Visual Basic), para remover itens até que a adição seja concluída e a coleção esteja vazia. Isso é chamado de *enumeração de mutação* ou de *mutação consumidora* porque, ao contrário de um loop típico `foreach` (`For Each`), esse enumerador modifica a coleção de origem, removendo itens.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como remover todos os itens em um <xref:System.Collections.Concurrent.BlockingCollection%601> usando um loop `foreach` (`For Each`).  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 Este exemplo usa um loop `foreach` com o método <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> no thread consumidor, que faz com que cada item seja removido da coleção ao ser enumerado. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limita o número máximo de itens que estão na coleção a qualquer momento. Enumerar a coleção dessa maneira bloqueará o thread consumidor se nenhum item estiver disponível ou se a coleção estiver vazia. Neste exemplo, o bloqueio não é um problema porque o thread produtor adiciona itens mais rápido do que eles podem ser consumidos.  
  
 Não há nenhuma garantia de que os itens sejam enumerados na mesma ordem em que são adicionados por threads de produtor.  
  
 Para enumerar a coleção sem modificá-la, basta usar `foreach` (`For Each`) sem o método <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A>. No entanto, é importante compreender que esse tipo de enumeração representa um instantâneo da coleção em um ponto preciso no tempo. Se outros threads estiverem adicionando ou removendo itens simultaneamente enquanto você estiver executando o loop, o loop poderá não representar o estado real da coleção.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [Programação paralela](../../../../docs/standard/parallel-programming/index.md)
