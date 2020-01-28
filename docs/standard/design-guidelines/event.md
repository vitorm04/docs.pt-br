---
title: Design de eventos
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: b44ee5933f8629b4dddbf3be1b79b2e77b0254f7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741681"
---
# <a name="event-design"></a><span data-ttu-id="43bc7-102">Design de eventos</span><span class="sxs-lookup"><span data-stu-id="43bc7-102">Event Design</span></span>
<span data-ttu-id="43bc7-103">Os eventos são a forma mais comumente usada de retornos de chamada (construções que permitem que a estrutura chame no código do usuário).</span><span class="sxs-lookup"><span data-stu-id="43bc7-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="43bc7-104">Outros mecanismos de retorno de chamada incluem membros que utilizam delegados, membros virtuais e plug-ins baseados em interface. os dados de estudos de usabilidade indicam que a maioria dos desenvolvedores é mais confortável usando eventos do que usar os outros mecanismos de retorno de chamada .</span><span class="sxs-lookup"><span data-stu-id="43bc7-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="43bc7-105">Os eventos são perfeitamente integrados ao Visual Studio e a várias linguagens.</span><span class="sxs-lookup"><span data-stu-id="43bc7-105">Events are nicely integrated with Visual Studio and many languages.</span></span>

 <span data-ttu-id="43bc7-106">É importante observar que há dois grupos de eventos: eventos gerados antes que um estado do sistema seja alterado, chamado pré-eventos e eventos gerados depois de um Estado ser alterado, chamado post-events.</span><span class="sxs-lookup"><span data-stu-id="43bc7-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="43bc7-107">Um exemplo de um pré-evento seria `Form.Closing`, que é gerado antes que um formulário seja fechado.</span><span class="sxs-lookup"><span data-stu-id="43bc7-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="43bc7-108">Um exemplo de um post-Event seria `Form.Closed`, que é gerado depois que um formulário é fechado.</span><span class="sxs-lookup"><span data-stu-id="43bc7-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>

 <span data-ttu-id="43bc7-109">✔️ usar o termo "Raise" para eventos em vez de "Fire" ou "Trigger".</span><span class="sxs-lookup"><span data-stu-id="43bc7-109">✔️ DO use the term "raise" for events rather than "fire" or "trigger."</span></span>

 <span data-ttu-id="43bc7-110">✔️ usar <xref:System.EventHandler%601?displayProperty=nameWithType> em vez de criar manualmente novos delegados para serem usados como manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="43bc7-110">✔️ DO use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>

 <span data-ttu-id="43bc7-111">✔️ Considere o uso de uma subclasse de <xref:System.EventArgs> como o argumento de evento, a menos que você tenha certeza absoluta de que o evento nunca precisará transportar dados para o método de manipulação de eventos; nesse caso, você pode usar o tipo de `EventArgs` diretamente.</span><span class="sxs-lookup"><span data-stu-id="43bc7-111">✔️ CONSIDER using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>

 <span data-ttu-id="43bc7-112">Se você enviar uma API usando `EventArgs` diretamente, nunca será possível adicionar dados a serem transportados com o evento sem a necessidade de perder a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="43bc7-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="43bc7-113">Se você usar uma subclasse, mesmo que inicialmente completamente vazia, você poderá adicionar propriedades à subclasse quando necessário.</span><span class="sxs-lookup"><span data-stu-id="43bc7-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>

 <span data-ttu-id="43bc7-114">✔️ usar um método virtual protegido para gerar cada evento.</span><span class="sxs-lookup"><span data-stu-id="43bc7-114">✔️ DO use a protected virtual method to raise each event.</span></span> <span data-ttu-id="43bc7-115">Isso só é aplicável a eventos não estáticos em classes sem lacre, não a structs, a classes seladas ou a eventos estáticos.</span><span class="sxs-lookup"><span data-stu-id="43bc7-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>

 <span data-ttu-id="43bc7-116">A finalidade do método é fornecer uma maneira para uma classe derivada manipular o evento usando uma substituição.</span><span class="sxs-lookup"><span data-stu-id="43bc7-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="43bc7-117">A substituição é uma maneira mais flexível, mais rápida e natural de lidar com eventos de classe base em classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="43bc7-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="43bc7-118">Por convenção, o nome do método deve começar com "on" e ser seguido do nome do evento.</span><span class="sxs-lookup"><span data-stu-id="43bc7-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>

 <span data-ttu-id="43bc7-119">A classe derivada pode optar por não chamar a implementação base do método em sua substituição.</span><span class="sxs-lookup"><span data-stu-id="43bc7-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="43bc7-120">Esteja preparado para isso por não incluir nenhum processamento no método necessário para que a classe base funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="43bc7-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>

 <span data-ttu-id="43bc7-121">✔️ executar um parâmetro para o método protegido que gera um evento.</span><span class="sxs-lookup"><span data-stu-id="43bc7-121">✔️ DO take one parameter to the protected method that raises an event.</span></span>

 <span data-ttu-id="43bc7-122">O parâmetro deve ser nomeado `e` e deve ser digitado como a classe de argumento de evento.</span><span class="sxs-lookup"><span data-stu-id="43bc7-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>

 <span data-ttu-id="43bc7-123">❌ não passe nulo como o remetente ao gerar um evento não estático.</span><span class="sxs-lookup"><span data-stu-id="43bc7-123">❌ DO NOT pass null as the sender when raising a nonstatic event.</span></span>

 <span data-ttu-id="43bc7-124">✔️ passar NULL como o remetente ao gerar um evento estático.</span><span class="sxs-lookup"><span data-stu-id="43bc7-124">✔️ DO pass null as the sender when raising a static event.</span></span>

 <span data-ttu-id="43bc7-125">❌ não passar nulo como o parâmetro de dados de evento ao gerar um evento.</span><span class="sxs-lookup"><span data-stu-id="43bc7-125">❌ DO NOT pass null as the event data parameter when raising an event.</span></span>

 <span data-ttu-id="43bc7-126">Você deve passar `EventArgs.Empty` se não quiser passar dados para o método de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="43bc7-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="43bc7-127">Os desenvolvedores esperam que esse parâmetro não seja nulo.</span><span class="sxs-lookup"><span data-stu-id="43bc7-127">Developers expect this parameter not to be null.</span></span>

 <span data-ttu-id="43bc7-128">✔️ Considere a geração de eventos que o usuário final pode cancelar.</span><span class="sxs-lookup"><span data-stu-id="43bc7-128">✔️ CONSIDER raising events that the end user can cancel.</span></span> <span data-ttu-id="43bc7-129">Isso se aplica apenas a eventos anteriores.</span><span class="sxs-lookup"><span data-stu-id="43bc7-129">This only applies to pre-events.</span></span>

 <span data-ttu-id="43bc7-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> ou sua subclasse como o argumento de evento para permitir que o usuário final cancele eventos.</span><span class="sxs-lookup"><span data-stu-id="43bc7-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>

