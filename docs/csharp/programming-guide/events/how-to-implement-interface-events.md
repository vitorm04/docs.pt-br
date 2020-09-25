---
title: Como implementar eventos de interface – guia de programação C#
description: Saiba como implementar eventos de interface em uma classe. Confira exemplos de código e exiba recursos adicionais disponíveis.
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 153a2efa254bf2f2c81cec4b28a53207cdc4efe5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167542"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="818d7-104">Como implementar eventos de interface (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="818d7-104">How to implement interface events (C# Programming Guide)</span></span>

<span data-ttu-id="818d7-105">Um [interface](../../language-reference/keywords/interface.md) pode declarar uma [evento](../../language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="818d7-105">An [interface](../../language-reference/keywords/interface.md) can declare an [event](../../language-reference/keywords/event.md).</span></span> <span data-ttu-id="818d7-106">O exemplo a seguir mostra como implementar eventos de interface em uma classe.</span><span class="sxs-lookup"><span data-stu-id="818d7-106">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="818d7-107">Basicamente, as regras são as mesmas aplicadas à implementação de qualquer método ou propriedade de interface.</span><span class="sxs-lookup"><span data-stu-id="818d7-107">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="818d7-108">Implementar eventos de interface em uma classe</span><span class="sxs-lookup"><span data-stu-id="818d7-108">To implement interface events in a class</span></span>  
  
<span data-ttu-id="818d7-109">Declare o evento na classe e, em seguida, invoque-o nas áreas apropriadas.</span><span class="sxs-lookup"><span data-stu-id="818d7-109">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
```csharp
namespace ImplementInterfaceEvents  
{  
    public interface IDrawingObject  
    {  
        event EventHandler ShapeChanged;  
    }  
    public class MyEventArgs : EventArgs
    {  
        // class members  
    }  
    public class Shape : IDrawingObject  
    {  
        public event EventHandler ShapeChanged;  
        void ChangeShape()  
        {  
            // Do something here before the event…  

            OnShapeChanged(new MyEventArgs(/*arguments*/));  

            // or do something here after the event.
        }  
        protected virtual void OnShapeChanged(MyEventArgs e)  
        {  
            ShapeChanged?.Invoke(this, e);  
        }  
    }  

}  
```  
  
## <a name="example"></a><span data-ttu-id="818d7-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="818d7-110">Example</span></span>  

<span data-ttu-id="818d7-111">O exemplo a seguir mostra como lidar com a situação menos comum, na qual a classe herda de duas ou mais interfaces e cada interface tem um evento com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="818d7-111">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="818d7-112">Nessa situação, é necessário fornecer uma implementação explícita da interface para pelo menos um dos eventos.</span><span class="sxs-lookup"><span data-stu-id="818d7-112">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="818d7-113">Ao gravar uma implementação explícita da interface de um evento, também é necessário gravar os acessadores de evento `add` e `remove`.</span><span class="sxs-lookup"><span data-stu-id="818d7-113">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="818d7-114">Normalmente, eles são fornecidos pelo compilador, mas nesse caso o compilador não pode fornecê-los.</span><span class="sxs-lookup"><span data-stu-id="818d7-114">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="818d7-115">Ao fornecer acessadores próprios, é possível especificar se os dois eventos são representados pelo mesmo evento na classe ou por eventos diferentes.</span><span class="sxs-lookup"><span data-stu-id="818d7-115">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="818d7-116">Por exemplo, se os eventos forem gerados em horários diferentes, de acordo com as especificações da interface, será possível associar cada evento a uma implementação separada na classe.</span><span class="sxs-lookup"><span data-stu-id="818d7-116">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="818d7-117">No exemplo a seguir, os assinantes determinam qual evento `OnDraw` receberão ao converter a referência de forma para um `IShape` ou um `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="818d7-117">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a><span data-ttu-id="818d7-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="818d7-118">See also</span></span>

- [<span data-ttu-id="818d7-119">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="818d7-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="818d7-120">Eventos</span><span class="sxs-lookup"><span data-stu-id="818d7-120">Events</span></span>](./index.md)
- [<span data-ttu-id="818d7-121">Representantes</span><span class="sxs-lookup"><span data-stu-id="818d7-121">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="818d7-122">Implementação de interface explícita</span><span class="sxs-lookup"><span data-stu-id="818d7-122">Explicit Interface Implementation</span></span>](../interfaces/explicit-interface-implementation.md)
- [<span data-ttu-id="818d7-123">Como acionar eventos de classe base em classes derivadas</span><span class="sxs-lookup"><span data-stu-id="818d7-123">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)
