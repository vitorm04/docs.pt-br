---
title: 'Como: acionar eventos de classe base em classes derivadas – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: bc968ea9c6f60ea6efda807bf254f595c61f8d4a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976073"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="01c72-102">Como: acionar eventos de classe base em classes derivadas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="01c72-102">How to: Raise Base Class Events in Derived Classes (C# Programming Guide)</span></span>
<span data-ttu-id="01c72-103">O exemplo simples a seguir mostra o modo padrão para declarar os eventos em uma classe base para que eles também possam ser gerados das classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="01c72-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="01c72-104">Esse padrão é amplamente usado em classes do Windows Forms em uma biblioteca de classes de [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="01c72-104">This pattern is used extensively in Windows Forms classes in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library.</span></span>  
  
 <span data-ttu-id="01c72-105">Quando você cria uma classe que pode ser usada como uma classe base para outras classes, deve considerar o fato de que os eventos são um tipo especial de delegado que pode ser invocado apenas de dentro da classe que os declarou.</span><span class="sxs-lookup"><span data-stu-id="01c72-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="01c72-106">As classes derivadas não podem invocar diretamente eventos declarados dentro da classe base.</span><span class="sxs-lookup"><span data-stu-id="01c72-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="01c72-107">Embora, às vezes, você possa desejar um evento que possa ser gerado apenas pela classe base, na maioria das vezes você deve habilitar a classe derivada para invocar os eventos de classe base.</span><span class="sxs-lookup"><span data-stu-id="01c72-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="01c72-108">Para fazer isso, você pode criar um método de invocação protegido na classe base que encapsula o evento.</span><span class="sxs-lookup"><span data-stu-id="01c72-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="01c72-109">Chamando ou substituindo esse método de invocação, as classes derivadas podem invocar o evento diretamente.</span><span class="sxs-lookup"><span data-stu-id="01c72-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01c72-110">Não declare eventos virtuais em uma classe base e substitua-os em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="01c72-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="01c72-111">O compilador C# não lida com eles corretamente e é imprevisível se um assinante do evento derivado realmente estará assinando o evento de classe base.</span><span class="sxs-lookup"><span data-stu-id="01c72-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01c72-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="01c72-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="01c72-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01c72-113">See also</span></span>

- [<span data-ttu-id="01c72-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="01c72-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="01c72-115">Eventos</span><span class="sxs-lookup"><span data-stu-id="01c72-115">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="01c72-116">Delegados</span><span class="sxs-lookup"><span data-stu-id="01c72-116">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="01c72-117">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="01c72-117">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="01c72-118">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01c72-118">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
