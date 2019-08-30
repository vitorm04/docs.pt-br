---
title: Usando a variação em delegados (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: ebba7e862e1b4677d9438aa301ef2b713fba3712
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169077"
---
# <a name="using-variance-in-delegates-visual-basic"></a>Usando a variação em delegados (Visual Basic)

Quando você atribui um método a um delegado, a *covariância* e a *contravariância* fornece flexibilidade para corresponder um tipo de delegado a uma assinatura de método. A covariância permite que um método tenha o tipo de retorno mais derivado do que o definido no delegado. A contravariância permite que um método que tem tipos de parâmetro menos derivados do que no tipo delegado.

## <a name="example-1-covariance"></a>Exemplo 1: Covariância

### <a name="description"></a>Descrição

Este exemplo demonstra como delegados podem ser usados com métodos que têm tipos de retorno que são derivados do tipo de retorno na assinatura do delegado. O tipo de dados retornado por `DogsHandler` é do tipo `Dogs`, que deriva do tipo `Mammals` definido no delegado.

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

## <a name="example-2-contravariance"></a>Exemplo 2: Contravariância

### <a name="description"></a>Descrição

Este exemplo demonstra como os delegados podem ser usados com métodos que têm parâmetros cujos tipos são tipos base do tipo de parâmetro de assinatura de representante. Com a contravariância, você pode usar um manipulador de eventos em vez de manipuladores separados. O exemplo a seguir usa dois delegados:

- Um <xref:System.Windows.Forms.KeyEventHandler> delegado que define a assinatura do evento [Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) . Sua assinatura é:

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- Um <xref:System.Windows.Forms.MouseEventHandler> delegado que define a assinatura do evento [Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) . Sua assinatura é:

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

O exemplo define um manipulador de eventos com <xref:System.EventArgs> um parâmetro e o usa para lidar com `Button.KeyDown` os `Button.MouseClick` eventos e. Isso pode fazer isso porque <xref:System.EventArgs> é um tipo base <xref:System.Windows.Forms.KeyEventArgs> de e <xref:System.Windows.Forms.MouseEventArgs>.

### <a name="code"></a>Código

```vb
' Event handler that accepts a parameter of the EventArgs type.
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

- [Variação em delegados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Usando variação para delegados genéricos Func e Action (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
