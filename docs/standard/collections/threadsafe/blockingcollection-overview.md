---
title: "Visão geral de BlockingCollection"
description: "Visão geral de BlockingCollection"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a1a867de-53c2-49ca-9a1a-e5770a942724
translationtype: Human Translation
ms.sourcegitcommit: e07788926a995b41571be276379ad9285747951d
ms.openlocfilehash: 64a01b5e21e012dfaae07a02f5fb27932be9cf98

---

# <a name="blockingcollection-overview"></a>Visão geral de BlockingCollection

[BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) é uma classe de coleção thread-safe que fornece os seguintes recursos:

*   Uma implementação do padrão de produtor-consumidor.

*   Adição e remoção thread-safe de itens de uma coleção.

*   Capacidade máxima opcional.

*   Operações de inserção e remoção que bloqueiam quando a coleção está vazia ou cheia.

*   Operações “try” de inserção e remoção que não bloqueiam ou bloqueiam até um período específico.

*   Encapsula qualquer tipo de coleção que implemente [IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1).

*   Cancelamento com tokens de cancelamento.

*   Dois tipos de enumeração com `foreach`: 

    1. Enumeração de somente leitura.
    
    2. Enumeração que remove itens conforme eles são enumerados.
    
## <a name="bounding-and-blocking-support"></a>Suporte a delimitação e bloqueio 

[BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) dá suporte à delimitação e bloqueio. Delimitação significa que você pode definir a capacidade máxima da coleção. A delimitação é importante em determinados cenários, porque permite que você controle o tamanho máximo da coleção na memória e impede que os threads de produção se distanciem muito a frente dos threads de consumo.

Várias tarefas ou threads podem adicionar itens à coleção simultaneamente e se a coleção atingir sua capacidade máxima especificada, os threads de produção serão bloqueados até que um item seja removido. Vários consumidores podem remover itens simultaneamente e, se a coleção ficar vazia, os threads de consumo serão bloqueados até que um produtor adicione um item. Um thread de produção pode chamar `CompleteAdding` para indicar que não serão adicionados mais itens. Os consumidores monitoram a propriedade `IsCompleted` para saber quando a coleção está vazia e não serão adicionados mais itens. O exemplo a seguir mostra um `BlockingCollection` simples com uma capacidade limitada de 100. Uma tarefa de produtor adiciona itens à coleção contanto que algumas condições sejam verdadeiras e, em seguida, chama `CompleteAdding`. A tarefa de consumidor tira itens até que a propriedade `IsCompleted` seja true.

```csharp
// A bounded collection. It can hold no more 
// than 100 items at once.
BlockingCollection<Data> dataItems = new BlockingCollection<Data>(100);


// A simple blocking consumer with no cancellation.
Task.Run(() => 
{
    while (!dataItems.IsCompleted)
    {

        Data data = null;
        // Blocks if number.Count == 0
        // IOE means that Take() was called on a completed collection.
        // Some other thread can call CompleteAdding after we pass the
        // IsCompleted check but before we call Take. 
        // In this example, we can simply catch the exception since the 
        // loop will break on the next iteration.
        try
        {
            data = dataItems.Take();
        }
        catch (InvalidOperationException) { }

        if (data != null)
        {
            Process(data);
        }
    }
    Console.WriteLine("\r\nNo more items to take.");
});

// A simple blocking producer with no cancellation.
Task.Run(() =>
{
    while (moreItemsToAdd)
    {
        Data data = GetData();
        // Blocks if numbers.Count == dataItems.BoundedCapacity
        dataItems.Add(data);
    }
    // Let consumer know we are done.
    dataItems.CompleteAdding();
});
```

Para obter um exemplo completo, consulte [Como adicionar e tirar itens individualmente de uma BlockingCollection](how-to-add-and-take-items.md).

## <a name="timed-blocking-operations"></a>Operações de bloqueio cronometrado

Nas operações `TryAdd` e `TryTake` de bloqueio cronometrado em coleções limitadas, o método tenta adicionar ou tirar um item. Se um item estiver disponível, ele será colocado na variável que foi passada pela referência e o método retornará `true`. Se nenhum item for recuperado após um período de tempo limite especificado o método retornará `false`. O thread fica, então, livre para realizar outro trabalho útil antes de tentar acessar a coleção novamente. Para obter um exemplo de acesso com bloqueio cronometrado, consulte o segundo exemplo em [Como adicionar e tirar itens individualmente de uma BlockingCollection](how-to-add-and-take-items.md).

## <a name="cancelling-add-and-take-operations"></a>Cancelando as operações Add e Take

As operações Add e Take normalmente são realizadas em um loop. Você pode cancelar um loop, passando um `CancellationToken` para o método `TryAdd` ou `TryTake` e, em seguida, verificando o valor da propriedade `IsCancellationRequested` do token em cada iteração. Se o valor for `true`, então cabe a você responder à solicitação de cancelamento limpando quaisquer recursos e saindo do loop. O exemplo a seguir mostra uma sobrecarga de `TryAdd` que usa um token de cancelamento e o código que ele usa:

```csharp
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );
```

## <a name="specifying-the-collection-type"></a>Especificando o tipo de coleção

Ao criar um `BlockingCollection<T>;`, você pode especificar não apenas a capacidade limitada, mas também o tipo de coleção a ser usado. Por exemplo, seria possível especificar um [ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) para o comportamento PEPS (primeiro a entrar, primeiro a sair) ou um [ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) para o comportamento UEPS (último a entrar, primeiro a sair). Você pode usar qualquer classe de coleção que implemente a interface [IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1). O tipo de coleção padrão para `BlockingCollection<T>` é `ConcurrentQueue<T>`. O exemplo de código a seguir mostra como criar um `BlockingCollection<T>` de cadeias de caracteres que tem uma capacidade de 1000 e usa um [ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1):

```csharp
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );
```

## <a name="ienumerable-support"></a>Suporte a IEnumerable

`BlockingCollection<T>` fornece um método `GetConsumingEnumerable` que permite que os consumidores usem uma instrução `foreach` para remover itens até a coleção ser concluída, o que significa que ela está vazia e não serão adicionados mais itens. Para obter mais informações, confira [Como usar ForEach para remover itens de uma BlockingCollection](how-to-use-foreach-to-remove.md).

## <a name="using-many-blockingcollections-as-one"></a>Usando vários BlockingCollections como um

Para cenários em que um consumidor precisa remover itens de várias coleções simultaneamente, é possível criar matrizes de `BlockingCollection<T>` e usar os métodos estáticos como `TakeFromAny` e `AddToAny` que adicionarão ou retirarão de qualquer uma das coleções na matriz. Se uma coleção for de bloqueio, o método imediatamente tenta outra até encontrar uma que possa realizar a operação. Para obter mais informações, confira [Como usar matrizes de coleções Blocking em um pipeline](how-to-use-arrays-of-blockingcollections.md).

## <a name="see-also"></a>Consulte também

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[Coleções e Estruturas de Dados](../index.md)

[Coleções Thread-Safe](index.md)




<!--HONumber=Nov16_HO5-->


