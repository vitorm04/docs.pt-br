---
title: "Como implementar eventos de interface (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a53c6ba29837ad8827d97ea745be0462451eb145
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="67391-102">Como implementar eventos de interface (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="67391-102">How to: Implement Interface Events (C# Programming Guide)</span></span>
<span data-ttu-id="67391-103">Um [interface](../../../csharp/language-reference/keywords/interface.md) pode declarar uma [evento](../../../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="67391-103">An [interface](../../../csharp/language-reference/keywords/interface.md) can declare an [event](../../../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="67391-104">O exemplo a seguir mostra como implementar eventos de interface em uma classe.</span><span class="sxs-lookup"><span data-stu-id="67391-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="67391-105">Basicamente, as regras são as mesmas aplicadas à implementação de qualquer método ou propriedade de interface.</span><span class="sxs-lookup"><span data-stu-id="67391-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
### <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="67391-106">Implementar eventos de interface em uma classe</span><span class="sxs-lookup"><span data-stu-id="67391-106">To implement interface events in a class</span></span>  
  
-   <span data-ttu-id="67391-107">Declare o evento na classe e, em seguida, invoque-o nas áreas apropriadas.</span><span class="sxs-lookup"><span data-stu-id="67391-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
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
                if(ShapeChanged != null)  
                {  
                   ShapeChanged(this, e);  
                }  
            }  
        }  
  
    }  
    ```  
  
## <a name="example"></a><span data-ttu-id="67391-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="67391-108">Example</span></span>  
 <span data-ttu-id="67391-109">O exemplo a seguir mostra como lidar com a situação menos comum, na qual a classe herda de duas ou mais interfaces e cada interface tem um evento com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="67391-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="67391-110">Nessa situação, é necessário fornecer uma implementação explícita da interface para pelo menos um dos eventos.</span><span class="sxs-lookup"><span data-stu-id="67391-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="67391-111">Ao gravar uma implementação explícita da interface de um evento, também é necessário gravar os acessadores de evento `add` e `remove`.</span><span class="sxs-lookup"><span data-stu-id="67391-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="67391-112">Normalmente, eles são fornecidos pelo compilador, mas nesse caso o compilador não pode fornecê-los.</span><span class="sxs-lookup"><span data-stu-id="67391-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
 <span data-ttu-id="67391-113">Ao fornecer acessadores próprios, é possível especificar se os dois eventos são representados pelo mesmo evento na classe ou por eventos diferentes.</span><span class="sxs-lookup"><span data-stu-id="67391-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="67391-114">Por exemplo, se os eventos forem gerados em horários diferentes, de acordo com as especificações da interface, será possível associar cada evento a uma implementação separada na classe.</span><span class="sxs-lookup"><span data-stu-id="67391-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="67391-115">No exemplo a seguir, os assinantes determinam qual evento `OnDraw` receberão ao converter a referência de forma para um `IShape` ou um `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="67391-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="67391-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67391-116">See Also</span></span>  
 [<span data-ttu-id="67391-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="67391-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="67391-118">Eventos</span><span class="sxs-lookup"><span data-stu-id="67391-118">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="67391-119">Delegados</span><span class="sxs-lookup"><span data-stu-id="67391-119">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="67391-120">Implementação de interface explícita</span><span class="sxs-lookup"><span data-stu-id="67391-120">Explicit Interface Implementation</span></span>](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 [<span data-ttu-id="67391-121">Como acionar eventos de classe base em classes derivadas</span><span class="sxs-lookup"><span data-stu-id="67391-121">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
