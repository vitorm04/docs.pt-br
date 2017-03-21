---
title: "Usando variação em delegações (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5bd3e60031eac713cee3dee1399af8c6b83e6656
ms.lasthandoff: 03/13/2017

---
# <a name="using-variance-in-delegates-visual-basic"></a>Usando variação em delegações (Visual Basic)
Quando você atribui um método a um delegado, *covariância* e *contravariância* fornecem flexibilidade para corresponder a um tipo de delegado com uma assinatura de método. Covariância permite que um método para ter o tipo de retorno que seja mais derivado daquele definido no delegado. Contravariância permite que um método que possui tipos de parâmetro que são menos derivados no tipo delegado.  
  
## <a name="example-1-covariance"></a>Exemplo 1: covariância  
  
### <a name="description"></a>Descrição  
 Este exemplo demonstra como delegados podem ser usados com métodos que têm tipos de retorno que são derivados do tipo de retorno na assinatura do delegado. O tipo de dados retornado por `DogsHandler` é do tipo `Dogs`, que deriva de `Mammals` tipo definido no delegado.  
  
### <a name="code"></a>Código  
  
```vb  
Class Mammals  
End Class  
  
Class Dogs  
    Inherits Mammals  
End Class  
Class Test  
    Public Delegate Function HandlerMethod() As Mammals  
    Public Shared Function MammalsHandler() As Mammals  
        Return Nothing  
    End Function  
    Public Shared Function DogsHandler() As Dogs  
        Return Nothing  
    End Function  
    Sub Test()  
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler  
        ' Covariance enables this assignment.  
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler  
    End Sub  
End Class  
```  
  
## <a name="example-2-contravariance"></a>Exemplo 2: contravariância  
  
### <a name="description"></a>Descrição  
 Este exemplo demonstra como delegados podem ser usados com métodos que têm parâmetros de um tipo que são tipos base do tipo de parâmetro de assinatura do delegado. Com contravariância, você pode usar um manipulador de eventos em vez de manipuladores separados. Por exemplo, você pode criar um manipulador de eventos que aceita um `EventArgs` parâmetro de entrada e usá-la com um `Button.MouseClick` eventos que envia uma `MouseEventArgs` tipo como um parâmetro e também com um `TextBox.KeyDown` eventos que envia um `KeyEventArgs` parâmetro.  
  
### <a name="code"></a>Código  
  
```vb  
' Event hander that accepts a parameter of the EventArgs type.  
Private Sub MultiHandler(ByVal sender As Object,  
                         ByVal e As System.EventArgs)  
    Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Form1_Load(ByVal sender As System.Object,  
    ByVal e As System.EventArgs) Handles MyBase.Load  
  
    ' You can use a method that has an EventArgs parameter,  
    ' although the event expects the KeyEventArgs parameter.  
    AddHandler Button1.KeyDown, AddressOf MultiHandler  
  
    ' You can use the same method   
    ' for the event that expects the MouseEventArgs parameter.  
    AddHandler Button1.MouseClick, AddressOf MultiHandler  
End Sub  
```  
  
## <a name="see-also"></a>Consulte também  
 [Variação em delegações (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)   
 [Usando variação para delegações Func e Action genérica (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
