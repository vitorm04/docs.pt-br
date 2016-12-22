---
title: "Como invocar um m&#233;todo delegado (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como invocar um m&#233;todo delegado (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como associar um método um delegado e depois chama esse método através do delegado.  
  
### Crie o delegado e procedimentos correspondentes.  
  
1.  Cria um delegado de nome `MySubDelegate`.  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  Declare uma classe que contém um método com a mesma assinatura que o delegado.  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  Definir um método que cria uma instância do delegado e invoca o método associado com o delegado chamando interno `Invoke` método.  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## Consulte também  
 [Instrução Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Eventos](../../../../visual-basic/programming-guide/language-features/events/events.md)   
 [Aplicativos multithread](../Topic/Multithreaded%20Applications%20\(C%23%20and%20Visual%20Basic\).md)