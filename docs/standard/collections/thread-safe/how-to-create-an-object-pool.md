---
title: "Instruções: criar um pool de objetos usando um ConcurrentBag | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
caps.latest.revision: 5
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bfe61501586deed112d6a94bf90fd83e84f2639f
ms.lasthandoff: 04/18/2017

---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>Como criar um pool de objetos usando um ConcurrentBag
Este exemplo mostra como usar um recipiente simultâneo para implementar um pool de objetos. Pools de objeto podem melhorar o desempenho do aplicativo em situações em que exigem várias instâncias de uma classe e nos quais criar ou destruir a classe é um processo caro. Quando um programa cliente solicita um novo objeto, o pool de objetos primeiro tenta fornecer um que já foi criado e retornado ao pool. Se nenhum estiver disponível, só então um novo objeto será criado.  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601> é usado para armazenar os objetos porque ele dá suporte à inserção e remoção rápidas, especialmente quando o mesmo thread está tanto adicionando quanto removendo itens. Este exemplo poderia ser ampliado ainda mais para ser criado em torno de um <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> que a estrutura de dados do recipiente implementa, como fazem <xref:System.Collections.Concurrent.ConcurrentQueue%601> e <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>Consulte também  
 [Coleções Thread-Safe](../../../../docs/standard/collections/thread-safe/index.md)
