---
title: Eventos – Guia de Programação em C#
description: Saiba mais sobre os eventos. Eventos permitem que uma classe ou objeto notifique outras classes ou objetos quando algo interessante ocorrer.
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 14c18006e393dece5d32d30c2a727d797515c779
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167451"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="202c4-104">Eventos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="202c4-104">Events (C# Programming Guide)</span></span>

<span data-ttu-id="202c4-105">Eventos permitem que uma [classe](../../language-reference/keywords/class.md) ou objeto notifique outras classes ou objetos quando algo interessante ocorre.</span><span class="sxs-lookup"><span data-stu-id="202c4-105">Events enable a [class](../../language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="202c4-106">A classe que envia (ou *aciona*) o evento é chamada de *editor* e as classes que recebem (ou *manipulam*) os eventos são chamadas *assinantes*.</span><span class="sxs-lookup"><span data-stu-id="202c4-106">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
<span data-ttu-id="202c4-107">Em um aplicativo Windows Forms em C# ou Web típico, você assina eventos acionados pelos controles, como botões e caixas de listagem.</span><span class="sxs-lookup"><span data-stu-id="202c4-107">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="202c4-108">Você pode usar o IDE (ambiente de desenvolvimento integrado) do Visual C# para procurar os eventos que um controle publica e selecionar aqueles que você deseja manipular.</span><span class="sxs-lookup"><span data-stu-id="202c4-108">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="202c4-109">O IDE oferece uma maneira fácil de adicionar automaticamente um método de manipulador de eventos vazio e o código para assinar o evento.</span><span class="sxs-lookup"><span data-stu-id="202c4-109">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="202c4-110">Para obter mais informações, consulte [como assinar e cancelar a assinatura de eventos](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="202c4-110">For more information, see [How to subscribe to and unsubscribe from events](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>
  
## <a name="events-overview"></a><span data-ttu-id="202c4-111">Visão geral sobre eventos</span><span class="sxs-lookup"><span data-stu-id="202c4-111">Events Overview</span></span>  

 <span data-ttu-id="202c4-112">Os eventos têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="202c4-112">Events have the following properties:</span></span>  
  
- <span data-ttu-id="202c4-113">O editor determina quando um evento é acionado. Os assinantes determinam a ação que é executada em resposta ao evento.</span><span class="sxs-lookup"><span data-stu-id="202c4-113">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="202c4-114">Um evento pode ter vários assinantes.</span><span class="sxs-lookup"><span data-stu-id="202c4-114">An event can have multiple subscribers.</span></span> <span data-ttu-id="202c4-115">Um assinante pode manipular vários eventos de vários publicadores.</span><span class="sxs-lookup"><span data-stu-id="202c4-115">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="202c4-116">Eventos que não têm assinantes nunca são acionados.</span><span class="sxs-lookup"><span data-stu-id="202c4-116">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="202c4-117">Normalmente, os eventos são usados para sinalizar ações do usuário, como cliques de botão ou seleções de menu em interfaces gráficas do usuário.</span><span class="sxs-lookup"><span data-stu-id="202c4-117">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="202c4-118">Quando um evento tem vários assinantes, os manipuladores de eventos são invocados sincronicamente quando um evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="202c4-118">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="202c4-119">Para invocar eventos de forma assíncrona, consulte [Chamando métodos síncronos assincronamente](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="202c4-119">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="202c4-120">Na biblioteca de classes .NET, os eventos são baseados no <xref:System.EventHandler> delegado e na <xref:System.EventArgs> classe base.</span><span class="sxs-lookup"><span data-stu-id="202c4-120">In the .NET class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="202c4-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="202c4-121">Related Sections</span></span>  

 <span data-ttu-id="202c4-122">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="202c4-122">For more information, see:</span></span>  
  
- [<span data-ttu-id="202c4-123">Como realizar e cancelar a assinatura de eventos</span><span class="sxs-lookup"><span data-stu-id="202c4-123">How to subscribe to and unsubscribe from events</span></span>](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [<span data-ttu-id="202c4-124">Como publicar eventos em conformidade com as diretrizes do .NET</span><span class="sxs-lookup"><span data-stu-id="202c4-124">How to publish events that conform to .NET Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [<span data-ttu-id="202c4-125">Como acionar eventos de classe base em classes derivadas</span><span class="sxs-lookup"><span data-stu-id="202c4-125">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)

- [<span data-ttu-id="202c4-126">Como implementar eventos de interface</span><span class="sxs-lookup"><span data-stu-id="202c4-126">How to implement interface events</span></span>](./how-to-implement-interface-events.md)

- [<span data-ttu-id="202c4-127">Como implementar acessadores de eventos personalizados</span><span class="sxs-lookup"><span data-stu-id="202c4-127">How to implement custom event accessors</span></span>](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a><span data-ttu-id="202c4-128">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="202c4-128">C# Language Specification</span></span>  

<span data-ttu-id="202c4-129">Para obter mais informações, veja [Eventos](~/_csharplang/spec/classes.md#events) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="202c4-129">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="202c4-130">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="202c4-130">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="202c4-131">Capítulos do Livro em Destaque</span><span class="sxs-lookup"><span data-stu-id="202c4-131">Featured Book Chapters</span></span>  

 <span data-ttu-id="202c4-132">[Expressões lambda, eventos e delegados](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10)) em [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))</span><span class="sxs-lookup"><span data-stu-id="202c4-132">[Delegates, Events, and Lambda Expressions](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10)) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))</span></span>  
  
 <span data-ttu-id="202c4-133">[Delegados e eventos](/previous-versions/visualstudio/visual-studio-2008/ff652490(v=orm.10)) em [Learning C# 3.0: Master the fundamentals of C# 3.0](/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))</span><span class="sxs-lookup"><span data-stu-id="202c4-133">[Delegates and Events](/previous-versions/visualstudio/visual-studio-2008/ff652490(v=orm.10)) in [Learning C# 3.0: Master the fundamentals of C# 3.0](/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="202c4-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="202c4-134">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="202c4-135">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="202c4-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="202c4-136">Representantes</span><span class="sxs-lookup"><span data-stu-id="202c4-136">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="202c4-137">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="202c4-137">Creating Event Handlers in Windows Forms</span></span>](/dotnet/desktop/winforms/creating-event-handlers-in-windows-forms)
