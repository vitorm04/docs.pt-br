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
author: KrzysztofCwalina
ms.openlocfilehash: 530c68ea5342263acd07f8dc8a8c8ce889652503
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026439"
---
# <a name="event-design"></a><span data-ttu-id="e1365-102">Design de eventos</span><span class="sxs-lookup"><span data-stu-id="e1365-102">Event Design</span></span>
<span data-ttu-id="e1365-103">Eventos são a forma mais usada de retornos de chamada (construções que permitem que o framework chamar o código de usuário).</span><span class="sxs-lookup"><span data-stu-id="e1365-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="e1365-104">Outros mecanismos de retorno de chamada incluem membros fazer delegados, os membros virtuais e plug-ins baseados em interface. Dados de estudos de usabilidade indicam que a maioria dos desenvolvedores estão mais familiarizado com o uso de eventos que estão usando outros mecanismos de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="e1365-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="e1365-105">Eventos são integrados perfeitamente com o Visual Studio e muitos idiomas.</span><span class="sxs-lookup"><span data-stu-id="e1365-105">Events are nicely integrated with Visual Studio and many languages.</span></span>  
  
 <span data-ttu-id="e1365-106">É importante observar que há dois grupos de eventos: eventos gerados antes de um estado das alterações do sistema, chamado pré-eventos e eventos gerados depois que um estado for alterado, chamado pós eventos.</span><span class="sxs-lookup"><span data-stu-id="e1365-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="e1365-107">Um exemplo de um pré-evento de seria `Form.Closing`, que é gerado antes de um formulário é fechado.</span><span class="sxs-lookup"><span data-stu-id="e1365-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="e1365-108">Um exemplo de um pós-evento de seria `Form.Closed`, que é gerado depois que um formulário é fechado.</span><span class="sxs-lookup"><span data-stu-id="e1365-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>  
  
 <span data-ttu-id="e1365-109">**✓ DO** usam o termo "raise" eventos em vez de "fire" ou "disparar".</span><span class="sxs-lookup"><span data-stu-id="e1365-109">**✓ DO** use the term "raise" for events rather than "fire" or "trigger."</span></span>  
  
 <span data-ttu-id="e1365-110">**✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> em vez de criar manualmente novas delegados para serem usados como manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="e1365-110">**✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>  
  
 <span data-ttu-id="e1365-111">**✓ CONSIDER** usando uma subclasse de <xref:System.EventArgs> como o argumento do evento, a menos que seja absolutamente-se de que o evento não será necessário executar todos os dados para o método de manipulação de eventos caso em que você pode usar o `EventArgs` digitados diretamente.</span><span class="sxs-lookup"><span data-stu-id="e1365-111">**✓ CONSIDER** using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>  
  
 <span data-ttu-id="e1365-112">Se você enviar uma API usando `EventArgs` diretamente, você nunca poderá adicionar dados a ser realizada com o evento sem interromper a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="e1365-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="e1365-113">Se você usar uma subclasse, mesmo se inicialmente completamente vazia, você poderá adicionar propriedades para a subclasse quando necessário.</span><span class="sxs-lookup"><span data-stu-id="e1365-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>  
  
 <span data-ttu-id="e1365-114">**✓ DO** usar um método virtual protegido para gerar cada evento.</span><span class="sxs-lookup"><span data-stu-id="e1365-114">**✓ DO** use a protected virtual method to raise each event.</span></span> <span data-ttu-id="e1365-115">Isso só é aplicável aos eventos não estáticos em classes sem lacre, não para structs, classes sealed ou eventos estáticos.</span><span class="sxs-lookup"><span data-stu-id="e1365-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>  
  
 <span data-ttu-id="e1365-116">A finalidade do método é fornecer uma maneira para uma classe derivada manipular o evento usando uma substituição.</span><span class="sxs-lookup"><span data-stu-id="e1365-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="e1365-117">Substituindo é uma maneira mais flexível, mais rápida e mais natural para lidar com eventos de classe base em classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="e1365-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="e1365-118">Por convenção, o nome do método deve começar com "On" e ser seguido pelo nome do evento.</span><span class="sxs-lookup"><span data-stu-id="e1365-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>  
  
 <span data-ttu-id="e1365-119">A classe derivada pode optar por não chamar a implementação base do método na sua substituição.</span><span class="sxs-lookup"><span data-stu-id="e1365-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="e1365-120">Esteja preparado para isso, não incluindo nenhum processamento no método que é necessário para a classe base funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="e1365-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>  
  
 <span data-ttu-id="e1365-121">**✓ DO** ter um parâmetro para o método protegido que gera um evento.</span><span class="sxs-lookup"><span data-stu-id="e1365-121">**✓ DO** take one parameter to the protected method that raises an event.</span></span>  
  
 <span data-ttu-id="e1365-122">O parâmetro deve ser nomeado `e` e devem ser digitados como a classe de argumento do evento.</span><span class="sxs-lookup"><span data-stu-id="e1365-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>  
  
 <span data-ttu-id="e1365-123">**X DO NOT** passar nulo como o remetente quando gerar um evento não estático.</span><span class="sxs-lookup"><span data-stu-id="e1365-123">**X DO NOT** pass null as the sender when raising a nonstatic event.</span></span>  
  
 <span data-ttu-id="e1365-124">**✓ DO** passar nulo como o remetente ao gerar um evento estático.</span><span class="sxs-lookup"><span data-stu-id="e1365-124">**✓ DO** pass null as the sender when raising a static event.</span></span>  
  
 <span data-ttu-id="e1365-125">**X DO NOT** passar nulo como o parâmetro de dados de evento ao gerar um evento.</span><span class="sxs-lookup"><span data-stu-id="e1365-125">**X DO NOT** pass null as the event data parameter when raising an event.</span></span>  
  
 <span data-ttu-id="e1365-126">Você deve passar `EventArgs.Empty` se você não quiser passar nenhum dado para o método de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="e1365-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="e1365-127">Os desenvolvedores esperam esse parâmetro não deve ser nulo.</span><span class="sxs-lookup"><span data-stu-id="e1365-127">Developers expect this parameter not to be null.</span></span>  
  
 <span data-ttu-id="e1365-128">**✓ CONSIDER** gerando eventos que o usuário final pode cancelar.</span><span class="sxs-lookup"><span data-stu-id="e1365-128">**✓ CONSIDER** raising events that the end user can cancel.</span></span> <span data-ttu-id="e1365-129">Isso se aplica apenas aos pré eventos de.</span><span class="sxs-lookup"><span data-stu-id="e1365-129">This only applies to pre-events.</span></span>  
  
 <span data-ttu-id="e1365-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> ou suas subclasses como o argumento de evento para permitir que o usuário final cancelar eventos.</span><span class="sxs-lookup"><span data-stu-id="e1365-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>  
  
