---
title: Como usar matrizes de coleções Blocking em um pipeline
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
ms.openlocfilehash: 397c438bacd1cfed1613efef61e9d7266d55ea47
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711253"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a>Como usar matrizes de coleções Blocking em um pipeline
O exemplo a seguir mostra como usar matrizes de objetos <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> com métodos estáticos como <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> e <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> para implementar transferência de dados rápida e flexível entre componentes.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra uma implementação de pipeline básica na qual cada objeto está pegando dados simultaneamente da coleção de entrada, transformando-os e passando-os à coleção de saída.  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a>Veja também

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Coleções Thread-Safe](../../../../docs/standard/collections/thread-safe/index.md)
