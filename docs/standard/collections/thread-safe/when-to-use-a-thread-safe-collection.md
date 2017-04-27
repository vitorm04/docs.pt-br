---
title: "Quando usar uma coleção thread-safe | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
caps.latest.revision: 9
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 87898a4a6ba3d3ef4c53fd1c6b8f94ff353f10e4
ms.lasthandoff: 04/18/2017

---
# <a name="when-to-use-a-thread-safe-collection"></a>Quando usar uma coleção thread-safe
O [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] apresenta cinco novos tipos de coleção especialmente projetados para dar suporte a operações multithread de adicionar e remover. Para obter o acesso thread-safe, esses novos tipos usam vários tipos de mecanismos de sincronização de bloqueio e sem bloqueio. A sincronização adiciona sobrecarga a uma operação. A quantidade de sobrecarga depende do tipo de sincronização usado, os tipos de operações que são executadas e outros fatores, como o número de threads que estão tentando acessar a coleção simultaneamente.  
  
 Em alguns cenários, a sobrecarga de sincronização é insignificante e permite que o tipo com multithread funcione significativamente mais rápido e ajuste a escala muito melhor do que seu equivalente não thread-safe quando protegido por um bloqueio externo. Em outros cenários, a sobrecarga pode fazer com o tipo thread-safe funcione e ajuste a escala na mesma velocidade ou até mais lentamente do que a versão bloqueada externamente não thread-safe do tipo.  
  
 As seções a seguir fornecem diretrizes gerais sobre quando usar uma coleção thread-safe versus sua equivalente não thread-safe que tem um bloqueio fornecido pelo usuário em torno de suas operações de leitura e gravação. Como o desempenho pode variar dependendo de vários fatores, as diretrizes não são específicas e não são necessariamente válidas em todas as circunstâncias. Se o desempenho for muito importante, a melhor maneira de determinar que tipo de coleção usar é medir o desempenho com base em cargas e configurações de computador representativas. Este documento usa os seguintes termos:  
  
 *Cenário de produtor-consumidor puro*  
 Um determinado thread está adicionando ou removendo elementos, mas não executando as duas ações.  
  
 *Cenário de produtor-consumidor misto*  
 Um determinado thread está tanto adicionando quanto removendo elementos.  
  
 *Aceleração*  
 Desempenho algorítmico mais rápido em relação a outro tipo no mesmo cenário.  
  
 *Escalabilidade*  
 O aumento no desempenho que é proporcional ao número de núcleos no computador. Um algoritmo que ajusta a escala tem um desempenho mais rápido em oito núcleos do que em dois núcleos.  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue(T) versus Queue(T)  
 Em cenários de produtor-consumidor puro, nos quais o tempo de processamento de cada elemento é muito pequeno (poucas instruções), a <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> pode oferecer benefícios de desempenho modestos em comparação a uma <xref:System.Collections.Generic.Queue%601?displayProperty=fullName> que tem um bloqueio externo. Nesse cenário, a <xref:System.Collections.Concurrent.ConcurrentQueue%601> funciona melhor quando um thread dedicado está enfileirando e um thread dedicado está desenfileirando. Se você não impuser essa regra, <xref:System.Collections.Generic.Queue%601> poderá até mesmo ser executada com uma rapidez um pouco maior do que <xref:System.Collections.Concurrent.ConcurrentQueue%601> em computadores com vários núcleos.  
  
 Quando o tempo de processamento estiver em torno de 500 FLOPS (operações em ponto flutuante) ou mais, a regra de dois threads não se aplicará a <xref:System.Collections.Concurrent.ConcurrentQueue%601>, que tem a escalabilidade muito boa. <xref:System.Collections.Generic.Queue%601> não tem um bom ajuste de escala nesse cenário.  
  
 Em cenários de produtor-consumidor misto, quando o tempo de processamento é muito pequeno, um <xref:System.Collections.Generic.Queue%601> que tem um bloqueio externo tem um ajuste de escala melhor do que <xref:System.Collections.Concurrent.ConcurrentQueue%601>. No entanto, quando o tempo de processamento está em torno de 500 FLOPS ou mais, a <xref:System.Collections.Concurrent.ConcurrentQueue%601> tem um ajuste de escala melhor.  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack vs. Pilha  
 Em cenários de produtor-consumidor puros, quando o tempo de processamento é muito pequeno, <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName> e <xref:System.Collections.Generic.Stack%601?displayProperty=fullName> que tem um externo bloqueio provavelmente terão praticamente o mesmo desempenho com um thread dedicado de colocar e um thread dedicado de remover o mais recente da pilha. No entanto, à medida que o número de threads aumenta, os dois tipos desaceleram devido ao aumento de contenção e <xref:System.Collections.Generic.Stack%601> pode executar melhor do que <xref:System.Collections.Concurrent.ConcurrentStack%601>. Quando o tempo de processamento é em torno de 500 FLOPS ou mais, os dois tipos ajustam a escala aproximadamente na mesma taxa.  
  
 Em cenários de produtor-consumidor mistos, <xref:System.Collections.Concurrent.ConcurrentStack%601> é mais rápida para cargas de trabalho pequenas e grandes.  
  
 O uso de <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> e <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> pode acelerar bastante os tempos de acesso.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary vs. Dicionário  
 Em geral, use um <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> em qualquer cenário em que você esteja adicionando e atualizando chaves ou valores simultaneamente de vários threads. Em cenários que envolvem atualizações frequentes e relativamente poucas leituras, o <xref:System.Collections.Concurrent.ConcurrentDictionary%602> geralmente oferece benefícios modestos. Em cenários que envolvem muitas leituras e muitas atualizações, geralmente, o <xref:System.Collections.Concurrent.ConcurrentDictionary%602> é significativamente mais rápido em computadores com qualquer número de núcleos.  
  
 Em cenários que envolvem atualizações frequentes, você pode aumentar o nível de simultaneidade no <xref:System.Collections.Concurrent.ConcurrentDictionary%602> e, em seguida, medir para ver se o desempenho aumenta em computadores que têm mais núcleos. Se você alterar o nível de simultaneidade, evite operações globais o máximo possível.  
  
 Se você só estiver lendo chave ou valores, o <xref:System.Collections.Generic.Dictionary%602> será mais rápido porque nenhuma sincronização será necessária se o dicionário não estiver sendo modificado por nenhum thread.  
  
## <a name="concurrentbag"></a>ConcurrentBag  
 Em cenários de produtor-consumidor puros, o <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName> provavelmente terá um desempenho mais lento do que os outros tipos de coleções simultâneas.  
  
 Em cenários de produtor-consumidor mistos, geralmente, o <xref:System.Collections.Concurrent.ConcurrentBag%601> é muito mais rápido e mais escalonável do que qualquer outro tipo de coleta simultânea para cargas de trabalho grandes e pequenas.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Quando as semânticas de limitação e bloqueio forem necessárias, provavelmente, <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> terá um desempenho mais rápido do que qualquer implementação personalizada. Ele também dá suporte ao cancelamento, enumeração e tratamento de exceções avançados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [Coleções thread-safe](../../../../docs/standard/collections/thread-safe/index.md)   
 [Programação paralela](../../../../docs/standard/parallel-programming/index.md)
