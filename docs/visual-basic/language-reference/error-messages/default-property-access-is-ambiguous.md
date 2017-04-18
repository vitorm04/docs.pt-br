---
title: "Acesso à propriedade padrão é ambíguo entre os membros de interface herdada&lt;defaultpropertyname&gt;&quot;da interface&quot;&lt;interfacename1&gt;&quot;e&quot;&lt;defaultpropertyname&gt;&quot;da interface&quot;&lt;interfacename2&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30686
- bc30686
dev_langs:
- VB
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 115ed88aa6c0781c452be745365efee04d2ce66d
ms.lasthandoff: 03/13/2017

---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a>Acesso à propriedade padrão é ambíguo entre os membros de interface herdada&lt;defaultpropertyname&gt;'da interface'&lt;interfacename1&gt;'e'&lt;defaultpropertyname&gt;'da interface'&lt;interfacename2&gt;'
Uma interface herda de duas interfaces, cada uma declara uma propriedade padrão com o mesmo nome. O compilador não resolve um acesso a sua propriedade padrão sem qualificação. O exemplo a seguir ilustra essa situação.  
  
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
  
 Quando você especificar `testObj(1)`, o compilador tenta resolvê-lo para a propriedade padrão. No entanto, há duas propriedades padrão possível por causa de interfaces herdadas, para que o compilador sinaliza esse erro.  
  
 **ID do erro:** BC30686  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Evite herdar quaisquer membros com o mesmo nome. No exemplo anterior, se `testObj` não precisa de nenhum dos membros de, digamos, `Iface2`, declare-o da seguinte maneira:  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     -ou-  
  
-   Implemente a interface herda de uma classe. Em seguida, você pode implementar cada uma das propriedades herdadas com nomes diferentes. No entanto, apenas um deles pode ser a propriedade padrão da classe de implementação. O exemplo a seguir ilustra essa situação.  
  
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
