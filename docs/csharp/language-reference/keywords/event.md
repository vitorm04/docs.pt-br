---
title: "event (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
dev_langs:
- CSharp
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
caps.latest.revision: 28
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 674e36625a68243afff75f6c5028309dc7aff02a
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="event-c-reference"></a><span data-ttu-id="85118-102">event (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="85118-102">event (C# Reference)</span></span>
<span data-ttu-id="85118-103">A palavra-chave `event` é usada para declarar um evento em uma classe publicadora.</span><span class="sxs-lookup"><span data-stu-id="85118-103">The `event` keyword is used to declare an event in a publisher class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85118-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="85118-104">Example</span></span>  
 <span data-ttu-id="85118-105">O exemplo a seguir mostra como declarar e acionar um evento que usa o <xref:System.EventHandler> como o tipo delegado subjacente.</span><span class="sxs-lookup"><span data-stu-id="85118-105">The following example shows how to declare and raise an event that uses <xref:System.EventHandler> as the underlying delegate type.</span></span> <span data-ttu-id="85118-106">Para obter o exemplo de código completo, que também mostra como usar o tipo delegado <xref:System.EventHandler%601> genérico e como assinar um evento e criar um método de manipulador de eventos, consulte [Como publicar eventos em conformidade com as diretrizes do .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="85118-106">For the complete code example that also shows how to use the generic <xref:System.EventHandler%601> delegate type and how to subscribe to an event and create an event handler method, see [How to: Publish Events that Conform to .NET Framework Guidelines](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).</span></span>  
  
 <span data-ttu-id="85118-107">[!code-cs[csrefKeywordsModifiers#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/event_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="85118-107">[!code-cs[csrefKeywordsModifiers#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/event_1.cs)]</span></span>  
  
 <span data-ttu-id="85118-108">Os eventos são um tipo especial de delegado multicast que só podem ser invocados de dentro da classe ou struct em que eles são declarados (a classe publicadora).</span><span class="sxs-lookup"><span data-stu-id="85118-108">Events are a special kind of multicast delegate that can only be invoked from within the class or struct where they are declared (the publisher class).</span></span> <span data-ttu-id="85118-109">Se outras classes ou structs assinarem o evento, seus respectivos métodos de manipulador de eventos serão chamados quando a classe publicadora acionar o evento.</span><span class="sxs-lookup"><span data-stu-id="85118-109">If other classes or structs subscribe to the event, their event handler methods will be called when the publisher class raises the event.</span></span> <span data-ttu-id="85118-110">Para obter mais informações e exemplos de código, consulte [Eventos](../../../csharp/programming-guide/events/index.md) e [Delegados](../../../csharp/programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="85118-110">For more information and code examples, see [Events](../../../csharp/programming-guide/events/index.md) and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
 <span data-ttu-id="85118-111">Os eventos podem ser marcados como [públicos](../../../csharp/language-reference/keywords/public.md), [particulares](../../../csharp/language-reference/keywords/private.md), [protegidos](../../../csharp/language-reference/keywords/protected.md), [internos](../../../csharp/language-reference/keywords/internal.md) ou `protected internal`.</span><span class="sxs-lookup"><span data-stu-id="85118-111">Events can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or `protected internal`.</span></span> <span data-ttu-id="85118-112">Esses modificadores de acesso definem como os usuários da classe podem acessar o evento.</span><span class="sxs-lookup"><span data-stu-id="85118-112">These access modifiers define how users of the class can access the event.</span></span> <span data-ttu-id="85118-113">Para obter mais informações, consulte [Modificadores de Acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="85118-113">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="keywords-and-events"></a><span data-ttu-id="85118-114">Palavras-chave e eventos</span><span class="sxs-lookup"><span data-stu-id="85118-114">Keywords and Events</span></span>  
 <span data-ttu-id="85118-115">As palavras-chave a seguir aplicam-se a eventos.</span><span class="sxs-lookup"><span data-stu-id="85118-115">The following keywords apply to events.</span></span>  
  
|<span data-ttu-id="85118-116">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="85118-116">Keyword</span></span>|<span data-ttu-id="85118-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="85118-117">Description</span></span>|<span data-ttu-id="85118-118">Para obter mais informações</span><span class="sxs-lookup"><span data-stu-id="85118-118">For more information</span></span>|  
|-------------|-----------------|--------------------------|  
|[<span data-ttu-id="85118-119">static</span><span class="sxs-lookup"><span data-stu-id="85118-119">static</span></span>](../../../csharp/language-reference/keywords/static.md)|<span data-ttu-id="85118-120">Torna o evento disponível para chamadores a qualquer momento, mesmo se não existir nenhuma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="85118-120">Makes the event available to callers at any time, even if no instance of the class exists.</span></span>|[<span data-ttu-id="85118-121">Classes static e membros de classes static</span><span class="sxs-lookup"><span data-stu-id="85118-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[<span data-ttu-id="85118-122">virtual</span><span class="sxs-lookup"><span data-stu-id="85118-122">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="85118-123">Permite que classes derivadas substituam o comportamento do evento, usando a palavra-chave [override](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="85118-123">Allows derived classes to override the event behavior by using the [override](../../../csharp/language-reference/keywords/override.md) keyword.</span></span>|[<span data-ttu-id="85118-124">Herança</span><span class="sxs-lookup"><span data-stu-id="85118-124">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[<span data-ttu-id="85118-125">sealed</span><span class="sxs-lookup"><span data-stu-id="85118-125">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)|<span data-ttu-id="85118-126">Especifica que, para classes derivadas, o evento não é mais virtual.</span><span class="sxs-lookup"><span data-stu-id="85118-126">Specifies that for derived classes it is no longer virtual.</span></span>||  
|[<span data-ttu-id="85118-127">abstract</span><span class="sxs-lookup"><span data-stu-id="85118-127">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="85118-128">O compilador não gerará mais os blocos de acessador de evento `add` e `remove`, portanto, as classes derivadas devem fornecer sua própria implementação.</span><span class="sxs-lookup"><span data-stu-id="85118-128">The compiler will not generate the `add` and `remove` event accessor blocks and therefore derived classes must provide their own implementation.</span></span>||  
  
 <span data-ttu-id="85118-129">Um evento pode ser declarado como um evento estático, usando apalavra-chave [static](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="85118-129">An event may be declared as a static event by using the [static](../../../csharp/language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="85118-130">Isso torna o evento disponível para chamadores a qualquer momento, mesmo se não existir nenhuma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="85118-130">This makes the event available to callers at any time, even if no instance of the class exists.</span></span> <span data-ttu-id="85118-131">Para obter mais informações, consulte [Classes Estáticas e Membros de Classes Estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="85118-131">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="85118-132">Um evento pode ser marcado como um evento virtual, usando a palavra-chave [virtual](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="85118-132">An event can be marked as a virtual event by using the [virtual](../../../csharp/language-reference/keywords/virtual.md) keyword.</span></span> <span data-ttu-id="85118-133">Isso habilita as classes derivadas a substituírem o comportamento do evento, usando a palavra-chave [override](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="85118-133">This enables derived classes to override the event behavior by using the [override](../../../csharp/language-reference/keywords/override.md) keyword.</span></span> <span data-ttu-id="85118-134">Para obter mais informações, consulte [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="85118-134">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span> <span data-ttu-id="85118-135">Um evento que substitui um evento virtual também pode ser [sealed](../../../csharp/language-reference/keywords/sealed.md), o que especifica que ele não é mais virtual para classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="85118-135">An event overriding a virtual event can also be [sealed](../../../csharp/language-reference/keywords/sealed.md), which specifies that for derived classes it is no longer virtual.</span></span> <span data-ttu-id="85118-136">Por fim, um evento pode ser declarado [abstract](../../../csharp/language-reference/keywords/abstract.md), o que significa que o compilador não gerará os blocos de acessador de evento `add` e `remove`.</span><span class="sxs-lookup"><span data-stu-id="85118-136">Lastly, an event can be declared [abstract](../../../csharp/language-reference/keywords/abstract.md), which means that the compiler will not generate the `add` and `remove` event accessor blocks.</span></span> <span data-ttu-id="85118-137">Portanto, classes derivadas devem fornecer sua própria implementação.</span><span class="sxs-lookup"><span data-stu-id="85118-137">Therefore derived classes must provide their own implementation.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="85118-138">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="85118-138">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="85118-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85118-139">See Also</span></span>  
 <span data-ttu-id="85118-140">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="85118-140">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="85118-141">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="85118-141">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="85118-142">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="85118-142">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="85118-143">[add](../../../csharp/language-reference/keywords/add.md) </span><span class="sxs-lookup"><span data-stu-id="85118-143">[add](../../../csharp/language-reference/keywords/add.md) </span></span>  
 <span data-ttu-id="85118-144">[remove](../../../csharp/language-reference/keywords/remove.md) </span><span class="sxs-lookup"><span data-stu-id="85118-144">[remove](../../../csharp/language-reference/keywords/remove.md) </span></span>  
 <span data-ttu-id="85118-145">[Modificadores](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="85118-145">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 [<span data-ttu-id="85118-146">Como combinar delegados (delegados multicast)</span><span class="sxs-lookup"><span data-stu-id="85118-146">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)

