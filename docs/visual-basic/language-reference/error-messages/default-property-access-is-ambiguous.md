---
title: "O acesso &#224; propriedade padr&#227;o &#233; amb&#237;guo entre os membros de interface herdada &#39;&lt;defaultpropertyname&gt;&#39; da interface &#39;&lt;interfacename1&gt;&#39; e &#39;&lt;defaultpropertyname&gt;&#39; da interface &#39;&lt;interfacename2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30686"
  - "bc30686"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30686"
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O acesso &#224; propriedade padr&#227;o &#233; amb&#237;guo entre os membros de interface herdada &#39;&lt;defaultpropertyname&gt;&#39; da interface &#39;&lt;interfacename1&gt;&#39; e &#39;&lt;defaultpropertyname&gt;&#39; da interface &#39;&lt;interfacename2&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma interface herda de duas interfaces, cada uma declara uma propriedade padrão com o mesmo nome.  O compilador não resolve um acesso a sua propriedade padrão sem habilitação.  O exemplo a seguir ilustra isto:  
  
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
  
 Quando você especifica `testObj(1)`, o compiladr tenta resolvê\-lo para a propriedade padrão.  Entretanto, há duas possíveis popriedades padrão devido às interfaces herdadas, de modo que o compilador sinaliza este erro.  
  
 **Identificação do erro:**  BC30686  
  
### Para corrigir este erro  
  
-   Evite herdar quaisquer membros com o mesmo nome.  No exemplo precedente, se `testObj` não precisa de nenhum dos membros de, a saber, `Iface2`, então declare\-o como se segue:  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     \- ou \-  
  
-   Implemente a interface que herda numa classe.  Então você pode implementar cada uma das propriedades herdadas com nomes diferentes.  Entretanto, apenas um deles pode ser a propriedade padrão da classe implementadora.  O exemplo a seguir ilustra isto:  
  
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
  
## Consulte também  
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)