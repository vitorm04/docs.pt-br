---
title: "Executando operações de cadeia de caracteres que não levam em conta a cultura em coleções"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CaseInsensitiveComparer class, using
- CollectionsUtil.CreateCaseInsensitiveHashtable method
- culture-insensitive string operations, collections
- collections [.NET Framework], culture-insensitive string operations
- CaseInsensitiveHashCodeProvider class, using
- ArrayList.Sort method
- SortedList class, culture-insensitive string operations
- culture parameter
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1ecba9c055f8e99d26283c7f37c2430dc17bf31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="45b9a-102">Executando operações de cadeia de caracteres que não levam em conta a cultura em coleções</span><span class="sxs-lookup"><span data-stu-id="45b9a-102">Performing Culture-Insensitive String Operations in Collections</span></span>
<span data-ttu-id="45b9a-103">Há classes e membros de <xref:System.Collections> namespace que fornece o comportamento de sensíveis à cultura por padrão.</span><span class="sxs-lookup"><span data-stu-id="45b9a-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="45b9a-104">Os construtores padrão para o <xref:System.Collections.CaseInsensitiveComparer> e <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes inicializar uma nova instância usando o <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="45b9a-104">The default constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="45b9a-105">Todas as sobrecargas do <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> método cria uma nova instância do <xref:System.Collections.Hashtable> classe usando o `Thread.CurrentCulture` propriedade por padrão.</span><span class="sxs-lookup"><span data-stu-id="45b9a-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="45b9a-106">Sobrecargas do <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> método executa classificações de cultura usando padrão `Thread.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="45b9a-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="45b9a-107">Classificação e pesquisa em uma <xref:System.Collections.SortedList> pode ser afetado por `Thread.CurrentCulture` quando as cadeias de caracteres são usadas como as chaves.</span><span class="sxs-lookup"><span data-stu-id="45b9a-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="45b9a-108">Siga as recomendações de uso fornecidas nesta seção para obter os resultados não levam em conta a cultura de classes e métodos de `Collections` namespace.</span><span class="sxs-lookup"><span data-stu-id="45b9a-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>  
  
 <span data-ttu-id="45b9a-109">**Observação** passando <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> para uma comparação método realizar uma comparação sem diferenciação de cultura.</span><span class="sxs-lookup"><span data-stu-id="45b9a-109">**Note** Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="45b9a-110">No entanto, ele não causa uma comparação não linguística, por exemplo, para caminhos de arquivos, chaves do registro e variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="45b9a-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="45b9a-111">Não oferece suporte a decisões de segurança com base no resultado da comparação.</span><span class="sxs-lookup"><span data-stu-id="45b9a-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="45b9a-112">Para obter uma comparação não linguística ou suporte para decisões de segurança com base no resultado, o aplicativo deve usar um método de comparação que aceita um <xref:System.StringComparison> valor.</span><span class="sxs-lookup"><span data-stu-id="45b9a-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="45b9a-113">O aplicativo deve passar <xref:System.StringComparison>.</span><span class="sxs-lookup"><span data-stu-id="45b9a-113">The application should then pass <xref:System.StringComparison>.</span></span>  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="45b9a-114">Usando as Classes de CaseInsensitiveHashCodeProvider e CaseInsensitiveComparer</span><span class="sxs-lookup"><span data-stu-id="45b9a-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>  
 <span data-ttu-id="45b9a-115">Os construtores padrão `CaseInsensitiveHashCodeProvider` e `CaseInsensitiveComparer` inicializar uma nova instância da classe usando o `Thread.CurrentCulture`, resultando no comportamento sensíveis à cultura.</span><span class="sxs-lookup"><span data-stu-id="45b9a-115">The default constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="45b9a-116">O exemplo de código a seguir demonstra o construtor para um `Hashtable` que é sensíveis à cultura, pois ele usa os construtores padrão `CaseInsensitiveHashCodeProvider` e `CaseInsensitiveComparer`.</span><span class="sxs-lookup"><span data-stu-id="45b9a-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the default constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 <span data-ttu-id="45b9a-117">Se você quiser criar uma cultura não diferencia `Hashtable` usando o `CaseInsensitiveComparer` e `CaseInsensitiveHashCodeProvider` classes, inicializar novas instâncias dessas classes usando os construtores que aceitam um `culture` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="45b9a-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="45b9a-118">Para o `culture` parâmetro, especifique <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="45b9a-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="45b9a-119">O exemplo de código a seguir demonstra o construtor para uma cultura não diferencia `Hashtable`.</span><span class="sxs-lookup"><span data-stu-id="45b9a-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(New  
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),  
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))  
```  
  
```csharp  
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider  
    (CultureInfo.InvariantCulture),   
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));  
```  
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="45b9a-120">Usando o método CollectionsUtil</span><span class="sxs-lookup"><span data-stu-id="45b9a-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>  
 <span data-ttu-id="45b9a-121">O `CollectionsUtil.CreateCaseInsensitiveHashTable` método é um atalho útil para criar uma nova instância do `Hashtable` classe que diferencia maiusculas de minúsculas de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="45b9a-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="45b9a-122">No entanto, todas as sobrecargas do `CollectionsUtil.CreateCaseInsensitiveHashTable` método são sensíveis à cultura, porque eles usam o `Thread.CurrentCulture` propriedade.</span><span class="sxs-lookup"><span data-stu-id="45b9a-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="45b9a-123">Não é possível criar uma cultura não diferencia `Hashtable` usando esse método.</span><span class="sxs-lookup"><span data-stu-id="45b9a-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="45b9a-124">Para criar uma cultura não diferencia `Hashtable`, use o `Hashtable` construtor que aceite um `culture` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="45b9a-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="45b9a-125">Para o `culture` parâmetro, especifique `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="45b9a-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="45b9a-126">O exemplo de código a seguir demonstra o construtor para uma cultura não diferencia `Hashtable`.</span><span class="sxs-lookup"><span data-stu-id="45b9a-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(New  
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),  
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))  
```  
  
