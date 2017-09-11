---
title: "Variação em Interfaces genéricas (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c53c27bdb085213046553fc4b08f11336880a7c2
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="31ae1-102">Variação em Interfaces genéricas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31ae1-102">Variance in Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="31ae1-103">O .NET framework 4 introduziu o suporte de variação de várias interfaces genéricas existentes.</span><span class="sxs-lookup"><span data-stu-id="31ae1-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="31ae1-104">Suporte a variância permite a conversão implícita de classes que implementam essas interfaces.</span><span class="sxs-lookup"><span data-stu-id="31ae1-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="31ae1-105">As seguintes interfaces são variante agora:</span><span class="sxs-lookup"><span data-stu-id="31ae1-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="31ae1-106"><xref:System.Collections.Generic.IEnumerable%601>(T é covariante)</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="31ae1-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="31ae1-107"><xref:System.Collections.Generic.IEnumerator%601>(T é covariante)</xref:System.Collections.Generic.IEnumerator%601></span><span class="sxs-lookup"><span data-stu-id="31ae1-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="31ae1-108"><xref:System.Linq.IQueryable%601>(T é covariante)</xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="31ae1-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="31ae1-109"><xref:System.Linq.IGrouping%602>(`TKey` e `TElement` são covariante)</xref:System.Linq.IGrouping%602></span><span class="sxs-lookup"><span data-stu-id="31ae1-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="31ae1-110"><xref:System.Collections.Generic.IComparer%601>(T é contravariant)</xref:System.Collections.Generic.IComparer%601></span><span class="sxs-lookup"><span data-stu-id="31ae1-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="31ae1-111"><xref:System.Collections.Generic.IEqualityComparer%601>(T é contravariant)</xref:System.Collections.Generic.IEqualityComparer%601></span><span class="sxs-lookup"><span data-stu-id="31ae1-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="31ae1-112"><xref:System.IComparable%601>(T é contravariant)</xref:System.IComparable%601></span><span class="sxs-lookup"><span data-stu-id="31ae1-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="31ae1-113">Covariância permite que um método para ter um tipo de retorno mais derivado daquele definido pelo parâmetro de tipo genérico da interface.</span><span class="sxs-lookup"><span data-stu-id="31ae1-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="31ae1-114">Para ilustrar o recurso de covariância, considere essas interfaces genéricas: `IEnumerable(Of Object)` e `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="31ae1-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="31ae1-115">O `IEnumerable(Of String)` interface não herda o `IEnumerable(Of Object)` interface.</span><span class="sxs-lookup"><span data-stu-id="31ae1-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="31ae1-116">No entanto, o `String` tipo herdam o `Object` tipo e em alguns casos, você talvez queira atribuir objetos dessas interfaces uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="31ae1-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="31ae1-117">Isso é mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="31ae1-117">This is shown in the following code example.</span></span>  
  
<span data-ttu-id="31ae1-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="31ae1-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="31ae1-119">Em versões anteriores do .NET Framework, esse código causa um erro de compilação no Visual Basic com `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="31ae1-119">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="31ae1-120">Mas, agora você pode usar `strings` em vez de `objects`, conforme mostrado no exemplo anterior, porque o <xref:System.Collections.Generic.IEnumerable%601>interface é covariante.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="31ae1-120">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="31ae1-121">Contravariância permite que um método para ter tipos de argumento que são menos derivados que o especificado pelo parâmetro genérico da interface.</span><span class="sxs-lookup"><span data-stu-id="31ae1-121">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="31ae1-122">Para ilustrar contravariância, suponha que você tenha criado um `BaseComparer` classe para comparar instâncias de `BaseClass` classe.</span><span class="sxs-lookup"><span data-stu-id="31ae1-122">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="31ae1-123">O `BaseComparer` classe implementa o `IEqualityComparer(Of BaseClass)` interface.</span><span class="sxs-lookup"><span data-stu-id="31ae1-123">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="31ae1-124">Porque o <xref:System.Collections.Generic.IEqualityComparer%601>interface agora é contravariant, você pode usar `BaseComparer` para comparar instâncias de classes que herdam de `BaseClass` classe</xref:System.Collections.Generic.IEqualityComparer%601></span><span class="sxs-lookup"><span data-stu-id="31ae1-124">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="31ae1-125">Isso é mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="31ae1-125">This is shown in the following code example.</span></span>  
  
<span data-ttu-id="31ae1-126"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="31ae1-126"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="31ae1-127">Para obter mais exemplos, consulte [usando variação em Interfaces para coleções genéricas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="31ae1-127">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="31ae1-128">Variação em interfaces genéricas tem suporte para somente tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="31ae1-128">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="31ae1-129">Tipos de valor não dão suporte a variação.</span><span class="sxs-lookup"><span data-stu-id="31ae1-129">Value types do not support variance.</span></span> <span data-ttu-id="31ae1-130">Por exemplo, `IEnumerable(Of Integer)` não pode ser convertido implicitamente em `IEnumerable(Of Object)`, como inteiros são representados por um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="31ae1-130">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>  
  
<span data-ttu-id="31ae1-131"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="31ae1-131"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="31ae1-132">Também é importante lembrar que as classes que implementam interfaces variantes são ainda invariáveis.</span><span class="sxs-lookup"><span data-stu-id="31ae1-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="31ae1-133">Por exemplo, embora <xref:System.Collections.Generic.List%601>implementa a interface covariante <xref:System.Collections.Generic.IEnumerable%601>, você não pode converter implicitamente `List(Of Object)` para `List(Of String)`.</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="31ae1-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="31ae1-134">Isso é ilustrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="31ae1-134">This is illustrated in the following code example.</span></span>  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a><span data-ttu-id="31ae1-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31ae1-135">See Also</span></span>  
 <span data-ttu-id="31ae1-136">[Usando variação em Interfaces para coleções genéricas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md) </span><span class="sxs-lookup"><span data-stu-id="31ae1-136">[Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md) </span></span>  
<span data-ttu-id="31ae1-137"> [Criando Interfaces genéricas variantes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="31ae1-137"> [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) </span></span>  
<span data-ttu-id="31ae1-138"> [Interfaces genéricas](http://msdn.microsoft.com/library/88bf5b04-d371-4edb-ba38-01ec7cabaacf) </span><span class="sxs-lookup"><span data-stu-id="31ae1-138"> [Generic Interfaces](http://msdn.microsoft.com/library/88bf5b04-d371-4edb-ba38-01ec7cabaacf) </span></span>  
<span data-ttu-id="31ae1-139"> [Variação em delegações (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="31ae1-139"> [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)</span></span>
