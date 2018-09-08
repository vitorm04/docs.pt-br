---
title: Nomes de membros de tipo
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0541f100f208543c796de7238e68ea6f90c7b299
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44205173"
---
# <a name="names-of-type-members"></a><span data-ttu-id="1e5a5-102">Nomes de membros de tipo</span><span class="sxs-lookup"><span data-stu-id="1e5a5-102">Names of Type Members</span></span>
<span data-ttu-id="1e5a5-103">Tipos são compostos de membros: métodos, propriedades, eventos, construtores e campos.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="1e5a5-104">As seções a seguir descrevem as diretrizes de nomenclatura de membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="1e5a5-105">Nomes de métodos</span><span class="sxs-lookup"><span data-stu-id="1e5a5-105">Names of Methods</span></span>  
 <span data-ttu-id="1e5a5-106">Como os métodos são os meios para executar uma ação, as diretrizes de design exigem que os nomes de métodos sejam verbos ou frases verbais.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="1e5a5-107">Seguir essa diretriz também serve para distinguir os nomes de métodos de nomes de propriedades e tipos, que são substantivos ou frases adjetivas.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="1e5a5-108">**✓ DO** nomeie os métodos que são verbos ou frases verbais.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="1e5a5-109">Nomes de propriedades</span><span class="sxs-lookup"><span data-stu-id="1e5a5-109">Names of Properties</span></span>  
 <span data-ttu-id="1e5a5-110">Diferentemente de outros membros, as propriedades devem ser nomeadas com uma frase substantivada ou um adjetivo.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="1e5a5-111">Isso porque uma propriedade se refere a dados, e o nome da propriedade reflete isso.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="1e5a5-112">PascalCasing sempre é usado para nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="1e5a5-113">**✓ DO** nomeie as propriedades usando um substantivo, uma frase substantivada ou um adjetivo.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="1e5a5-114">**X DO NOT** não tenha propriedades que correspondam ao nome dos métodos "Get", como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1e5a5-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="1e5a5-115">Esse padrão geralmente indica que a propriedade deveria realmente ser um método.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="1e5a5-116">**✓ DO** nomeie as propriedades de coleção com uma frase no plural que descreva os itens na coleção em vez de usar uma frase no singular seguida por "List" ou "Collection".</span><span class="sxs-lookup"><span data-stu-id="1e5a5-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="1e5a5-117">**✓ DO** nomeie as propriedades boolianas com uma frase afirmativa (`CanSeek` em vez de `CantSeek`).</span><span class="sxs-lookup"><span data-stu-id="1e5a5-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="1e5a5-118">Opcionalmente, você também pode prefixar as propriedades boolianas com "Is", "Can" ou "Has", mas somente quando adicionar valor.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="1e5a5-119">**✓ CONSIDER** nomeie uma propriedade com o mesmo nome de seu tipo.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="1e5a5-120">Por exemplo, a seguinte propriedade obtém e define corretamente um valor de enumeração denominado `Color`, portanto, a propriedade é chamada `Color`:</span><span class="sxs-lookup"><span data-stu-id="1e5a5-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="1e5a5-121">Nomes de eventos</span><span class="sxs-lookup"><span data-stu-id="1e5a5-121">Names of Events</span></span>  
 <span data-ttu-id="1e5a5-122">Eventos sempre fazem referência a uma ação, seja uma ação que está acontecendo ou que já ocorreu.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="1e5a5-123">Portanto, assim como acontece com os métodos, os eventos são nomeados com verbos e o tempo verbal é usado para indicar o horário em que o evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="1e5a5-124">**✓ DO** nomeie os eventos com um verbo ou uma frase verbal.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="1e5a5-125">Os exemplos incluem `Clicked`, `Painting`, `DroppedDown`, etc.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="1e5a5-126">**✓ DO** nomeie os eventos com um conceito de antes e depois, usando os tempos verbais Pretérito e Presente.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="1e5a5-127">Por exemplo, um evento de fechamento gerado antes de uma janela ser fechada seria chamado de `Closing`, e um gerado após a janela ser fechada seria chamado de `Closed`.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="1e5a5-128">**X DO NOT** não use os sufixos ou prefixos "Before" ou "After" para indicar eventos anteriores e posteriores.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="1e5a5-129">Use os tempos verbais Pretérito e Presente conforme descrito.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="1e5a5-130">**✓ DO** nomeie manipuladores de eventos (delegados usados como tipos de eventos) com o sufixo "EventHandler", conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1e5a5-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="1e5a5-131">**✓ DO** use dois parâmetros nomeados `sender` e `e` nos manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="1e5a5-132">O parâmetro do remetente representa o objeto que acionou o evento.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="1e5a5-133">O parâmetro do remetente normalmente é do tipo `object`, mesmo se for possível empregar um tipo mais específico.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="1e5a5-134">**✓ DO** nomeie classes de argumento de evento com o sufixo "EventArgs".</span><span class="sxs-lookup"><span data-stu-id="1e5a5-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="1e5a5-135">Nomes de campos</span><span class="sxs-lookup"><span data-stu-id="1e5a5-135">Names of Fields</span></span>  
 <span data-ttu-id="1e5a5-136">As diretrizes de nomenclatura de campo se aplicam a campos públicos e protegidos estáticos.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="1e5a5-137">Campos particulares e internos não são cobertos pelas diretrizes, e campos de instância pública ou protegida não são permitidos pelas [diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md).</span><span class="sxs-lookup"><span data-stu-id="1e5a5-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="1e5a5-138">**✓ DO** use PascalCasing nos nomes de campos.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="1e5a5-139">**✓ DO** nomeie os campos usando um substantivo, uma frase substantivada ou um adjetivo.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="1e5a5-140">**X DO NOT** não use um prefixo para nomes de campos.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="1e5a5-141">Por exemplo, não use "g_" ou "s_" para indicar campos estáticos.</span><span class="sxs-lookup"><span data-stu-id="1e5a5-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="1e5a5-142">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="1e5a5-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1e5a5-143">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="1e5a5-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5a5-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e5a5-144">See also</span></span>

- [<span data-ttu-id="1e5a5-145">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="1e5a5-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="1e5a5-146">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="1e5a5-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
