---
title: Usando variação em delegações (C#)
description: Saiba como usar a variação em delegados usando os exemplos de código de covariância e contravariância incluídos.
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 62b0555ee29c5e7d2ba0954a8949d61596122cc7
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105678"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="18c1c-103">Usando variação em delegações (C#)</span><span class="sxs-lookup"><span data-stu-id="18c1c-103">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="18c1c-104">Quando você atribui um método a um delegado, a *covariância* e a *contravariância* fornece flexibilidade para corresponder um tipo de delegado a uma assinatura de método.</span><span class="sxs-lookup"><span data-stu-id="18c1c-104">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="18c1c-105">A covariância permite que um método tenha o tipo de retorno mais derivado do que o definido no delegado.</span><span class="sxs-lookup"><span data-stu-id="18c1c-105">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="18c1c-106">A contravariância permite que um método que tem tipos de parâmetro menos derivados do que no tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="18c1c-106">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="18c1c-107">Exemplo 1: covariância</span><span class="sxs-lookup"><span data-stu-id="18c1c-107">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="18c1c-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="18c1c-108">Description</span></span>  
 <span data-ttu-id="18c1c-109">Este exemplo demonstra como delegados podem ser usados com métodos que têm tipos de retorno que são derivados do tipo de retorno na assinatura do delegado.</span><span class="sxs-lookup"><span data-stu-id="18c1c-109">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="18c1c-110">O tipo de dados retornado por `DogsHandler` é do tipo `Dogs`, que deriva do tipo `Mammals` definido no delegado.</span><span class="sxs-lookup"><span data-stu-id="18c1c-110">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="18c1c-111">Código</span><span class="sxs-lookup"><span data-stu-id="18c1c-111">Code</span></span>  
  
```csharp  
class Mammals {}  
class Dogs : Mammals {}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## <a name="example-2-contravariance"></a><span data-ttu-id="18c1c-112">Exemplo 2: contravariância</span><span class="sxs-lookup"><span data-stu-id="18c1c-112">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="18c1c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="18c1c-113">Description</span></span>

<span data-ttu-id="18c1c-114">Este exemplo demonstra como representantes podem ser usados com métodos que têm parâmetros cujos tipos são tipos base do tipo de parâmetro de assinatura do representante.</span><span class="sxs-lookup"><span data-stu-id="18c1c-114">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="18c1c-115">Com a contravariância, você pode usar um manipulador de eventos em vez de manipuladores separados.</span><span class="sxs-lookup"><span data-stu-id="18c1c-115">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="18c1c-116">O seguinte exemplo usa dois representantes:</span><span class="sxs-lookup"><span data-stu-id="18c1c-116">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="18c1c-117">Um representante <xref:System.Windows.Forms.KeyEventHandler> que define a assinatura do evento [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown).</span><span class="sxs-lookup"><span data-stu-id="18c1c-117">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="18c1c-118">Sua assinatura é:</span><span class="sxs-lookup"><span data-stu-id="18c1c-118">Its signature is:</span></span>

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <span data-ttu-id="18c1c-119">Um representante <xref:System.Windows.Forms.MouseEventHandler> que define a assinatura do evento [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown).</span><span class="sxs-lookup"><span data-stu-id="18c1c-119">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="18c1c-120">Sua assinatura é:</span><span class="sxs-lookup"><span data-stu-id="18c1c-120">Its signature is:</span></span>

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

<span data-ttu-id="18c1c-121">O exemplo define um manipulador de eventos com um parâmetro <xref:System.EventArgs> e o usa para manipular os eventos `Button.KeyDown` e `Button.MouseClick`.</span><span class="sxs-lookup"><span data-stu-id="18c1c-121">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="18c1c-122">Ele pode fazer isso porque <xref:System.EventArgs> é um tipo base de <xref:System.Windows.Forms.KeyEventArgs> e <xref:System.Windows.Forms.MouseEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="18c1c-122">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>
  
### <a name="code"></a><span data-ttu-id="18c1c-123">Código</span><span class="sxs-lookup"><span data-stu-id="18c1c-123">Code</span></span>  
  
```csharp  
// Event handler that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="18c1c-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="18c1c-124">See also</span></span>

- [<span data-ttu-id="18c1c-125">Variação em delegados (C#)</span><span class="sxs-lookup"><span data-stu-id="18c1c-125">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="18c1c-126">Usando variação para delegados genéricos Func e Action (C#)</span><span class="sxs-lookup"><span data-stu-id="18c1c-126">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
