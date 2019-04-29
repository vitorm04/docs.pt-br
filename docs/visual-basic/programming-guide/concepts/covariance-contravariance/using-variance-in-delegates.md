---
title: Usando variação em delegados (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: 19eb3070c1b8359a4eb050e7cf2f16622f66ebe9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787251"
---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="5b525-102">Usando variação em delegados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b525-102">Using Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="5b525-103">Quando você atribui um método a um delegado, a *covariância* e a *contravariância* fornece flexibilidade para corresponder um tipo de delegado a uma assinatura de método.</span><span class="sxs-lookup"><span data-stu-id="5b525-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="5b525-104">A covariância permite que um método tenha o tipo de retorno mais derivado do que o definido no delegado.</span><span class="sxs-lookup"><span data-stu-id="5b525-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="5b525-105">A contravariância permite que um método que tem tipos de parâmetro menos derivados do que no tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="5b525-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>

## <a name="example-1-covariance"></a><span data-ttu-id="5b525-106">Exemplo 1: Covariância</span><span class="sxs-lookup"><span data-stu-id="5b525-106">Example 1: Covariance</span></span>

### <a name="description"></a><span data-ttu-id="5b525-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b525-107">Description</span></span>

<span data-ttu-id="5b525-108">Este exemplo demonstra como delegados podem ser usados com métodos que têm tipos de retorno que são derivados do tipo de retorno na assinatura do delegado.</span><span class="sxs-lookup"><span data-stu-id="5b525-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="5b525-109">O tipo de dados retornado por `DogsHandler` é do tipo `Dogs`, que deriva do tipo `Mammals` definido no delegado.</span><span class="sxs-lookup"><span data-stu-id="5b525-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>

### <a name="code"></a><span data-ttu-id="5b525-110">Código</span><span class="sxs-lookup"><span data-stu-id="5b525-110">Code</span></span>

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

## <a name="example-2-contravariance"></a><span data-ttu-id="5b525-111">Exemplo 2: Contravariância</span><span class="sxs-lookup"><span data-stu-id="5b525-111">Example 2: Contravariance</span></span>

### <a name="description"></a><span data-ttu-id="5b525-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b525-112">Description</span></span>

<span data-ttu-id="5b525-113">Este exemplo demonstra como delegados podem ser usados com métodos que têm parâmetros de um tipo que são tipos base do tipo de parâmetro de assinatura do delegado.</span><span class="sxs-lookup"><span data-stu-id="5b525-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="5b525-114">Com a contravariância, você pode usar um manipulador de eventos em vez de manipuladores separados.</span><span class="sxs-lookup"><span data-stu-id="5b525-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="5b525-115">Por exemplo, você pode criar um manipulador de eventos que aceita um parâmetro de entrada `EventArgs` e usá-lo com um evento `Button.MouseClick` que envia um tipo `MouseEventArgs` como um parâmetro e também com um evento `TextBox.KeyDown` que envia um parâmetro `KeyEventArgs`.</span><span class="sxs-lookup"><span data-stu-id="5b525-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>

### <a name="code"></a><span data-ttu-id="5b525-116">Código</span><span class="sxs-lookup"><span data-stu-id="5b525-116">Code</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5b525-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b525-117">See also</span></span>

- [<span data-ttu-id="5b525-118">Variação em delegados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b525-118">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [<span data-ttu-id="5b525-119">Usando variação para delegados genéricos Func e Action (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b525-119">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
