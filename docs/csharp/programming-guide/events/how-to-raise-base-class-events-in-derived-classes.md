---
title: Como gerar eventos de classe base em classes derivadas – guia de programação C#
description: Saiba como gerar eventos de classe base em classes derivadas. Consulte um exemplo de código e exiba recursos adicionais disponíveis.
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: b9708876e7d46072439ae498fd551a7b3b23a29e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167516"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="94937-104">Como gerar eventos de classe base em classes derivadas (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="94937-104">How to raise base class events in derived classes (C# Programming Guide)</span></span>

<span data-ttu-id="94937-105">O exemplo simples a seguir mostra o modo padrão para declarar os eventos em uma classe base para que eles também possam ser gerados das classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="94937-105">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="94937-106">Esse padrão é usado extensivamente em Windows Forms classes nas bibliotecas de classes do .NET.</span><span class="sxs-lookup"><span data-stu-id="94937-106">This pattern is used extensively in Windows Forms classes in the .NET class libraries.</span></span>  
  
 <span data-ttu-id="94937-107">Quando você cria uma classe que pode ser usada como uma classe base para outras classes, deve considerar o fato de que os eventos são um tipo especial de delegado que pode ser invocado apenas de dentro da classe que os declarou.</span><span class="sxs-lookup"><span data-stu-id="94937-107">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="94937-108">As classes derivadas não podem invocar diretamente eventos declarados dentro da classe base.</span><span class="sxs-lookup"><span data-stu-id="94937-108">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="94937-109">Embora, às vezes, você possa desejar um evento que possa ser gerado apenas pela classe base, na maioria das vezes você deve habilitar a classe derivada para invocar os eventos de classe base.</span><span class="sxs-lookup"><span data-stu-id="94937-109">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="94937-110">Para fazer isso, você pode criar um método de invocação protegido na classe base que encapsula o evento.</span><span class="sxs-lookup"><span data-stu-id="94937-110">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="94937-111">Chamando ou substituindo esse método de invocação, as classes derivadas podem invocar o evento diretamente.</span><span class="sxs-lookup"><span data-stu-id="94937-111">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94937-112">Não declare eventos virtuais em uma classe base e substitua-os em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="94937-112">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="94937-113">O compilador C# não lida com eles corretamente e é imprevisível se um assinante do evento derivado realmente estará assinando o evento de classe base.</span><span class="sxs-lookup"><span data-stu-id="94937-113">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94937-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94937-114">Example</span></span>  

 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="94937-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="94937-115">See also</span></span>

- [<span data-ttu-id="94937-116">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="94937-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="94937-117">Eventos</span><span class="sxs-lookup"><span data-stu-id="94937-117">Events</span></span>](./index.md)
- [<span data-ttu-id="94937-118">Representantes</span><span class="sxs-lookup"><span data-stu-id="94937-118">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="94937-119">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="94937-119">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="94937-120">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94937-120">Creating Event Handlers in Windows Forms</span></span>](/dotnet/desktop/winforms/creating-event-handlers-in-windows-forms)
