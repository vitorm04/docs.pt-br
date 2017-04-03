---
title: "Variação em interfaces genéricas (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4c4f3ab00b4de2a6f38858dd5f332db3d47eb85b
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-generic-interfaces-c"></a>Variância em interfaces genéricas (C#)
O .NET Framework 4 introduziu o suporte à variação para diversas interfaces genéricas existentes. O suporte à variação possibilita a conversão implícita de classes que implementam essas interfaces. As seguintes interfaces agora são variantes:  
  
-   <xref:System.Collections.Generic.IEnumerable%601> (T é covariante)  
  
-   <xref:System.Collections.Generic.IEnumerator%601> (T é covariante)  
  
-   <xref:System.Linq.IQueryable%601> (T é covariante)  
  
-   <xref:System.Linq.IGrouping%602> (`TKey` e `TElement` são covariantes)  
  
-   <xref:System.Collections.Generic.IComparer%601> (T é contravariante)  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601> (T é contravariante)  
  
-   <xref:System.IComparable%601> (T é contravariante)  
  
 A covariância permite que um método tenha um tipo de retorno mais derivados que aquele definidos pelo parâmetro de tipo genérico da interface. Para ilustrar o recurso de covariância, considere estas interfaces genéricas: `IEnumerable<Object>` e `IEnumerable<String>`. A interface `IEnumerable<String>` não herda a interface `IEnumerable<Object>`. No entanto, o tipo `String` herda o tipo `Object` e, em alguns casos, talvez você queira atribuir objetos dessas interfaces uns aos outros. Isso será mostrado no exemplo de código a seguir.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Em versões anteriores do .NET Framework, esse código causa um erro de compilação em C# com `Option Strict On`. Mas agora você pode usar `strings` em vez de `objects`, conforme mostrado no exemplo anterior, porque a interface <xref:System.Collections.Generic.IEnumerable%601> é covariante.  
  
 A contravariância permite que um método tenha tipos de argumentos menos derivados que aquele especificado pelo parâmetro genérico da interface. Para ilustrar a contravariância, suponha que você tenha criado uma classe `BaseComparer` para comparar instâncias da classe `BaseClass`. A classe `BaseComparer` implementa a interface `IEqualityComparer<BaseClass>`. Como a interface <xref:System.Collections.Generic.IEqualityComparer%601> agora é contravariante, você pode usar `BaseComparer` para comparar instâncias de classes que herdam a classe `BaseClass`. Isso será mostrado no exemplo de código a seguir.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Para ver mais exemplos, consulte [Usando variação em interfaces para coleções genéricas (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).  
  
 A variação em interfaces genéricas tem suporte somente para tipos de referência. Tipos de valor não dão suporte à variação. Por exemplo, `IEnumerable<int>` não pode ser convertido implicitamente em `IEnumerable<object>`, porque inteiros são representados por um tipo de valor.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Também é importante lembrar que as classes que implementam interfaces variantes ainda são invariantes. Por exemplo, embora <xref:System.Collections.Generic.List%601> implemente a interface covariante <xref:System.Collections.Generic.IEnumerable%601>, você não pode converter implicitamente `List<Object>` em `List<String>`. Isso é ilustrado no exemplo de código a seguir.  
  
```cs  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a>Consulte também  
 [Usando variação em interfaces para Coleções Genéricas (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)   
 [Criando interfaces genéricas variantes (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)   
 [Interfaces Genéricas](http://msdn.microsoft.com/library/88bf5b04-d371-4edb-ba38-01ec7cabaacf)   
 [Variação em delegados (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
