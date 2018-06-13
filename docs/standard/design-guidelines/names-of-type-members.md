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
ms.openlocfilehash: 25fe93b63c518f54ee72300f26dfcb3f3ad21d76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575343"
---
# <a name="names-of-type-members"></a><span data-ttu-id="345c3-102">Nomes de membros de tipo</span><span class="sxs-lookup"><span data-stu-id="345c3-102">Names of Type Members</span></span>
<span data-ttu-id="345c3-103">São feitas tipos de membros: métodos, propriedades, eventos, construtores e campos.</span><span class="sxs-lookup"><span data-stu-id="345c3-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="345c3-104">As seções a seguir descrevem as diretrizes de nomeação de membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="345c3-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="345c3-105">Nomes de métodos</span><span class="sxs-lookup"><span data-stu-id="345c3-105">Names of Methods</span></span>  
 <span data-ttu-id="345c3-106">Como os métodos são os meios de executar uma ação, as diretrizes de design requerem que os nomes de método verbos ou frases de verbo.</span><span class="sxs-lookup"><span data-stu-id="345c3-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="345c3-107">Seguir essa orientação também serve para distinguir os nomes de método de nomes de propriedade e o tipo, que são frases nominais ou adjetivo.</span><span class="sxs-lookup"><span data-stu-id="345c3-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="345c3-108">**FAZER ✓** atribuir nomes de métodos que são verbos ou frases de verbo.</span><span class="sxs-lookup"><span data-stu-id="345c3-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="345c3-109">Nomes de propriedades</span><span class="sxs-lookup"><span data-stu-id="345c3-109">Names of Properties</span></span>  
 <span data-ttu-id="345c3-110">Ao contrário de outros membros, propriedades devem ser dadas locução ou nomes de adjetivo.</span><span class="sxs-lookup"><span data-stu-id="345c3-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="345c3-111">Isso ocorre porque uma propriedade refere-se aos dados e o nome da propriedade reflete que.</span><span class="sxs-lookup"><span data-stu-id="345c3-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="345c3-112">PascalCasing sempre é usado para nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="345c3-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="345c3-113">**FAZER ✓** propriedades usando um substantivo, locução ou adjetivo nomes.</span><span class="sxs-lookup"><span data-stu-id="345c3-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="345c3-114">**X não** têm propriedades que correspondem ao nome de "Get" métodos como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="345c3-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="345c3-115">Esse padrão geralmente indica que a propriedade deve ser realmente um método.</span><span class="sxs-lookup"><span data-stu-id="345c3-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="345c3-116">**FAZER ✓** nome propriedades de coleção com plural frase que descreve os itens na coleção em vez de usar uma frase singular seguida por "List" ou "Coleção".</span><span class="sxs-lookup"><span data-stu-id="345c3-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="345c3-117">**FAZER ✓** nome propriedades Boolianas com uma frase afirmativa (`CanSeek` em vez de `CantSeek`).</span><span class="sxs-lookup"><span data-stu-id="345c3-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="345c3-118">Opcionalmente, você também poderá colocar propriedades Boolianas com "É", "pode" ou "Tem", mas somente quando ele agrega valor.</span><span class="sxs-lookup"><span data-stu-id="345c3-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="345c3-119">**✓ CONSIDERE** fornecendo uma propriedade o mesmo nome de seu tipo.</span><span class="sxs-lookup"><span data-stu-id="345c3-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="345c3-120">Por exemplo, a seguinte propriedade corretamente obtém e define um valor de enumeração denominado `Color`, portanto, a propriedade é denominada `Color`:</span><span class="sxs-lookup"><span data-stu-id="345c3-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="345c3-121">Nomes de eventos</span><span class="sxs-lookup"><span data-stu-id="345c3-121">Names of Events</span></span>  
 <span data-ttu-id="345c3-122">Sempre consultem eventos alguma ação, que está acontecendo ou que ocorreu.</span><span class="sxs-lookup"><span data-stu-id="345c3-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="345c3-123">Portanto, como com métodos, eventos são nomeados com verbos e indicativo de verbo é usado para indicar o momento quando o evento é gerado.</span><span class="sxs-lookup"><span data-stu-id="345c3-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="345c3-124">**FAZER ✓** nome eventos com um verbo ou uma frase de verbo.</span><span class="sxs-lookup"><span data-stu-id="345c3-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="345c3-125">Os exemplos incluem `Clicked`, `Painting`, `DroppedDown`e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="345c3-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="345c3-126">**FAZER ✓** atribuir nomes de eventos com um conceito de antes e depois, usando o presente e tempos de passado.</span><span class="sxs-lookup"><span data-stu-id="345c3-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="345c3-127">Por exemplo, um evento de fechamento é gerado antes de fechar uma janela será chamado `Closing`, e que é gerado depois que a janela for fechada será chamado `Closed`.</span><span class="sxs-lookup"><span data-stu-id="345c3-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="345c3-128">**X não** usar "Antes" ou "Depois" prefixos ou postfixes para indicar pré e pós-eventos.</span><span class="sxs-lookup"><span data-stu-id="345c3-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="345c3-129">Use presente e tempos de passado como acabou de ser descrita.</span><span class="sxs-lookup"><span data-stu-id="345c3-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="345c3-130">**FAZER ✓** nome manipuladores de eventos (delegados são usados como tipos de eventos) com o sufixo "EventHandler", conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="345c3-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="345c3-131">**FAZER ✓** usa dois parâmetros nomeados `sender` e `e` em manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="345c3-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="345c3-132">O parâmetro do remetente representa o objeto que gerou o evento.</span><span class="sxs-lookup"><span data-stu-id="345c3-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="345c3-133">O parâmetro do remetente normalmente é do tipo `object`, mesmo que seja possível usar um tipo mais específico.</span><span class="sxs-lookup"><span data-stu-id="345c3-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="345c3-134">**FAZER ✓** nome do evento de classes de argumento com o sufixo "EventArgs".</span><span class="sxs-lookup"><span data-stu-id="345c3-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="345c3-135">Nomes de campos</span><span class="sxs-lookup"><span data-stu-id="345c3-135">Names of Fields</span></span>  
 <span data-ttu-id="345c3-136">As diretrizes de nomenclatura de campo se aplicam a campos protegidos e públicos estáticos.</span><span class="sxs-lookup"><span data-stu-id="345c3-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="345c3-137">Campos internos e privados não são cobertos pelas diretrizes e campos de instância público ou protegido não são permitidos pelo [diretrizes de design do membro](../../../docs/standard/design-guidelines/member.md).</span><span class="sxs-lookup"><span data-stu-id="345c3-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="345c3-138">**FAZER ✓** use PascalCasing em nomes de campo.</span><span class="sxs-lookup"><span data-stu-id="345c3-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="345c3-139">**FAZER ✓** nome campos usando um substantivo, locução ou adjetivo.</span><span class="sxs-lookup"><span data-stu-id="345c3-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="345c3-140">**X não** use um prefixo para nomes de campo.</span><span class="sxs-lookup"><span data-stu-id="345c3-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="345c3-141">Por exemplo, não use "g _" ou "s _" para indicar campos estáticos.</span><span class="sxs-lookup"><span data-stu-id="345c3-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="345c3-142">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="345c3-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="345c3-143">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="345c3-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="345c3-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="345c3-144">See Also</span></span>  
 [<span data-ttu-id="345c3-145">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="345c3-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="345c3-146">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="345c3-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