### <a name="custom-event-handler-design"></a><span data-ttu-id="e1365-131">Design de manipulador de evento personalizado</span><span class="sxs-lookup"><span data-stu-id="e1365-131">Custom Event Handler Design</span></span>  
 <span data-ttu-id="e1365-132">Há casos em que `EventHandler<T>` não podem ser usadas, como quando o framework precisa trabalhar com versões anteriores do CLR, que não oferecia suporte a genéricos.</span><span class="sxs-lookup"><span data-stu-id="e1365-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="e1365-133">Nesses casos, você talvez precise criar e desenvolver um delegado de manipulador de eventos personalizado.</span><span class="sxs-lookup"><span data-stu-id="e1365-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>  
  
 <span data-ttu-id="e1365-134">**✓ DO** usar um tipo de retorno de void para manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="e1365-134">**✓ DO** use a return type of void for event handlers.</span></span>  
  
 <span data-ttu-id="e1365-135">Um manipulador de eventos pode chamar vários métodos, possivelmente em vários objetos de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="e1365-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="e1365-136">Se os métodos de manipulação de eventos foram permitidos para retornar um valor, deve haver vários valores de retorno para cada invocação do evento.</span><span class="sxs-lookup"><span data-stu-id="e1365-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>  
  
 <span data-ttu-id="e1365-137">**✓ DO** usar `object` como o tipo do primeiro parâmetro do manipulador de eventos e chamá-la `sender`.</span><span class="sxs-lookup"><span data-stu-id="e1365-137">**✓ DO** use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>  
  
 <span data-ttu-id="e1365-138">**✓ DO** usar <xref:System.EventArgs?displayProperty=nameWithType> ou suas subclasses como o tipo do segundo parâmetro do manipulador de eventos e chamá-la `e`.</span><span class="sxs-lookup"><span data-stu-id="e1365-138">**✓ DO** use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>  
  
 <span data-ttu-id="e1365-139">**X DO NOT** ter mais de dois parâmetros em manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="e1365-139">**X DO NOT** have more than two parameters on event handlers.</span></span>  
  
 <span data-ttu-id="e1365-140">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="e1365-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e1365-141">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="e1365-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1365-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1365-142">See also</span></span>

- [<span data-ttu-id="e1365-143">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="e1365-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="e1365-144">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="e1365-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
