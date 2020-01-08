---
title: Como implementar eventos de interface – C# guia de programação
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: cd2192d6146a431559f5cd9dd1a80da577695d66
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346346"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="aef8b-102">Como implementar eventos de interface (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="aef8b-102">How to implement interface events (C# Programming Guide)</span></span>
<span data-ttu-id="aef8b-103">Um [interface](../../language-reference/keywords/interface.md) pode declarar uma [evento](../../language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="aef8b-103">An [interface](../../language-reference/keywords/interface.md) can declare an [event](../../language-reference/keywords/event.md).</span></span> <span data-ttu-id="aef8b-104">O exemplo a seguir mostra como implementar eventos de interface em uma classe.</span><span class="sxs-lookup"><span data-stu-id="aef8b-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="aef8b-105">Basicamente, as regras são as mesmas aplicadas à implementação de qualquer método ou propriedade de interface.</span><span class="sxs-lookup"><span data-stu-id="aef8b-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="aef8b-106">Implementar eventos de interface em uma classe</span><span class="sxs-lookup"><span data-stu-id="aef8b-106">To implement interface events in a class</span></span>  
  
<span data-ttu-id="aef8b-107">Declare o evento na classe e, em seguida, invoque-o nas áreas apropriadas.</span><span class="sxs-lookup"><span data-stu-id="aef8b-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="aef8b-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aef8b-108">Example</span></span>  
<span data-ttu-id="aef8b-109">O exemplo a seguir mostra como lidar com a situação menos comum, na qual a classe herda de duas ou mais interfaces e cada interface tem um evento com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="aef8b-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="aef8b-110">Nessa situação, é necessário fornecer uma implementação explícita da interface para pelo menos um dos eventos.</span><span class="sxs-lookup"><span data-stu-id="aef8b-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="aef8b-111">Ao gravar uma implementação explícita da interface de um evento, também é necessário gravar os acessadores de evento `add` e `remove`.</span><span class="sxs-lookup"><span data-stu-id="aef8b-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="aef8b-112">Normalmente, eles são fornecidos pelo compilador, mas nesse caso o compilador não pode fornecê-los.</span><span class="sxs-lookup"><span data-stu-id="aef8b-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="aef8b-113">Ao fornecer acessadores próprios, é possível especificar se os dois eventos são representados pelo mesmo evento na classe ou por eventos diferentes.</span><span class="sxs-lookup"><span data-stu-id="aef8b-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="aef8b-114">Por exemplo, se os eventos forem gerados em horários diferentes, de acordo com as especificações da interface, será possível associar cada evento a uma implementação separada na classe.</span><span class="sxs-lookup"><span data-stu-id="aef8b-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="aef8b-115">No exemplo a seguir, os assinantes determinam qual evento `OnDraw` receberão ao converter a referência de forma para um `IShape` ou um `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="aef8b-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a><span data-ttu-id="aef8b-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="aef8b-116">See also</span></span>

- [<span data-ttu-id="aef8b-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="aef8b-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="aef8b-118">Eventos</span><span class="sxs-lookup"><span data-stu-id="aef8b-118">Events</span></span>](./index.md)
- [<span data-ttu-id="aef8b-119">Delegados</span><span class="sxs-lookup"><span data-stu-id="aef8b-119">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="aef8b-120">Implementação de interface explícita</span><span class="sxs-lookup"><span data-stu-id="aef8b-120">Explicit Interface Implementation</span></span>](../interfaces/explicit-interface-implementation.md)
- [<span data-ttu-id="aef8b-121">Como gerar eventos de classe base em classes derivadas</span><span class="sxs-lookup"><span data-stu-id="aef8b-121">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)
