---
title: Como adicionar e tirar itens individualmente de uma BlockingCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f83e260e41acd7c8fff03cf7df0832bab229911
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568492"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Como adicionar e tirar itens individualmente de uma BlockingCollection
Este exemplo mostra como adicionar e remover itens de um <xref:System.Collections.Concurrent.BlockingCollection%601> tanto com bloqueio quanto sem bloqueio. Para obter mais informações sobre <xref:System.Collections.Concurrent.BlockingCollection%601>, veja [Visão geral de BlockingCollection](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
 Para obter um exemplo de como enumerar um <xref:System.Collections.Concurrent.BlockingCollection%601> até que ele fique vazio e não existam mais elementos a adicionar, veja [Como usar ForEach para remover itens de uma BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).
  
## <a name="example"></a>Exemplo  
 Este primeiro exemplo mostra como adicionar e remover itens para que as operações sejam bloqueadas se a coleção fica temporariamente vazia (ao remover) ou com a capacidade máxima (ao adicionar) ou se um período de tempo limite especificado é decorrido. Observe que o bloqueio de capacidade máxima é habilitado apenas quando a BlockingCollection é criada com uma capacidade máxima especificada no construtor.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Exemplo  
 Este segundo exemplo mostra como adicionar e tirar itens para que as operações não sejam bloqueadas. Se nenhum item estiver presente, a capacidade máxima em uma coleção associada tiver sido atingida ou o tempo limite tiver expirado, a operação <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> ou <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> retornará false. Isso permite que o thread faça algum trabalho útil por um tempo e então, mais tarde, tente novamente recuperar um item novo ou tente adicionar o mesmo item que não pôde ser adicionado anteriormente. O programa também demonstra como implementar o cancelamento ao acessar um <xref:System.Collections.Concurrent.BlockingCollection%601>.  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Visão geral de BlockingCollection](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