### <a name="custom-event-handler-design"></a><span data-ttu-id="43bc7-131">Design do manipulador de eventos personalizado</span><span class="sxs-lookup"><span data-stu-id="43bc7-131">Custom Event Handler Design</span></span>
 <span data-ttu-id="43bc7-132">Há casos em que `EventHandler<T>` não pode ser usado, como quando a estrutura precisa trabalhar com versões anteriores do CLR, o que não oferecia suporte a genéricos.</span><span class="sxs-lookup"><span data-stu-id="43bc7-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="43bc7-133">Nesses casos, talvez seja necessário criar e desenvolver um delegado de manipulador de eventos personalizado.</span><span class="sxs-lookup"><span data-stu-id="43bc7-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>

 <span data-ttu-id="43bc7-134">✔️ usar um tipo de retorno de void para manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="43bc7-134">✔️ DO use a return type of void for event handlers.</span></span>

 <span data-ttu-id="43bc7-135">Um manipulador de eventos pode invocar vários métodos de manipulação de eventos, possivelmente em vários objetos.</span><span class="sxs-lookup"><span data-stu-id="43bc7-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="43bc7-136">Se os métodos de manipulação de eventos tivessem permissão para retornar um valor, haveria vários valores de retorno para cada invocação de evento.</span><span class="sxs-lookup"><span data-stu-id="43bc7-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>

 <span data-ttu-id="43bc7-137">✔️ usar `object` como o tipo do primeiro parâmetro do manipulador de eventos e chamá-lo `sender`.</span><span class="sxs-lookup"><span data-stu-id="43bc7-137">✔️ DO use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>

 <span data-ttu-id="43bc7-138">✔️ usar <xref:System.EventArgs?displayProperty=nameWithType> ou sua subclasse como o tipo do segundo parâmetro do manipulador de eventos e chamá-lo `e`.</span><span class="sxs-lookup"><span data-stu-id="43bc7-138">✔️ DO use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>

 <span data-ttu-id="43bc7-139">❌ não tem mais de dois parâmetros em manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="43bc7-139">❌ DO NOT have more than two parameters on event handlers.</span></span>

 <span data-ttu-id="43bc7-140">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="43bc7-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="43bc7-141">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="43bc7-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="43bc7-142">Veja também</span><span class="sxs-lookup"><span data-stu-id="43bc7-142">See also</span></span>

- [<span data-ttu-id="43bc7-143">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="43bc7-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="43bc7-144">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="43bc7-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
