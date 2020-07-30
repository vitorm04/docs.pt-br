---
title: Eventos – Guia de Programação em C#
description: Saiba mais sobre os eventos. Eventos permitem que uma classe ou objeto notifique outras classes ou objetos quando algo interessante ocorrer.
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 3160d1e381c6cb3af0f017538f9555b3fded9910
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302068"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="d46ca-104">Eventos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d46ca-104">Events (C# Programming Guide)</span></span>
<span data-ttu-id="d46ca-105">Eventos permitem que uma [classe](../../language-reference/keywords/class.md) ou objeto notifique outras classes ou objetos quando algo interessante ocorre.</span><span class="sxs-lookup"><span data-stu-id="d46ca-105">Events enable a [class](../../language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="d46ca-106">A classe que envia (ou *aciona*) o evento é chamada de *editor* e as classes que recebem (ou *manipulam*) os eventos são chamadas *assinantes*.</span><span class="sxs-lookup"><span data-stu-id="d46ca-106">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
<span data-ttu-id="d46ca-107">Em um aplicativo Windows Forms em C# ou Web típico, você assina eventos acionados pelos controles, como botões e caixas de listagem.</span><span class="sxs-lookup"><span data-stu-id="d46ca-107">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="d46ca-108">Você pode usar o IDE (ambiente de desenvolvimento integrado) do Visual C# para procurar os eventos que um controle publica e selecionar aqueles que você deseja manipular.</span><span class="sxs-lookup"><span data-stu-id="d46ca-108">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="d46ca-109">O IDE oferece uma maneira fácil de adicionar automaticamente um método de manipulador de eventos vazio e o código para assinar o evento.</span><span class="sxs-lookup"><span data-stu-id="d46ca-109">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="d46ca-110">Para obter mais informações, consulte [como assinar e cancelar a assinatura de eventos](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="d46ca-110">For more information, see [How to subscribe to and unsubscribe from events](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>
  
## <a name="events-overview"></a><span data-ttu-id="d46ca-111">Visão geral sobre eventos</span><span class="sxs-lookup"><span data-stu-id="d46ca-111">Events Overview</span></span>  
 <span data-ttu-id="d46ca-112">Os eventos têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="d46ca-112">Events have the following properties:</span></span>  
  
- <span data-ttu-id="d46ca-113">O editor determina quando um evento é acionado. Os assinantes determinam a ação que é executada em resposta ao evento.</span><span class="sxs-lookup"><span data-stu-id="d46ca-113">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="d46ca-114">Um evento pode ter vários assinantes.</span><span class="sxs-lookup"><span data-stu-id="d46ca-114">An event can have multiple subscribers.</span></span> <span data-ttu-id="d46ca-115">Um assinante pode manipular vários eventos de vários publicadores.</span><span class="sxs-lookup"><span data-stu-id="d46ca-115">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="d46ca-116">Eventos que não têm assinantes nunca são acionados.</span><span class="sxs-lookup"><span data-stu-id="d46ca-116">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="d46ca-117">Normalmente, os eventos são usados para sinalizar ações do usuário, como cliques de botão ou seleções de menu em interfaces gráficas do usuário.</span><span class="sxs-lookup"><span data-stu-id="d46ca-117">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="d46ca-118">Quando um evento tem vários assinantes, os manipuladores de eventos são invocados sincronicamente quando um evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="d46ca-118">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="d46ca-119">Para invocar eventos de forma assíncrona, consulte [Chamando métodos síncronos assincronamente](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="d46ca-119">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="d46ca-120">Na biblioteca de classes .NET Framework, os eventos são baseados no delegado <xref:System.EventHandler> e na classe base <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="d46ca-120">In the .NET Framework class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d46ca-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="d46ca-121">Related Sections</span></span>  
 <span data-ttu-id="d46ca-122">Para obter mais informações, veja:</span><span class="sxs-lookup"><span data-stu-id="d46ca-122">For more information, see:</span></span>  
  
- [<span data-ttu-id="d46ca-123">Como realizar e cancelar a assinatura de eventos</span><span class="sxs-lookup"><span data-stu-id="d46ca-123">How to subscribe to and unsubscribe from events</span></span>](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [<span data-ttu-id="d46ca-124">Como publicar eventos que estão em conformidade com as diretrizes do .NET</span><span class="sxs-lookup"><span data-stu-id="d46ca-124">How to publish events that conform to .NET Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [<span data-ttu-id="d46ca-125">Como acionar eventos de classe base em classes derivadas</span><span class="sxs-lookup"><span data-stu-id="d46ca-125">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)

- [<span data-ttu-id="d46ca-126">Como implementar eventos de interface</span><span class="sxs-lookup"><span data-stu-id="d46ca-126">How to implement interface events</span></span>](./how-to-implement-interface-events.md)

- [<span data-ttu-id="d46ca-127">Como implementar acessadores de eventos personalizados</span><span class="sxs-lookup"><span data-stu-id="d46ca-127">How to implement custom event accessors</span></span>](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a><span data-ttu-id="d46ca-128">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d46ca-128">C# Language Specification</span></span>  

<span data-ttu-id="d46ca-129">Para obter mais informações, veja [Eventos](~/_csharplang/spec/classes.md#events) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="d46ca-129">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="d46ca-130">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="d46ca-130">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="d46ca-131">Capítulos do Livro em Destaque</span><span class="sxs-lookup"><span data-stu-id="d46ca-131">Featured Book Chapters</span></span>  
 <span data-ttu-id="d46ca-132">[Expressões lambda, eventos e delegados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) em [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="d46ca-132">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="d46ca-133">[Delegados e eventos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) em [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="d46ca-133">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d46ca-134">Veja também</span><span class="sxs-lookup"><span data-stu-id="d46ca-134">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="d46ca-135">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="d46ca-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d46ca-136">Representantes</span><span class="sxs-lookup"><span data-stu-id="d46ca-136">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="d46ca-137">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d46ca-137">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
