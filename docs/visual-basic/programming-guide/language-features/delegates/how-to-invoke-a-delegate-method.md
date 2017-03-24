---
title: "Como: chamar um método delegado (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 29b20eb6089886c8111711388472004bbacea312
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Como invocar um método delegado (Visual Basic)
Este exemplo mostra como associar um método um delegado e depois chama esse método por meio do delegado.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Crie o delegado e procedimentos correspondentes.  
  
1.  Criar um delegado chamado `MySubDelegate`.  
  
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
  
3.  Defina um método que cria uma instância do delegado e invoca o método associado com o delegado chamando interna `Invoke` método.  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Instrução delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)   
 [Aplicativos com Multithread](http://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)
