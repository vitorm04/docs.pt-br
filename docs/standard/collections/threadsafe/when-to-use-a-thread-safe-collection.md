---
title: "Quando usar uma coleção thread-safe"
description: "Quando usar uma coleção thread-safe"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a2a42d44-f6a5-4f16-9000-026221d66349
translationtype: Human Translation
ms.sourcegitcommit: e07788926a995b41571be276379ad9285747951d
ms.openlocfilehash: 05f692a1a58c0c653e14993cafd61a0711ebf9f8

---

# <a name="when-to-use-a-thread-safe-collection"></a>Quando usar uma coleção thread-safe

Os tipos de coleção `ConcurrentQueue`, `ConcurrentStack`, `ConcurrentDictionary`, `ConcurrentBag` e `BlockingCollection` são projetados especialmente para dar suporte a operações de adição e remoção com multithread. Para obter o acesso thread-safe, esses novos tipos usam vários tipos de mecanismos de sincronização de bloqueio e sem bloqueio. A sincronização adiciona sobrecarga a uma operação. A quantidade de sobrecarga depende do tipo de sincronização usado, os tipos de operações que são executadas e outros fatores, como o número de threads que estão tentando acessar a coleção simultaneamente.

Em alguns cenários, a sobrecarga de sincronização é insignificante e permite que o tipo com multithread funcione significativamente mais rápido e ajuste a escala muito melhor do que seu equivalente não thread-safe quando protegido por um bloqueio externo. Em outros cenários, a sobrecarga pode fazer com o tipo thread-safe funcione e ajuste a escala na mesma velocidade ou até mais lentamente do que a versão bloqueada externamente não thread-safe do tipo.

As seções a seguir fornecem diretrizes gerais sobre quando usar uma coleção thread-safe versus sua equivalente não thread-safe que tem um bloqueio fornecido pelo usuário em torno de suas operações de leitura e gravação. Como o desempenho pode variar dependendo de vários fatores, as diretrizes não são específicas e não são necessariamente válidas em todas as circunstâncias. Se o desempenho for muito importante, a melhor maneira de determinar que tipo de coleção usar é medir o desempenho com base em cargas e configurações de computador representativas. Este documento usa os seguintes termos:

*Cenário de produtor-consumidor puro:* qualquer thread que está adicionando ou removendo elementos, não ambos.

*Cenário de produtor-consumidor misto:* qualquer thread que está adicionando e removendo elementos.

*Acelerado:* desempenho algorítmico mais rápido relativo a outro tipo no mesmo cenário.

*Escalabilidade:* o aumento no desempenho proporcional ao número de núcleos no computador. Um algoritmo que ajusta a escala tem um desempenho mais rápido em oito núcleos do que em dois núcleos.

## <a name="concurrentqueuelttgt-vs-queuelttgt"></a>ConcurrentQueue&lt;T&gt; vs. Queue&lt;T&gt;

Em cenários de produtor-consumidor puros, em que o tempo de processamento para cada elemento é muito pequeno (poucas instruções), [System.Collections.Concurrent.ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) pode oferecer os benefícios de desempenho modestos em relação a um [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) que tem um bloqueio externo. Nesse cenário, `ConcurrentQueue<T>` funciona melhor quando um thread dedicado está enfileirando e um está retirando da fila. Se você não impuser essa regra, `Queue<T>` poderá até mesmo funcionar um pouco mais rápido do que `ConcurrentQueue<T>` em computadores com vários núcleos. 

Quando o tempo de processamento é em torno de 500 FLOPS (operações em ponto flutuante) ou mais, a regra de dois threads não se aplica a `ConcurrentQueue<T>`, que tem a escalabilidade muito boa. `Queue<T>` não ajusta a escala bem nesse cenário.

Em cenários de produtor-consumidor mistos, quando o tempo de processamento é muito pequeno, um `Queue<T>` que tem um bloqueio externo ajusta a escala melhor do que `ConcurrentQueue<T>`. No entanto, quando o tempo de processamento é em torno de 500 FLOPS ou mais, o `ConcurrentQueue<T>` ajusta a escala melhor.

## <a name="concurrentstack-vs-stack"></a>ConcurrentStack vs. Pilha

Em cenários de produtor-consumidor puros, quando o tempo de processamento é muito pequeno, [System.Collections.Concurrent.ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) e [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) que têm um bloqueio externo provavelmente funcionarão praticamente da mesma forma com um thread de colocação dedicado e um thread de retirada dedicado. No entanto, conforme o número de threads aumenta, os dois tipos ficam mais lentos devido ao aumento da contenção e `Stack<T>` pode funcionar melhor do que `ConcurrentStack<T>`. Quando o tempo de processamento é em torno de 500 FLOPS ou mais, os dois tipos ajustam a escala aproximadamente na mesma taxa. 

Em cenários de produtor-consumidor mistos, `ConcurrentStack<T>` é mais rápido para cargas de trabalho grandes e pequenas.

O uso de `PushRange` e `TryPopRange` pode acelerar muito os tempos de acesso.

## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary vs. Dicionário

Em geral, use uma [System.Collections.Concurrent.ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) em qualquer cenário em que estiver adicionando ou atualizando chaves ou valores simultaneamente de vários threads. Em cenários que envolvem atualizações frequentes e relativamente poucas leituras, o `ConcurrentDictionary<TKey, TValue>` geralmente oferece benefícios modestos. Em cenários que envolvem muitas leituras e muitas atualizações, o `ConcurrentDictionary<TKey, TValue>` geralmente é significativamente mais rápido em computadores que têm qualquer número de núcleos.

Em cenários que envolvem atualizações frequentes, você pode aumentar o nível de simultaneidade no `ConcurrentDictionary<TKey, TValue>` e, depois, medir para ver se o desempenho aumenta em computadores que têm mais núcleos. Se você alterar o nível de simultaneidade, evite operações globais o máximo possível.

Se você estiver apenas lendo chaves ou valores, o [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) é mais rápido porque não é necessária nenhuma sincronização se o dicionário não estiver sendo modificado por nenhum thread.

## <a name="concurrentbag"></a>ConcurrentBag

Em cenários de produtor-consumidor puros, [System.Collections.Concurrent.ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) provavelmente funcionará mais lentamente do que os outros tipos de coleção simultâneas.

Em cenários produtor-consumidor mistos, `ConcurrentBag<T>` geralmente é muito mais rápido e mais escalonável do que qualquer outro tipo de coleção simultânea para cargas de trabalho grandes e pequenas.

## <a name="blockingcollection"></a>BlockingCollection

Quando forem necessárias semânticas de delimitação e bloqueio, [System.Collections.Concurrent.BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) provavelmente funcionará mais rápido do que qualquer implementação personalizada. Ele também dá suporte ao cancelamento, enumeração e tratamento de exceções avançados.

## <a name="see-also"></a>Consulte também

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[Coleções Thread-Safe](index.md)



<!--HONumber=Nov16_HO4-->


