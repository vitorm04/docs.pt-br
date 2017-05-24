---
title: "Coleções e estruturas de dados | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grouping data in collections
- objects [.NET Framework], grouping in collections
- Array class, grouping data in collections
- threading [.NET Framework], safety
- Collections classes
- collections [.NET Framework]
ms.assetid: 60cc581f-1db5-445b-ba04-a173396bf872
caps.latest.revision: 36
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: c50b3e328998b65ec47efe6d7457b36116813c77
ms.openlocfilehash: 27c475b8d29eb295bb3d6be24aa9ee9188f5c114
ms.contentlocale: pt-br
ms.lasthandoff: 04/08/2017

---
# <a name="collections-and-data-structures"></a>Coleções e estruturas de dados
Dados semelhantes podem normalmente ser tratados com mais eficiência quando armazenados e manipulados como uma coleção. Você pode usar a classe <xref:System.Array?displayProperty=fullName> ou as classes nos namespaces <xref:System.Collections>, <xref:System.Collections.Generic>, <xref:System.Collections.Concurrent>, System.Collections.Immutable para adicionar, remover e modificar elementos individuais ou um intervalo de elementos em uma coleção.  
  
 Há dois tipos principais de coleções; coleções genéricas e coleções não genéricas. Coleções genéricas foram adicionadas ao .NET Framework 2.0 e fornecem coleções que são fortemente tipadas no tempo de compilação. Por isso, coleções genéricas normalmente oferecem melhor desempenho. As coleções genéricas aceitam um parâmetro de tipo quando são construídas e não exigem que você converta bidirecionalmente o tipo <xref:System.Object> ao adicionar ou remover itens da coleção.  Além disso, a maioria das coleções genéricas tem suporte nos aplicativos [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)]. As coleções não genéricas armazenam itens como <xref:System.Object>, exigem conversão e a maioria não é compatível para desenvolvimento de aplicativos da [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)]. No entanto, você pode ver as coleções não genéricas no código mais antigo.  
  
 A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], as coleções no namespace <xref:System.Collections.Concurrent> fornecem operações thread-safe eficientes para acessar itens da coleção de vários threads. As classes de coleção imutáveis no namespace System.Collections.Immutable ([NuGet package](https://www.nuget.org/packages/System.Collections.Immutable)) são inerentemente thread-safe, pois as operações são executadas em uma cópia da coleção original e a coleção original não pode ser modificada.  
  
  
<a name="BKMK_Commoncollectionfeatures"></a>   
## <a name="common-collection-features"></a>Recursos comuns de coleção  
 Todas as coleções fornecem métodos para adicionar, remover ou localizar itens na coleção. Além disso, todas as coleções que direta ou indiretamente implementam a interface <xref:System.Collections.ICollection> ou a interface <xref:System.Collections.Generic.ICollection%601> compartilham estes recursos:  
  
-   **A capacidade de enumerar a coleção**  
  
     As coleções do .NET Framework implementam <xref:System.Collections.IEnumerable?displayProperty=fullName> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> para permitir a iteração da coleção. Um enumerador pode ser considerado um ponteiro móvel para qualquer elemento da coleção. A instrução [foreach, in](~/docs/csharp/language-reference/keywords/foreach-in.md) e a instrução [For Each...Next](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) usam o enumerador exposto pelo método <xref:System.Collections.IEnumerable.GetEnumerator%2A> e ocultam a complexidade de manipular o enumerador. Além disso, qualquer coleção que implemente <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> é considerada um *tipo passível de consulta* e pode ser consultada com LINQ. Consultas LINQ fornecem um padrão comum para o acesso de dados. Elas são geralmente mais concisas e legíveis que loops `foreach` padrão e fornecem filtragem, classificação e agrupamento de recursos. Consultas LINQ também podem melhorar o desempenho. Para saber mais, confira [LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9), [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md) e [Introdução a consultas LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
-   **A capacidade de copiar o conteúdo da coleção para uma matriz**  
  
     Todas as coleções podem ser copiadas para uma matriz usando o método **CopyTo**; no entanto, a ordem dos elementos na nova matriz se baseia na sequência na qual o enumerador os retorna. A matriz resultante é sempre unidimensional com um limite inferior de zero.  
  
 Além disso, muitas classes de coleção contêm os seguintes recursos:  
  
-   **Propriedades de capacidade e contagem**  
  
     A capacidade de uma coleção é o número de elementos que ela pode conter. A contagem de uma coleção é o número de elementos que ela realmente contém. Algumas coleções ocultam a capacidade ou a contagem ou ambas.  
  
     A maioria das coleções se expande automaticamente em capacidade quando a capacidade atual é atingida. A memória é realocada e os elementos são copiados da coleção antiga para a nova. Isso reduz o código necessário para usar a coleção; no entanto, o desempenho da coleção pode ser afetado de forma negativa. Por exemplo, para <xref:System.Collections.Generic.List%601>, se <xref:System.Collections.Generic.List%601.Count%2A> for menor que <xref:System.Collections.Generic.List%601.Capacity%2A>, adicionar um item é uma operação O(1). Se a capacidade precisar ser aumentada para acomodar o novo elemento, adicionar um item se tornar uma operação O(n), em que n é <xref:System.Collections.Generic.List%601.Count%2A>. A melhor maneira de evitar um desempenho ruim causado por várias realocações é definir a capacidade inicial para que seja o tamanho estimado da coleção.  
  
     Uma <xref:System.Collections.BitArray> é um caso especial; sua capacidade é a mesma que seu comprimento, que é o mesmo de sua contagem.  
  
-   **Um limite inferior consistente**  
  
     O limite inferior de uma coleção é o índice do seu primeiro elemento. Todas as coleções indexadas nos namespaces <xref:System.Collections> têm um limite inferior de zero, indicando que são indexados em 0. <xref:System.Array> tem um limite inferior de zero por padrão, mas um limite inferior diferente pode ser definido durante a criação de uma instância da classe **Array** usando <xref:System.Array.CreateInstance%2A?displayProperty=fullName>.  
  
-   **Sincronização para acesso de vários threads** (somente classes <xref:System.Collections>).  
  
     Os tipos de coleção não genérica no namespace <xref:System.Collections> fornecem algum acesso thread-safe com sincronização; geralmente expostos por meio dos membros <xref:System.Collections.ICollection.SyncRoot%2A> e <xref:System.Collections.ICollection.IsSynchronized%2A>. Essas coleções são não thread-safe por padrão. Se você precisar de acesso multithread escalonável e eficiente a uma coleção, use uma das classes no namespace <xref:System.Collections.Concurrent> ou considere usar uma coleção imutável. Para obter mais informações, veja [Coleções thread-safe](../../../docs/standard/collections/thread-safe/index.md).  
  
<a name="BKMK_Choosingacollection"></a>   
## <a name="choosing-a-collection"></a>Escolhendo uma coleção  
 Em geral, você deve usar coleções genéricas. A tabela a seguir descreve alguns cenários comuns de coleção e as classes de coleção que você pode usar para esses cenários. Se você for inexperiente com coleções genéricas, esta tabela o ajudará a escolher a coleção genérica adequada para a tarefa.  
<!-- todo: All code-formatted API refs in the table need to be changed into links -->  
|Eu quero…|Opções de coleção genérica|Opções de coleção não genérica|Opções de coleção thread-safe ou imutável|  
|-|-|-|-|  
|Armazenar itens como pares chave/valor para consulta rápida por chave|<xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>|<xref:System.Collections.Hashtable><br /><br /> (Um conjunto de pares chave/valor que são organizados com base no código hash da chave).|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=fullName><br /><br /> `ImmutableDictionary(TKey, TValue) Class`|  
|Itens de acesso por índice|<xref:System.Collections.Generic.List%601?displayProperty=fullName>|<xref:System.Array?displayProperty=fullName><br /><br /> <xref:System.Collections.ArrayList?displayProperty=fullName>|`ImmutableList(T) Class`<br /><br /> `ImmutableArray Class`|  
|Usar itens primeiro a entrar, primeiro a sair (PEPS)|<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>|<xref:System.Collections.Queue?displayProperty=fullName>|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName><br /><br /> `ImmutableQueue(T) Class`|  
|Usar dados último a entrar, primeiro a sair (UEPS)|<xref:System.Collections.Generic.Stack%601?displayProperty=fullName>|<xref:System.Collections.Stack?displayProperty=fullName>|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName><br /><br /> `ImmutableStack(T) Class`|  
|Acessar itens em sequência|<xref:System.Collections.Generic.LinkedList%601?displayProperty=fullName>|Nenhuma recomendação|Nenhuma recomendação|  
|Receba notificações quando itens forem removidos da coleção ou adicionados a ela. (implementa <xref:System.ComponentModel.INotifyPropertyChanged> e <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=fullName>)|<xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=fullName>|Nenhuma recomendação|Nenhuma recomendação|  
|Uma coleção classificada|<xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>|<xref:System.Collections.SortedList?displayProperty=fullName>|`ImmutableSortedDictionary(TKey, TValue) Class`<br /><br /> `ImmutableSortedSet(T) Class`|  
|Um conjunto de funções matemáticas|<xref:System.Collections.Generic.HashSet%601?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName>|Nenhuma recomendação|`ImmutableHashSet(T) Class`<br /><br /> `ImmutableSortedSet(T) Class`|  
  
<a name="BKMK_RelatedTopics"></a>   
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Selecionando uma Classe de Coleção](../../../docs/standard/collections/selecting-a-collection-class.md)|Descreve as diferentes coleções e ajuda a selecionar uma para o seu cenário.|  
|[Tipos de Coleção de Uso Comum](../../../docs/standard/collections/commonly-used-collection-types.md)|Descreve tipos de coleção genérica e não genérica frequentemente usados como <xref:System.Array?displayProperty=fullName>, <xref:System.Collections.Generic.List%601?displayProperty=fullName> e <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>.|  
|[Quando Usar Coleções Genéricas](../../../docs/standard/collections/when-to-use-generic-collections.md)|Descreve o uso de tipos de coleção genérica.|  
|[Comparações e Classificações Dentro de Coleções](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|Discute o uso de comparações de igualdade e comparações de classificação em coleções.|  
|[Tipos de Coleção Sorted](../../../docs/standard/collections/sorted-collection-types.md)|Descreve as características e o desempenho de coleções classificadas|  
|[Tipos de Coleção de Tabela de Hash e Dicionário](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Descreve os recursos de tipos de dicionário baseado em hash genérico e não genérico.|  
|[Coleções Thread-Safe](../../../docs/standard/collections/thread-safe/index.md)|Descreve tipos de coleção como <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> e <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName> que dão suporte a acesso simultâneo seguro e eficiente de vários threads.|  
|System.Collections.Immutable|Apresenta as coleções imutáveis e fornece links para os tipos de coleção.|  
  
<a name="BKMK_Reference"></a>   
## <a name="reference"></a>Referência  
 <xref:System.Array?displayProperty=fullName>  
  
 <xref:System.Collections?displayProperty=fullName>  
  
 <xref:System.Collections.Concurrent?displayProperty=fullName>  
  
 <xref:System.Collections.Generic?displayProperty=fullName>  
  
 <xref:System.Collections.Specialized?displayProperty=fullName>  
  
 <xref:System.Linq?displayProperty=fullName>  
  
 System.Collections.Immutable