```csharp  
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider  
    (CultureInfo.InvariantCulture),   
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));  
```  
  
<a name="cpconperformingculture-insensitivestringoperationsincollectionsanchor1"></a>   
## <a name="using-the-sortedlist-class"></a><span data-ttu-id="45b9a-127">Usando a classe SortedList</span><span class="sxs-lookup"><span data-stu-id="45b9a-127">Using the SortedList Class</span></span>  
 <span data-ttu-id="45b9a-128">Um `SortedList` representa uma coleção de pares chave-valor que são classificados pelas chaves e são acessíveis por chave e por índice.</span><span class="sxs-lookup"><span data-stu-id="45b9a-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="45b9a-129">Quando você usa um `SortedList` onde as chaves de cadeias de caracteres, a classificação e a pesquisa podem ser afetados pelo `Thread.CurrentCulture` propriedade.</span><span class="sxs-lookup"><span data-stu-id="45b9a-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="45b9a-130">Para obter o comportamento de cultura de um `SortedList`, crie um `SortedList` usando um dos construtores que aceita um `comparer` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="45b9a-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="45b9a-131">O `comparer` parâmetro especifica o <xref:System.Collections.IComparer> implementação para uso na comparação entre chaves.</span><span class="sxs-lookup"><span data-stu-id="45b9a-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="45b9a-132">Para o parâmetro, especifique uma classe de comparador personalizado que usa `CultureInfo.InvariantCulture` para comparar as chaves.</span><span class="sxs-lookup"><span data-stu-id="45b9a-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="45b9a-133">O exemplo a seguir ilustra uma classe de comparador sem diferenciação de cultura personalizada que você pode especificar como o `comparer` parâmetro para um `SortedList` construtor.</span><span class="sxs-lookup"><span data-stu-id="45b9a-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>  
  
```vb  
Imports System  
Imports System.Collections  
Imports System.Globalization  
  
Friend Class InvariantComparer  
    Implements IComparer   
    Private m_compareInfo As CompareInfo  
    Friend Shared [Default] As New InvariantComparer()  
  
    Friend Sub New()  
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo  
    End Sub     
  
    Public Function Compare(a As Object, b As Object) As Integer _  
            Implements IComparer.Compare  
        Dim sa As String = CType(a, String)  
        Dim sb As String = CType(b, String)  
        If Not (sa Is Nothing) And Not (sb Is Nothing) Then  
            Return m_compareInfo.Compare(sa, sb)  
        Else  
            Return Comparer.Default.Compare(a, b)  
        End If  
    End Function  
End Class  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Globalization;  
  
internal class InvariantComparer : IComparer   
{  
    private CompareInfo m_compareInfo;  
    internal static readonly InvariantComparer Default = new  
        InvariantComparer();  
  
    internal InvariantComparer()   
    {  
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo;  
    }  
  
    public int Compare(Object a, Object b)  
    {  
        String sa = a as String;  
        String sb = b as String;  
        if (sa != null && sb != null)  
            return m_compareInfo.Compare(sa, sb);  
        else  
            return Comparer.Default.Compare(a,b);  
    }  
}  
```  
  
 <span data-ttu-id="45b9a-134">Em geral, se você usar um `SortedList` em cadeias de caracteres sem especificar um comparador personalizado invariável, uma alteração `Thread.CurrentCulture` depois que a lista foi preenchida pode invalidar a lista.</span><span class="sxs-lookup"><span data-stu-id="45b9a-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>  
  
## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="45b9a-135">Usando o método ArrayList</span><span class="sxs-lookup"><span data-stu-id="45b9a-135">Using the ArrayList.Sort Method</span></span>  
 <span data-ttu-id="45b9a-136">Sobrecargas do `ArrayList.Sort` método executa classificações de sensíveis à cultura por padrão usando o `Thread.CurrentCulture` propriedade.</span><span class="sxs-lookup"><span data-stu-id="45b9a-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="45b9a-137">Podem variar com a cultura devido a diferentes ordens de classificação.</span><span class="sxs-lookup"><span data-stu-id="45b9a-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="45b9a-138">Para eliminar o comportamento de sensíveis à cultura, use as sobrecargas do método que aceitem um `IComparer` implementação.</span><span class="sxs-lookup"><span data-stu-id="45b9a-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="45b9a-139">Para o `comparer` parâmetro, especifique uma classe de comparador invariável personalizado que usa `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="45b9a-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="45b9a-140">Um exemplo de uma classe personalizada comparador invariável é fornecido no [usando a classe SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) tópico.</span><span class="sxs-lookup"><span data-stu-id="45b9a-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45b9a-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45b9a-141">See Also</span></span>  
 <xref:System.Collections.CaseInsensitiveComparer>  
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Collections.SortedList>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="45b9a-142">Executando operações de cadeia de caracteres que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="45b9a-142">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
