---
title: Como invocar um método delegado (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: c50a32d300aaf52efe0c55cef69d5793a98305ac
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204598"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Como invocar um método delegado (Visual Basic)
Este exemplo mostra como associar um método com um delegado e, em seguida, chama esse método por meio do delegado.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Criar o delegado e procedimentos correspondentes.  
  
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
  
3.  Definir um método que cria uma instância do delegado e invoca o método associado com o delegado, chamando o interno `Invoke` método.  
  
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

- [Instrução Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
- [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
- [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)  
- [Aplicativos com Multithread](../../../../standard/threading/using-threads-and-threading.md)
