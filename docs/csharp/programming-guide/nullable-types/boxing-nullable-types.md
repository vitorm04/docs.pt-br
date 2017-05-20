---
title: "Executando a Conversão Boxing de Tipos que Permitem Valor Nulo (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: e4ff2e8a31ca5a59494f80597460e90107e78c8a
ms.contentlocale: pt-br
ms.lasthandoff: 03/24/2017

---
# <a name="boxing-nullable-types-c-programming-guide"></a>Executando a conversão boxing de tipos anuláveis (Guia de Programação em C#)
Objetos baseados em tipos que permitem valor nulo serão convertidos somente se o objeto não for nulo. Se <xref:System.Nullable%601.HasValue%2A> for `false`, a referência do objeto será atribuída a `null`, em vez da conversão boxing. Por exemplo:  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 Se o objeto for não nulo – se <xref:System.Nullable%601.HasValue%2A> for `true` –, então, a conversão boxing ocorrerá, mas somente o tipo subjacente no qual o objeto anulável é baseado será convertido. A conversão boxing de um tipo de valor anulável não nulo demarca o próprio tipo de valor e não o <xref:System.Nullable%601?displayProperty=fullName> que encapsula o tipo de valor. Por exemplo:  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 Os dois objetos convertidos são idênticos àqueles criados por meio da conversão boxing de tipos tipo que não permitem valor nulo. Assim como os tipos que não permitem valor nulo convertidos, eles podem ser desconvertidos para tipos que permitem valor nulo, conforme o exemplo a seguir:  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a>Comentários  
 O comportamento de tipos que permitem valor nulo convertidos oferece duas vantagens:  
  
1.  Objetos anuláveis e seus correspondentes convertidos podem ser testados como nulos:  
  
    ```csharp  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  Tipos convertidos que permitem valor nulo oferecem suporte total à funcionalidade do tipo subjacente:  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md)   
 [Como identificar um tipo que permite valor nulo](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
