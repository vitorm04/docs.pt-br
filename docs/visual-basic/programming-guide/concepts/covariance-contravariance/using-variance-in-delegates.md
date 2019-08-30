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
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="9471f-102">Usando a variação em delegados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9471f-102">Using Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="9471f-103">Quando você atribui um método a um delegado, a *covariância* e a *contravariância* fornece flexibilidade para corresponder um tipo de delegado a uma assinatura de método.</span><span class="sxs-lookup"><span data-stu-id="9471f-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="9471f-104">A covariância permite que um método tenha o tipo de retorno mais derivado do que o definido no delegado.</span><span class="sxs-lookup"><span data-stu-id="9471f-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="9471f-105">A contravariância permite que um método que tem tipos de parâmetro menos derivados do que no tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="9471f-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>

## <a name="example-1-covariance"></a><span data-ttu-id="9471f-106">Exemplo 1: Covariância</span><span class="sxs-lookup"><span data-stu-id="9471f-106">Example 1: Covariance</span></span>

### <a name="description"></a><span data-ttu-id="9471f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9471f-107">Description</span></span>

<span data-ttu-id="9471f-108">Este exemplo demonstra como delegados podem ser usados com métodos que têm tipos de retorno que são derivados do tipo de retorno na assinatura do delegado.</span><span class="sxs-lookup"><span data-stu-id="9471f-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="9471f-109">O tipo de dados retornado por `DogsHandler` é do tipo `Dogs`, que deriva do tipo `Mammals` definido no delegado.</span><span class="sxs-lookup"><span data-stu-id="9471f-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>

### <a name="code"></a><span data-ttu-id="9471f-110">Código</span><span class="sxs-lookup"><span data-stu-id="9471f-110">Code</span></span>

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

## <a name="example-2-contravariance"></a><span data-ttu-id="9471f-111">Exemplo 2: Contravariância</span><span class="sxs-lookup"><span data-stu-id="9471f-111">Example 2: Contravariance</span></span>

### <a name="description"></a><span data-ttu-id="9471f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9471f-112">Description</span></span>

<span data-ttu-id="9471f-113">Este exemplo demonstra como os delegados podem ser usados com métodos que têm parâmetros cujos tipos são tipos base do tipo de parâmetro de assinatura de representante.</span><span class="sxs-lookup"><span data-stu-id="9471f-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="9471f-114">Com a contravariância, você pode usar um manipulador de eventos em vez de manipuladores separados.</span><span class="sxs-lookup"><span data-stu-id="9471f-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="9471f-115">O exemplo a seguir usa dois delegados:</span><span class="sxs-lookup"><span data-stu-id="9471f-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="9471f-116">Um <xref:System.Windows.Forms.KeyEventHandler> delegado que define a assinatura do evento [Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) .</span><span class="sxs-lookup"><span data-stu-id="9471f-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="9471f-117">Sua assinatura é:</span><span class="sxs-lookup"><span data-stu-id="9471f-117">Its signature is:</span></span>

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- <span data-ttu-id="9471f-118">Um <xref:System.Windows.Forms.MouseEventHandler> delegado que define a assinatura do evento [Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) .</span><span class="sxs-lookup"><span data-stu-id="9471f-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="9471f-119">Sua assinatura é:</span><span class="sxs-lookup"><span data-stu-id="9471f-119">Its signature is:</span></span>

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

<span data-ttu-id="9471f-120">O exemplo define um manipulador de eventos com <xref:System.EventArgs> um parâmetro e o usa para lidar com `Button.KeyDown` os `Button.MouseClick` eventos e.</span><span class="sxs-lookup"><span data-stu-id="9471f-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="9471f-121">Isso pode fazer isso porque <xref:System.EventArgs> é um tipo base <xref:System.Windows.Forms.KeyEventArgs> de e <xref:System.Windows.Forms.MouseEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="9471f-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>

### <a name="code"></a><span data-ttu-id="9471f-122">Código</span><span class="sxs-lookup"><span data-stu-id="9471f-122">Code</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9471f-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9471f-123">See also</span></span>

- [<span data-ttu-id="9471f-124">Variação em delegados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9471f-124">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [<span data-ttu-id="9471f-125">Usando variação para delegados genéricos Func e Action (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9471f-125">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
