---
title: Comparações e classificações dentro de coleções
description: As comparações & classificações usando as classes System. Collections no .NET, que ajudam a localizar um elemento para remover ou retornar o valor de um par de chave e valor.
ms.date: 04/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
ms.openlocfilehash: aa001e8469947a532d77059bd52024c6b47b508e
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769191"
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="2f1ab-103">Comparações e classificações dentro de coleções</span><span class="sxs-lookup"><span data-stu-id="2f1ab-103">Comparisons and sorts within collections</span></span>

<span data-ttu-id="2f1ab-104">As classes <xref:System.Collections> executam comparações em quase todos os processos envolvidos no gerenciamento de coleções, seja procura pelo elemento para remoção ou retorno do valor de um par de chaves e valores.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-104">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>

<span data-ttu-id="2f1ab-105">As coleções normalmente usam um comparador de igualdade e/ou um comparador de ordenação.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-105">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="2f1ab-106">Dois constructos são usados para comparações.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-106">Two constructs are used for comparisons.</span></span>

<a name="BKMK_Checkingforequality"></a>
## <a name="check-for-equality"></a><span data-ttu-id="2f1ab-107">Verificar igualdade</span><span class="sxs-lookup"><span data-stu-id="2f1ab-107">Check for equality</span></span>

<span data-ttu-id="2f1ab-108">Métodos como `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A> e `Remove` usam um comparador de igualdade para os elementos da coleção.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-108">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="2f1ab-109">Se a coleção for genérica, os itens serão comparados para igualdade de acordo com as seguintes diretrizes:</span><span class="sxs-lookup"><span data-stu-id="2f1ab-109">If the collection is generic, then items are compared for equality according to the following guidelines:</span></span>

- <span data-ttu-id="2f1ab-110">Se o tipo T implementa a interface genérica <xref:System.IEquatable%601>, então o comparador de igualdade será o método <xref:System.IEquatable%601.Equals%2A> dessa interface.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-110">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>

- <span data-ttu-id="2f1ab-111">Se o tipo T não implementar <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> será usado.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-111">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>

<span data-ttu-id="2f1ab-112">Além disso, algumas sobrecargas de construtores para coleções de dicionários aceitam uma implementação <xref:System.Collections.Generic.IEqualityComparer%601>, que é usada para comparar chaves com relação à igualdade.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-112">In addition, some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="2f1ab-113">Para ver um exemplo, consulte o construtor <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-113">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A> constructor.</span></span>

<a name="BKMK_Determiningsortorder"></a>
## <a name="determine-sort-order"></a><span data-ttu-id="2f1ab-114">Determinar ordem de classificação</span><span class="sxs-lookup"><span data-stu-id="2f1ab-114">Determine sort order</span></span>

<span data-ttu-id="2f1ab-115">Métodos como `BinarySearch` e `Sort` usam um comparador de ordenação para os elementos da coleção.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-115">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="2f1ab-116">As comparações podem ser entre elementos da coleção ou entre um elemento e um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-116">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="2f1ab-117">Para comparar objetos, há o conceito de um `default comparer` e um `explicit comparer`.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-117">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>

<span data-ttu-id="2f1ab-118">O comparador padrão baseia-se em pelo menos um dos objetos que estão sendo comparados para implementar a interface **IComparable**.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-118">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="2f1ab-119">É uma boa prática implementar **IComparable** em todas as classes usadas como valores em uma coleção de lista ou como chaves em uma coleção de dicionário.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-119">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="2f1ab-120">Para uma coleção genérica, a comparação de igualdade é determinada de acordo com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2f1ab-120">For a generic collection, equality comparison is determined according to the following:</span></span>

- <span data-ttu-id="2f1ab-121">Se o tipo T implementa a interface genérica <xref:System.IComparable%601?displayProperty=nameWithType>, então o comparador padrão será o método <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> dessa interface.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-121">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>

- <span data-ttu-id="2f1ab-122">Se o tipo T implementa a interface não genérica <xref:System.IComparable?displayProperty=nameWithType>, então o comparador padrão será o método <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> dessa interface.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-122">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>

- <span data-ttu-id="2f1ab-123">Se o tipo T não implementa a interface, não há nenhum comparador padrão, e um representante de comparação ou comparador deve ser fornecido explicitamente.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-123">If type T doesn't implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>

<span data-ttu-id="2f1ab-124">Para fornecer comparações explícitas, alguns métodos aceitam uma implementação de **IComparer** como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-124">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="2f1ab-125">Por exemplo, o método <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> aceita uma implementação <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-125">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>

<span data-ttu-id="2f1ab-126">A configuração de cultura atual do sistema pode afetar as comparações e as classificações dentro de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-126">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="2f1ab-127">Por padrão, as comparações e classificações nas classes **Collections** levam em conta a cultura.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-127">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="2f1ab-128">Para ignorar a configuração de cultura e assim obter comparação consistente e classificar os resultados, use o <xref:System.Globalization.CultureInfo.InvariantCulture%2A> com sobrecargas de membros que aceitam uma <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-128">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="2f1ab-129">Para obter mais informações, consulte [Executando operações de cadeia de caracteres que não levam em conta a cultura em coleções](../globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) e [Executando operações de cadeia de caracteres que não levam em conta a cultura em matrizes](../globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="2f1ab-129">For more information, see [Performing Culture-Insensitive String Operations in Collections](../globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>

<a name="BKMK_Equalityandsortexample"></a>
## <a name="equality-and-sort-example"></a><span data-ttu-id="2f1ab-130">Exemplo de igualdade e classificação</span><span class="sxs-lookup"><span data-stu-id="2f1ab-130">Equality and sort example</span></span>

<span data-ttu-id="2f1ab-131">O código a seguir demonstra uma implementação de <xref:System.IEquatable%601> e <xref:System.IComparable%601> em um objeto de negócios simples.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-131">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="2f1ab-132">Além disso, quando o objeto é armazenado em uma lista e classificado, você verá que chamar o método <xref:System.Collections.Generic.List%601.Sort> resulta no uso do comparador padrão para o tipo `Part` e o método <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> implementado usando um método anônimo.</span><span class="sxs-lookup"><span data-stu-id="2f1ab-132">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>

[!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
[!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="2f1ab-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="2f1ab-133">See also</span></span>

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
