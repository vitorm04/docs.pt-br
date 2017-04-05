---
title: "Coleções e estruturas de dados"
description: "Coleções e estruturas de dados"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 9e70255a-c02a-4046-86b7-10c84bab2d38
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 30e53c38bd58e15668e01f2af79defb0a0918192
ms.lasthandoff: 04/05/2017

---

# <a name="collections-and-data-structures"></a>Coleções e estruturas de dados

Dados semelhantes podem normalmente ser tratados com mais eficiência quando armazenados e manipulados como uma coleção. Você pode usar a classe [System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array) ou as classes nos namespaces [System. Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections), [System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic) ou [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) para adicionar, remover e modificar elementos individuais ou um intervalo de elementos em uma coleção.

Há dois tipos principais de coleções; coleções genéricas e coleções não genéricas. Coleções genéricas são fortemente tipadas em tempo de compilação. Por isso, coleções genéricas normalmente oferecem melhor desempenho. Coleções genéricas aceitam um parâmetro de tipo quando são criadas e não exigem que você converta de e para o tipo [Objeto](https://docs.microsoft.com/dotnet/core/api/System.Object) ao adicionar ou remover itens da coleção. Coleções não genéricas armazenam itens como [Objeto](https://docs.microsoft.com/dotnet/core/api/System.Object) e exigem conversão. Você pode ver as coleções não genéricas no código mais antigo.

As coleções no namespace [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) fornecem operações thread-safe eficientes para acessar itens da coleção de vários threads.

## <a name="common-collection-features"></a>Recursos comuns de coleção

Todas as coleções fornecem métodos para adicionar, remover ou localizar itens na coleção. Além disso, todas as coleções que direta ou indiretamente implementam a interface [ICollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection) ou a interface [ICollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.ICollection-1) compartilham estes recursos: 

* **A capacidade de enumerar a coleção**

   Coleções do .NET framework implementam [System.Collections.IEnumerable](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) ou [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1) para permitir a iteração da coleção. Um enumerador pode ser considerado um ponteiro móvel para qualquer elemento da coleção. A instrução `foreach, in` (C#) usa o enumerador exposto pelo método `GetEnumerator` e oculta a complexidade de manipulação do enumerador. Além disso, qualquer coleção que implementa [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1) é considerada um tipo passível de consulta e pode ser consultada com LINQ. Consultas LINQ fornecem um padrão comum para o acesso de dados. Elas são geralmente mais concisas e legíveis que loops for each padrão e fornecem filtragem, classificação e agrupamento de recursos. Consultas LINQ também podem melhorar o desempenho.
    
* **A capacidade de copiar o conteúdo da coleção para uma matriz**

   Todas as coleções podem ser copiadas para uma matriz usando o método `CopyTo`; no entanto, a ordem dos elementos na nova matriz se baseia na sequência na qual o enumerador os retorna. A matriz resultante é sempre unidimensional com um limite inferior de zero.
    
Além disso, muitas classes de coleção contêm os seguintes recursos:

* **Propriedades de capacidade e contagem**

   A capacidade de uma coleção é o número de elementos que ela pode conter. A contagem de uma coleção é o número de elementos que ela realmente contém. Algumas coleções ocultam a capacidade ou a contagem ou ambas.
    
   A maioria das coleções se expande automaticamente em capacidade quando a capacidade atual é atingida. A memória é realocada e os elementos são copiados da coleção antiga para a nova. Isso reduz o código necessário para usar a coleção; no entanto, o desempenho da coleção pode ser afetado de forma negativa. Por exemplo, para [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1), se `Count` for inferior a `Capacity`, adicionar um item será uma operação O(1). Se a capacidade precisar ser aumentada para acomodar o novo elemento, adicionar um item se torna uma operação O(n), em que n é `Count`. A melhor maneira de evitar um desempenho ruim causado por várias realocações é definir a capacidade inicial para que seja o tamanho estimado da coleção. 
    
   Uma [BitArray](https://docs.microsoft.com/dotnet/core/api/System.Collections.BitArray) é um caso especial; sua capacidade é a mesma que seu comprimento, que é o mesmo de sua contagem.
    
*   **Um limite inferior consistente**

   O limite inferior de uma coleção é o índice do seu primeiro elemento. Todas as coleções indexadas nos namespaces [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) têm um limite inferior de zero, indicando que são indexados em 0. [Array](https://docs.microsoft.com/dotnet/core/api/System.Array) tem um limite inferior de zero por padrão, mas um limite inferior diferente pode ser definido ao criar uma instância da classe `Array` usando `Array.CreateInstance`.

*   **Sincronização para acesso de vários threads** (somente classes [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections)).

   Tipos de coleção não genéricas no namespace [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) oferecem algum acesso thread-safe com sincronização; geralmente exposto por meio dos membros `SyncRoot` e `IsSynchronized`. Essas coleções são não thread-safe por padrão. Se você precisar de acesso com multithread escalável e eficiente para uma coleção, use uma das classes no namespace [System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) ou considere usar uma coleção imutável. Para obter mais informações, veja [Coleções thread-safe](threadsafe/index.md).    
    
## <a name="choosing-a-collection"></a>Escolhendo uma coleção 

Em geral, você deve usar coleções genéricas. A tabela a seguir descreve alguns cenários comuns de coleção e as classes de coleção que você pode usar para esses cenários. Se você for inexperiente com coleções genéricas, esta tabela o ajudará a escolher a coleção genérica adequada para a tarefa.

Eu quero… | Opções de coleção genérica | Opções de coleção não genérica
---------- | ---------------------------- | --------------------------------
Armazenar itens como pares chave/valor para consulta rápida por chave | [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) | [Tabela de hash](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable)
Itens de acesso por índice | [System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) | [System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array), [System.Collections.ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList)
Usar itens primeiro a entrar, primeiro a sair (PEPS) | [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) | [System.Collections.Queue](https://docs.microsoft.com/dotnet/core/api/System.Collections.Queue)
Usar dados último a entrar, primeiro a sair (UEPS) | [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) | [System.Collections.Stack](https://docs.microsoft.com/dotnet/core/api/System.Collections.Stack)
Acessar itens em sequência | [System.Collections.Generic.LinkedList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1) | Nenhuma recomendação
Receba notificações quando itens forem removidos da coleção ou adicionados a ela. (implementa [INotifyPropertyChanged](https://docs.microsoft.com/dotnet/core/api/System.ComponentModel.INotifyPropertyChanged) e [INotifyCollectionChanged](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.INotifyCollectionChanged)) | [System.Collections.ObjectModel.ObservableCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.ObservableCollection-1) | Nenhuma recomendação
Usar uma coleção classificada | [System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) | [System.Collections.SortedList](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList)
Gerenciar o armazenamento eficiente e acesso de elementos exclusivos | [System.Collections.Generic.HashSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.HashSet-1), [System.Collections.Generic.SortedSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedSet-1) | Nenhuma recomendação

## <a name="related-topics"></a>Tópicos relacionados

Título | Descrição
----- | -----------
[Selecionando uma Classe de Coleção](selecting-a-collection-class.md) | Descreve as diferentes coleções e ajuda a selecionar uma para o seu cenário.
[Tipos de Coleção de Uso Comum](commonly-used-collection-types.md) | Descreve os tipos de coleção genérica e não genérica usados com frequência, como [System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array), [System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) e [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2). 
[Quando Usar Coleções Genéricas](when-to-use-generic-collections.md) | Descreve o uso de tipos de coleção genérica.
[Comparações e Classificações Dentro de Coleções](comparisons-and-sorts-within-collections.md) | Discute o uso de comparações de igualdade e comparações de classificação em coleções.
[Tipos de Coleção Sorted](sorted-collection-types.md) | Descreve as características e o desempenho de coleções classificadas.
[Tipos de Coleção de Tabela de Hash e Dicionário](hashtable-and-dictionary-collection-types.md) | Descreve os recursos de tipos de dicionário baseado em hash genérico e não genérico.
[Coleções Thread-Safe](threadsafe/index.md) | Descreve tipos de coleção como [System.Collections.Concurrent.BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) e [System.Collections.Concurrent.ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) que oferecem suporte a acesso simultâneo seguro e eficiente de vários threads.

## <a name="reference"></a>Referência

[System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array)

[System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections)

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic)

[System.Collections.Specialized](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized)

[System.Linq](https://docs.microsoft.com/dotnet/core/api/System.Linq)
  

