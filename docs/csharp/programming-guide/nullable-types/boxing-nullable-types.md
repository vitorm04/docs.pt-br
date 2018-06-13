---
title: Executando a conversão boxing de tipos anuláveis (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
ms.openlocfilehash: e2c7602bf45f1861d3a32a73824e9fedf0a4d29d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334750"
---
# <a name="boxing-nullable-types-c-programming-guide"></a>Executando a conversão boxing de tipos anuláveis (Guia de Programação em C#)
Objetos baseados em tipos que permitem valor nulo serão convertidos somente se o objeto não for nulo. Se <xref:System.Nullable%601.HasValue%2A> for `false`, a referência do objeto será atribuída a `null`, em vez da conversão boxing. Por exemplo:  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 Se o objeto for não nulo – se <xref:System.Nullable%601.HasValue%2A> for `true` –, então, a conversão boxing ocorrerá, mas somente o tipo subjacente no qual o objeto anulável é baseado será convertido. A conversão boxing de um tipo de valor anulável não nulo demarca o próprio tipo de valor e não o <xref:System.Nullable%601?displayProperty=nameWithType> que encapsula o tipo de valor. Por exemplo:  
  
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
