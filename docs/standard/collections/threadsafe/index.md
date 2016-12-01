---
title: "Coleções thread-safe"
description: "Coleções thread-safe"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 92d5515d-f5d6-4a09-8bbb-31865d678643
translationtype: Human Translation
ms.sourcegitcommit: cfe65fcba1b3fdc09ffcac704a760d8ce29ea60b
ms.openlocfilehash: 421d46585b5d83f5772fa6596ad581c8c6acbf71

---

# <a name="thread-safe-collections"></a>Coleções thread-safe

O namespace [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) inclui várias classes de coleção que são tanto thread-safe quanto escalonáveis. Vários threads podem adicionar ou remover itens dessas coleções de modo seguro e eficiente sem a necessidade de sincronização adicional no código do usuário. Ao escrever novo código, use as classes de coleção simultâneas sempre que a coleção for gravada em vários threads simultaneamente. Se estiver lendo apenas de uma coleção compartilhada, você poderá usar as classes no namespace [System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic). É recomendável que você não use [System. Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) classes de coleções, a menos que você precise ter como destino o tempo de execução do .NET Framework 1.1 ou anterior.

## <a name="fine-grained-locking-and-lock-free-mechanisms"></a>Bloqueio refinado e mecanismos sem bloqueio

Alguns dos tipos de coleção simultâneos usam mecanismos de sincronização leves como [SpinLock](https://docs.microsoft.com/dotnet/core/api/System.Threading.SpinLock), [SpinWait](https://docs.microsoft.com/dotnet/core/api/System.Threading.SpinWait), [SemaphoreSlim](https://docs.microsoft.com/dotnet/core/api/System.Threading.SemaphoreSlim) e [CountdownEvent](https://docs.microsoft.com/dotnet/core/api/System.Threading.CountdownEvent). Esses tipos de sincronização geralmente usam giro ocupado por breves períodos antes de colocarem o thread em um verdadeiro estado `Wait`. Quando espera-se que os tempos de espera sejam muito curtos, girar é muito menos dispendioso em termos de recursos computacionais do que esperar, o que envolve uma transição de kernel que utiliza muitos recursos. Para classes de coleção que usam o giro, essa eficiência significa que vários threads podem adicionar e remover itens em uma taxa muito alta.

As classes [ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) e [ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) não usam nenhum bloqueio. Em vez disso, elas usam operações integradas para obter acesso thread-safe.

> [!NOTE]
> Considerando que as classes de coleções simultâneas dão suporte a [ICollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection), elas fornecem implementações para as propriedades `IsSynchronized` e `SyncRoot`, embora essas propriedades sejam irrelevantes. `IsSynchronized` sempre retorna `false` e `SyncRoot` é sempre nulo.

A tabela a seguir lista os tipos de coleção no namespace [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent).

Tipo | Descrição
---- | -----------
[BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) | Fornece funcionalidade de delimitação e bloqueio de qualquer tipo que implemente [IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1). Para obter mais informações, veja [Visão geral de BlockingCollection](blockingcollection-overview.md).
[ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) | Implementação thread-safe de uma coleção não ordenada de elementos.
[ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) | Implementação thread-safe de um dicionário de pares chave-valor.
[ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) | Implementação thread-safe de uma fila PEPS (primeiro a entrar, primeiro a sair).
[ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) | Implementação thread-safe de uma fila LIFO (último a entrar, primeiro a sair).
[IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1) | A interface que um tipo deve implementar para uso em um `BlockingCollection`.

## <a name="thread-synchronization-in-the-net-framework-version-10-and-20-collections"></a>Sincronização de thread nas coleções do .NET Framework versão 1.0 e 2.0

As coleções introduzidas pela primeira vez no .NET Framework versão 1.0 são encontradas no namespace [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections). Essas coleções, que incluem os comumente usados [ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList) e [Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable), fornecem algum acesso thread-safe por meio da propriedade `Synchronized`, que retorna um wrapper thread-safe em torno da coleção. O wrapper funciona bloqueando toda a coleção a cada operação de adição ou remoção. Portanto, cada thread que está tentando acessar a coleção deve aguardar por sua vez para receber esse bloqueio. Isso não é escalonável e pode causar degradação significativa no desempenho para coleções grandes. Além disso, o design não é totalmente protegido contra condições de corrida. 

As classes de coleção introduzidas pela primeira vez no .NET Framework versão 2.0 são encontradas no namespace [System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic). Eles incluem [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1), [Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) e assim por diante. Essas classes fornecem desempenho e segurança de tipo aprimorados em comparação com as classes `System.Collections`. No entanto, as classes de coleção `System.Collections.Generic` não fornecem nenhuma sincronização de thread; o código de usuário deve fornecer sincronização quando itens são adicionados ou removidos simultaneamente em vários threads.

Recomendamos as classes de coleção `System.Collections.Concurrent`, pois elas fornecem não apenas a segurança de tipo das classes de coleção `System.Collections.Generic`, mas também um acesso thread-safe mais eficiente e mais completo que aquele fornecido pelas coleções `System.Collections`.

## <a name="related-topics"></a>Tópicos relacionados

Título | Descrição
----- | -----------
[Visão geral de BlockingCollection](blockingcollection-overview.md) | Este tópico descreve a funcionalidade fornecida pelo tipo `BlockingCollection<T>`.
[Quando Usar uma Coleção Thread-Safe](when-to-use-a-thread-safe-collection.md) | Explica quando é apropriado usar uma coleção thread-safe.
[Como Adicionar e Remover Itens de um ConcurrentDictionary](how-to-add-and-remove-items.md) | Descreve como adicionar e remover elementos de um `ConcurrentDictionary<TKey, TValue>`.
[Como Adicionar e Retirar Itens Individualmente de uma BlockingCollection](how-to-add-and-take-items.md) | Descreve como adicionar e recuperar itens de uma coleta de bloqueio sem usar o enumerador de somente leitura.
[Como Adicionar a Funcionalidade de Delimitação e Bloqueio a uma Coleção](how-to-add-bounding-and-blocking.md ) | Descreve como usar qualquer classe de coleção como o mecanismo de armazenamento subjacente para uma coleção `IProducerConsumerCollection<T>;`.
[Como Usar ForEach para Remover Itens de uma BlockingCollection](how-to-use-foreach-to-remove.md ) | Descreve como usar `foreach` para remover todos os itens em uma coleta de bloqueio.
[Como Usar Matrizes de Coleções Blocking em um Pipeline](how-to-use-arrays-of-blockingcollections.md) | Descreve como usar várias coleções de bloqueio ao mesmo tempo para implementar um pipeline.
[Como Criar um Pool de Objetos Usando um ConcurrentBag](how-to-create-an-object-pool.md) | Mostra como usar um recipiente simultâneo para melhorar o desempenho em cenários nos quais, em vez de criar novos objetos continuamente, você pode reutilizá-los.

## <a name="reference"></a>Referência

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)






 





<!--HONumber=Nov16_HO3-->


