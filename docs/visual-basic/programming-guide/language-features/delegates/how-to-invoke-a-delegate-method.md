---
title: Como invocar um método delegado (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: aca87dd9fa1990d44c99aab7753f2fd7d508adc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Como invocar um método delegado (Visual Basic)
Este exemplo mostra como associar um método um delegado e depois chama esse método por meio do representante.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Crie o delegado e procedimentos correspondentes.  
  
1.  Cria um delegado de nome `MySubDelegate`.  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  Declare uma classe que contém um método com a mesma assinatura do delegado.  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  Definir um método que cria uma instância do delegado e invoca o método associado com o delegado chamando o interno `Invoke` método.  
  
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
 [Instrução Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Aplicativos com Multithread](http://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)
