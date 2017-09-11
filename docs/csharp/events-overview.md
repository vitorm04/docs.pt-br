---
title: "Introdução a Eventos"
description: "Saiba mais sobre eventos no .NET Core e nossas metas de design de linguagem para eventos nesta visão geral."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f81c2d9fc2ec69c295485fe06029b5de65335db0
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="introduction-to-events"></a><span data-ttu-id="b0c05-104">Introdução a Eventos</span><span class="sxs-lookup"><span data-stu-id="b0c05-104">Introduction to Events</span></span>

[<span data-ttu-id="b0c05-105">Anterior</span><span class="sxs-lookup"><span data-stu-id="b0c05-105">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="b0c05-106">Eventos são, assim como delegados, um mecanismo de *associação tardia*.</span><span class="sxs-lookup"><span data-stu-id="b0c05-106">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="b0c05-107">De fato, os eventos são criados com base no suporte de linguagem para delegados.</span><span class="sxs-lookup"><span data-stu-id="b0c05-107">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="b0c05-108">Os eventos são uma forma de um objeto difundir (para todos os componentes interessados do sistema) que algo aconteceu.</span><span class="sxs-lookup"><span data-stu-id="b0c05-108">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="b0c05-109">Qualquer outro componente pode assinar ao evento e ser notificado quando um evento for gerado.</span><span class="sxs-lookup"><span data-stu-id="b0c05-109">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="b0c05-110">Provavelmente, você usou eventos em alguma parte de sua programação.</span><span class="sxs-lookup"><span data-stu-id="b0c05-110">You've probably used events in some of your programming.</span></span> <span data-ttu-id="b0c05-111">Muitos sistemas gráficos têm um modelo de evento para informar a interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="b0c05-111">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="b0c05-112">Esses eventos informariam movimentos do mouse, pressionamentos de botão e interações semelhantes.</span><span class="sxs-lookup"><span data-stu-id="b0c05-112">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="b0c05-113">Esse é um dos cenários mais comuns, mas certamento não o único cenário em que eventos são usados.</span><span class="sxs-lookup"><span data-stu-id="b0c05-113">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="b0c05-114">Você pode definir os eventos que devem ser gerados para suas classes.</span><span class="sxs-lookup"><span data-stu-id="b0c05-114">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="b0c05-115">Uma consideração importante ao trabalhar com eventos é que pode não haver nenhum objeto registrado para um determinado evento.</span><span class="sxs-lookup"><span data-stu-id="b0c05-115">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="b0c05-116">Você deve escrever seu código de modo que ele não gere eventos quando nenhum ouvinte estiver configurado.</span><span class="sxs-lookup"><span data-stu-id="b0c05-116">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="b0c05-117">Assinar um evento também cria um acoplamento entre dois objetos (a origem do evento e o coletor do evento).</span><span class="sxs-lookup"><span data-stu-id="b0c05-117">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="b0c05-118">Você precisa garantir que o coletor do evento cancele a assinatura da origem do evento quando não houver mais interesse nos eventos.</span><span class="sxs-lookup"><span data-stu-id="b0c05-118">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="b0c05-119">Metas de design para o suporte a eventos</span><span class="sxs-lookup"><span data-stu-id="b0c05-119">Design Goals for Event Support</span></span>

<span data-ttu-id="b0c05-120">O design de linguagem para eventos tem como alvo essas metas.</span><span class="sxs-lookup"><span data-stu-id="b0c05-120">The language design for events targets these goals.</span></span>

<span data-ttu-id="b0c05-121">Primeiro, habilite o acoplamento mínimo entre uma origem de evento e um coletor de evento.</span><span class="sxs-lookup"><span data-stu-id="b0c05-121">First, enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="b0c05-122">Esses dois componentes não podem ter sido escritos pela mesma organização e podem até mesmo ser atualizados segundo cronogramas totalmente diferentes.</span><span class="sxs-lookup"><span data-stu-id="b0c05-122">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

<span data-ttu-id="b0c05-123">Em segundo lugar, deve ser muito simples assinar em um evento e cancelar a assinatura desse mesmo evento.</span><span class="sxs-lookup"><span data-stu-id="b0c05-123">Secondly, it should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

<span data-ttu-id="b0c05-124">E, por fim, fontes de eventos devem dar suporte a vários assinantes do evento.</span><span class="sxs-lookup"><span data-stu-id="b0c05-124">And finally, event sources should support multiple event subscribers.</span></span> <span data-ttu-id="b0c05-125">Elas também devem dar suporte a não ter assinantes de evento anexados.</span><span class="sxs-lookup"><span data-stu-id="b0c05-125">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="b0c05-126">Você pode ver que as metas para os eventos são muito semelhantes às metas para delegados.</span><span class="sxs-lookup"><span data-stu-id="b0c05-126">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="b0c05-127">É por isso que o suporte à linguagem do evento é baseado no suporte à linguagem do delegado.</span><span class="sxs-lookup"><span data-stu-id="b0c05-127">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="b0c05-128">Suporte de linguagem para eventos</span><span class="sxs-lookup"><span data-stu-id="b0c05-128">Language Support for Events</span></span>

<span data-ttu-id="b0c05-129">A sintaxe para definir eventos e se inscrever ou cancelar a inscrição em eventos é uma extensão da sintaxe de delegados.</span><span class="sxs-lookup"><span data-stu-id="b0c05-129">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="b0c05-130">Para definir um evento, você use a palavra-chave `event`:</span><span class="sxs-lookup"><span data-stu-id="b0c05-130">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="b0c05-131">O tipo de evento (`EventHandler<FileListArgs>` neste exemplo) deve ser um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="b0c05-131">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="b0c05-132">Há uma série de convenções que você deve seguir ao declarar um evento.</span><span class="sxs-lookup"><span data-stu-id="b0c05-132">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="b0c05-133">Normalmente, o tipo de delegado do evento tem um retorno nulo.</span><span class="sxs-lookup"><span data-stu-id="b0c05-133">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="b0c05-134">Declarações de evento devem ser um verbo ou uma frase verbal.</span><span class="sxs-lookup"><span data-stu-id="b0c05-134">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="b0c05-135">Use o tempo passado (como neste exemplo) quando o evento informar que algo aconteceu.</span><span class="sxs-lookup"><span data-stu-id="b0c05-135">Use past tense (as in this example) when the event reports something that has happened.</span></span> <span data-ttu-id="b0c05-136">Use um tempo verbal presente (por exemplo, `Closing`) para informar algo que está prestes a ocorrer.</span><span class="sxs-lookup"><span data-stu-id="b0c05-136">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="b0c05-137">Frequentemente, usar o tempo presente indica que sua classe dá suporte a algum tipo de comportamento de personalização.</span><span class="sxs-lookup"><span data-stu-id="b0c05-137">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="b0c05-138">Um dos cenários mais comuns é dar suporte ao cancelamento.</span><span class="sxs-lookup"><span data-stu-id="b0c05-138">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="b0c05-139">Por exemplo, um evento `Closing` pode incluir um argumento que indicaria se a operação de encerramento deve continuar ou não.</span><span class="sxs-lookup"><span data-stu-id="b0c05-139">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="b0c05-140">Outros cenários podem permitir que os chamadores modifiquem o comportamento atualizando propriedades dos argumentos do evento.</span><span class="sxs-lookup"><span data-stu-id="b0c05-140">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="b0c05-141">Você pode acionar um evento para indicar uma próxima ação proposta que um algoritmo usará.</span><span class="sxs-lookup"><span data-stu-id="b0c05-141">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="b0c05-142">O manipulador de eventos pode forçar uma ação diferente modificando as propriedades do argumento do evento.</span><span class="sxs-lookup"><span data-stu-id="b0c05-142">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="b0c05-143">Quando quiser acionar o evento, você pode chamar os manipuladores de eventos usando a sintaxe de invocação de delegado:</span><span class="sxs-lookup"><span data-stu-id="b0c05-143">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="b0c05-144">Conforme discutido na seção sobre [delegados](delegates-patterns.md), o operador ?.</span><span class="sxs-lookup"><span data-stu-id="b0c05-144">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="b0c05-145">torna fácil garantir que você não tente acionar o evento quando não houver nenhum assinante do evento.</span><span class="sxs-lookup"><span data-stu-id="b0c05-145">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>
 
<span data-ttu-id="b0c05-146">Assine um evento usando o operador `+=`:</span><span class="sxs-lookup"><span data-stu-id="b0c05-146">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += OnProgress;
```

<span data-ttu-id="b0c05-147">O método do manipulador normalmente é o prefixo "On" seguido do nome do evento, conforme mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="b0c05-147">The handler method typically is the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="b0c05-148">Cancele a assinatura usando o operador `-=`:</span><span class="sxs-lookup"><span data-stu-id="b0c05-148">You unsubscribe using the `-=` operator:</span></span>

```csharp
lister.Progress -= onProgress;
```

<span data-ttu-id="b0c05-149">É importante observar que eu declarei um variável local para a expressão que representa o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="b0c05-149">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="b0c05-150">Isso garante que o cancelamento da assinatura remova o manipulador.</span><span class="sxs-lookup"><span data-stu-id="b0c05-150">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="b0c05-151">Se, em vez disso, você tiver usado o corpo da expressão lambda, você estará tentando remover um manipulador que nunca foi anexado, o que não faz nada.</span><span class="sxs-lookup"><span data-stu-id="b0c05-151">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="b0c05-152">No próximo artigo, você aprenderá mais sobre padrões de evento típicos e diferentes variações deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="b0c05-152">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="b0c05-153">Avançar</span><span class="sxs-lookup"><span data-stu-id="b0c05-153">Next</span></span>](event-pattern.md)

