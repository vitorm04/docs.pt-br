---
title: "Varia&#231;&#227;o em Interfaces gen&#233;ricas (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Varia&#231;&#227;o em Interfaces gen&#233;ricas (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O .NET framework 4 introduziu o suporte de variação de várias interfaces genéricas existentes. Suporte a variância permite a conversão implícita de classes que implementam essas interfaces. As seguintes interfaces são variante agora:  
  
-   <xref:System.Collections.Generic.IEnumerable%601> \(T é covariante\)  
  
-   <xref:System.Collections.Generic.IEnumerator%601> \(T é covariante\)  
  
-   <xref:System.Linq.IQueryable%601> \(T é covariante\)  
  
-   <xref:System.Linq.IGrouping%602> \(`TKey` e `TElement` são covariante\)  
  
-   <xref:System.Collections.Generic.IComparer%601> \(T é contravariant\)  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601> \(T é contravariant\)  
  
-   <xref:System.IComparable%601> \(T é contravariant\)  
  
 Covariância permite que um método para ter um tipo de retorno mais derivado daquele definido pelo parâmetro de tipo genérico da interface. Para ilustrar o recurso de covariância, considere essas interfaces genéricas: `IEnumerable(Of Object)` e `IEnumerable(Of String)`. O `IEnumerable(Of String)` interface não herda o `IEnumerable(Of Object)` interface. No entanto, o `String` tipo herdam o `Object` tipo e em alguns casos, você talvez queira atribuir objetos dessas interfaces uns aos outros. Isso é mostrado no exemplo de código a seguir.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Em versões anteriores do .NET Framework, esse código causa um erro de compilação no Visual Basic com `Option Strict On`. Mas, agora você pode usar `strings` em vez de `objects`, como mostrado no exemplo anterior, pois o <xref:System.Collections.Generic.IEnumerable%601> interface é covariante.  
  
 Contravariância permite que um método para ter tipos de argumento que são menos derivados que o especificado pelo parâmetro genérico da interface. Para ilustrar contravariância, suponha que você tenha criado um `BaseComparer` classe para comparar instâncias de `BaseClass` classe. O `BaseComparer` classe implementa o `IEqualityComparer(Of BaseClass)` interface. Porque o <xref:System.Collections.Generic.IEqualityComparer%601> interface agora é contravariant, você pode usar `BaseComparer` para comparar instâncias de classes que herdam de `BaseClass` classe. Isso é mostrado no exemplo de código a seguir.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Para obter mais exemplos, consulte [Usando variação em Interfaces para coleções genéricas \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).  
  
 Variação em interfaces genéricas tem suporte para somente tipos de referência. Tipos de valor não dão suporte a variação. Por exemplo, `IEnumerable(Of Integer)` não pode ser convertido implicitamente em `IEnumerable(Of Object)`, como inteiros são representados por um tipo de valor.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Também é importante lembrar que as classes que implementam interfaces variantes são ainda invariáveis. Por exemplo, embora <xref:System.Collections.Generic.List%601> implementa a interface covariante <xref:System.Collections.Generic.IEnumerable%601>, você não pode converter implicitamente `List(Of Object)` para `List(Of String)`. Isso é ilustrado no exemplo de código a seguir.  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## Consulte também  
 [Usando variação em Interfaces para coleções genéricas \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)   
 [Criando Interfaces genéricas variantes \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)   
 [Interfaces genéricas](../../../../csharp/programming-guide/generics/generic-interfaces.md)   
 [Variação em delegações \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)