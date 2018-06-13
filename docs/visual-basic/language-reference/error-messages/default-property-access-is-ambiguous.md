---
title: Acesso à propriedade padrão é ambíguo entre os membros de interface herdada &#39; &lt;defaultpropertyname&gt; &#39; da interface &#39; &lt;interfacename1&gt; &#39; e &#39; &lt;defaultpropertyname&gt; &#39; da interface &#39; &lt;interfacename2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 65a10067284cad3bf56ecdc441ebefa0a740ef53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590849"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a>Acesso à propriedade padrão é ambíguo entre os membros de interface herdada &#39; &lt;defaultpropertyname&gt; &#39; da interface &#39; &lt;interfacename1&gt; &#39; e &#39; &lt;defaultpropertyname&gt; &#39; da interface &#39; &lt;interfacename2&gt;&#39;
Uma interface herda de duas interfaces, cada uma delas declara uma propriedade padrão com o mesmo nome. O compilador não é possível resolver um acesso de propriedade padrão sem qualificação. O exemplo a seguir ilustra essa situação.  
  
```  
Public Interface Iface1  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface2  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface3  
    Inherits Iface1, Iface2  
End Interface  
Public Class testClass  
    Public Sub accessDefaultProperty()  
        Dim testObj As Iface3  
        Dim testInt As Integer = testObj(1)  
    End Sub  
End Class  
```  
  
 Quando você especificar `testObj(1)`, o compilador tenta resolvê-lo para a propriedade padrão. No entanto, há duas propriedades padrão possíveis devido a interfaces herdadas, para que o compilador sinaliza este erro.  
  
 **ID do erro:** BC30686  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Evite herdar quaisquer membros com o mesmo nome. No exemplo anterior, se `testObj` não precisa de nenhum dos membros de, digamos, `Iface2`, declare-o da seguinte maneira:  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     -ou-  
  
-   Implemente a interface que herda de uma classe. Em seguida, você pode implementar cada uma das propriedades herdadas com nomes diferentes. No entanto, apenas um deles pode ser a propriedade padrão da classe de implementação. O exemplo a seguir ilustra essa situação.  
  
    ```  
    Public Class useIface3  
        Implements Iface3  
        Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop  
            ' Insert code to define Get and Set procedures for prop1.  
        End Property  
        Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop  
            ' Insert code to define Get and Set procedures for prop2.  
        End Property  
    End Class  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
