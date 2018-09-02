---
title: Nomes de Classes, Structs e Interfaces
ms.date: 03/30/2017
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f60a2283c01d0dc2665dafaa99ea52000aa3bc47
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407480"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="b1368-102">Nomes de Classes, Structs e Interfaces</span><span class="sxs-lookup"><span data-stu-id="b1368-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="b1368-103">As diretrizes de nomenclatura que seguem se aplicam a nomenclatura de tipo geral.</span><span class="sxs-lookup"><span data-stu-id="b1368-103">The naming guidelines that follow apply to general type naming.</span></span>  
  
 <span data-ttu-id="b1368-104">**✓ DO** nome classes e estruturas com substantivos e frases nominais, usando PascalCasing.</span><span class="sxs-lookup"><span data-stu-id="b1368-104">**✓ DO** name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>  
  
 <span data-ttu-id="b1368-105">Isso distingue nomes de tipo de métodos, que são nomeados com frases verbais.</span><span class="sxs-lookup"><span data-stu-id="b1368-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>  
  
 <span data-ttu-id="b1368-106">**✓ DO** nome interfaces adjetivas frases ou ocasionalmente com substantivos e frases nominais.</span><span class="sxs-lookup"><span data-stu-id="b1368-106">**✓ DO** name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="b1368-107">Substantivos e frases nominais raramente devem ser usados e eles podem indicar que o tipo deve ser uma classe abstrata e não uma interface.</span><span class="sxs-lookup"><span data-stu-id="b1368-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>  
  
 <span data-ttu-id="b1368-108">**X DO NOT** dar nomes de classe um prefixo (por exemplo, "C").</span><span class="sxs-lookup"><span data-stu-id="b1368-108">**X DO NOT** give class names a prefix (e.g., "C").</span></span>  
  
 <span data-ttu-id="b1368-109">**✓ CONSIDER** encerrar o nome de classes derivadas com o nome de classe base.</span><span class="sxs-lookup"><span data-stu-id="b1368-109">**✓ CONSIDER** ending the name of derived classes with the name of the base class.</span></span>  
  
 <span data-ttu-id="b1368-110">Isso é muito legível e explica a relação claramente.</span><span class="sxs-lookup"><span data-stu-id="b1368-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="b1368-111">Alguns exemplos no código são: `ArgumentOutOfRangeException`, que é um tipo de `Exception`, e `SerializableAttribute`, que é uma espécie de `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="b1368-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="b1368-112">No entanto, é importante que você use o bom senso razoável na aplicação essa diretriz; Por exemplo, o `Button` classe é um tipo de `Control` evento, embora `Control` não aparecer em seu nome.</span><span class="sxs-lookup"><span data-stu-id="b1368-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>  
  
 <span data-ttu-id="b1368-113">**✓ DO** nomes de interface de prefixo com a letra que, para indicar que o tipo é uma interface.</span><span class="sxs-lookup"><span data-stu-id="b1368-113">**✓ DO** prefix interface names with the letter I, to indicate that the type is an interface.</span></span>  
  
 <span data-ttu-id="b1368-114">Por exemplo, `IComponent` (substantivo descritivo), `ICustomAttributeProvider` (frase substantiva), e `IPersistable` (adjetivo) são os nomes de interface apropriada.</span><span class="sxs-lookup"><span data-stu-id="b1368-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="b1368-115">Assim como acontece com outros nomes de tipo, evite abreviações.</span><span class="sxs-lookup"><span data-stu-id="b1368-115">As with other type names, avoid abbreviations.</span></span>  
  
 <span data-ttu-id="b1368-116">**✓ DO** Certifique-se de que os nomes diferem somente por "I" prefixo no nome da interface quando você está definindo um par de classe – interface em que a classe é uma implementação padrão da interface.</span><span class="sxs-lookup"><span data-stu-id="b1368-116">**✓ DO** ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>  
  
## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="b1368-117">Nomes dos parâmetros de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="b1368-117">Names of Generic Type Parameters</span></span>  
 <span data-ttu-id="b1368-118">Genéricos foram adicionados ao .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="b1368-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="b1368-119">O recurso introduziu um novo tipo de identificador chamado *parâmetro de tipo*.</span><span class="sxs-lookup"><span data-stu-id="b1368-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>  
  
 <span data-ttu-id="b1368-120">**✓ DO** nome parâmetros de tipo genérico com nomes descritivos, a menos que o nome de um única letra é totalmente auto-explicativo e um nome descritivo não seria adicionar valor.</span><span class="sxs-lookup"><span data-stu-id="b1368-120">**✓ DO** name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>  
  
 <span data-ttu-id="b1368-121">**✓ CONSIDER** usando `T` como o nome do parâmetro de tipo para tipos com um parâmetro de tipo de letra único.</span><span class="sxs-lookup"><span data-stu-id="b1368-121">**✓ CONSIDER** using `T` as the type parameter name for types with one single-letter type parameter.</span></span>  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 <span data-ttu-id="b1368-122">**✓ DO** prefixo nomes de parâmetro de tipo descritivo com `T`.</span><span class="sxs-lookup"><span data-stu-id="b1368-122">**✓ DO** prefix descriptive type parameter names with `T`.</span></span>  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 <span data-ttu-id="b1368-123">**✓ CONSIDER** indicando a restrições colocadas em um parâmetro de tipo no nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b1368-123">**✓ CONSIDER** indicating constraints placed on a type parameter in the name of the parameter.</span></span>  
  
 <span data-ttu-id="b1368-124">Por exemplo, um parâmetro restrito a `ISession` pode ser chamado `TSession`.</span><span class="sxs-lookup"><span data-stu-id="b1368-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>  
  
## <a name="names-of-common-types"></a><span data-ttu-id="b1368-125">Nomes dos tipos comuns</span><span class="sxs-lookup"><span data-stu-id="b1368-125">Names of Common Types</span></span>  
 <span data-ttu-id="b1368-126">**✓ DO** siga as diretrizes descritas na tabela a seguir ao nomear tipos derivados de ou implementar certos tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1368-126">**✓ DO** follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>  
  
|<span data-ttu-id="b1368-127">Tipo base</span><span class="sxs-lookup"><span data-stu-id="b1368-127">Base Type</span></span>|<span data-ttu-id="b1368-128">Diretriz de tipo derivado/implementação</span><span class="sxs-lookup"><span data-stu-id="b1368-128">Derived/Implementing Type Guideline</span></span>|  
|---------------|------------------------------------------|  
|`System.Attribute`|<span data-ttu-id="b1368-129">**✓ DO** adicionar o sufixo "Atributo" em nomes de classes de atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="b1368-129">**✓ DO** add the suffix "Attribute" to names of custom attribute classes.</span></span>|  
|`System.Delegate`|<span data-ttu-id="b1368-130">**✓ DO** adicionar o sufixo "EventHandler" em nomes de representantes que são usados em eventos.</span><span class="sxs-lookup"><span data-stu-id="b1368-130">**✓ DO** add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="b1368-131">**✓ DO** adicionar o sufixo "Retorno de chamada" para nomes de representantes de diferentes dos usados como manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="b1368-131">**✓ DO** add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="b1368-132">**X DO NOT** adicionar o sufixo "Representante" a um delegado.</span><span class="sxs-lookup"><span data-stu-id="b1368-132">**X DO NOT** add the suffix "Delegate" to a delegate.</span></span>|  
|`System.EventArgs`|<span data-ttu-id="b1368-133">**✓ DO** adicionar o sufixo "EventArgs".</span><span class="sxs-lookup"><span data-stu-id="b1368-133">**✓ DO** add the suffix "EventArgs."</span></span>|  
|`System.Enum`|<span data-ttu-id="b1368-134">**X DO NOT** derivar desta classe; use a palavra-chave com suporte em vez disso, o idioma; por exemplo, no c#, use o `enum` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b1368-134">**X DO NOT** derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="b1368-135">**X DO NOT** adicionar o sufixo "Enum" ou "Sinalizador".</span><span class="sxs-lookup"><span data-stu-id="b1368-135">**X DO NOT** add the suffix "Enum" or "Flag."</span></span>|  
|`System.Exception`|<span data-ttu-id="b1368-136">**✓ DO** adicionar o sufixo "Exception".</span><span class="sxs-lookup"><span data-stu-id="b1368-136">**✓ DO** add the suffix "Exception."</span></span>|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="b1368-137">**✓ DO** adicionar o sufixo "Dicionário".</span><span class="sxs-lookup"><span data-stu-id="b1368-137">**✓ DO** add the suffix "Dictionary."</span></span> <span data-ttu-id="b1368-138">Observe que `IDictionary` é um tipo específico da coleção, mas essa diretriz tem precedência sobre a orientação mais geral de coleções que segue.</span><span class="sxs-lookup"><span data-stu-id="b1368-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="b1368-139">**✓ DO** adicionar o sufixo "Coleção".</span><span class="sxs-lookup"><span data-stu-id="b1368-139">**✓ DO** add the suffix "Collection."</span></span>|  
|`System.IO.Stream`|<span data-ttu-id="b1368-140">**✓ DO** adicionar o sufixo "Fluxo".</span><span class="sxs-lookup"><span data-stu-id="b1368-140">**✓ DO** add the suffix "Stream."</span></span>|  
|`CodeAccessPermission IPermission`|<span data-ttu-id="b1368-141">**✓ DO** adicionar o sufixo "Permissão".</span><span class="sxs-lookup"><span data-stu-id="b1368-141">**✓ DO** add the suffix "Permission."</span></span>|  
  
## <a name="naming-enumerations"></a><span data-ttu-id="b1368-142">Enumerações de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="b1368-142">Naming Enumerations</span></span>  
 <span data-ttu-id="b1368-143">Nomes de tipos de enumeração (também chamados de enums) em geral devem seguir as padrão de nomenclatura de tipo de regras (PascalCasing, etc.).</span><span class="sxs-lookup"><span data-stu-id="b1368-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="b1368-144">No entanto, há diretrizes adicionais se aplicam especificamente aos enums.</span><span class="sxs-lookup"><span data-stu-id="b1368-144">However, there are additional guidelines that apply specifically to enums.</span></span>  
  
 <span data-ttu-id="b1368-145">**✓ DO** usar um nome de tipo singular para uma enumeração, a menos que seus valores são os campos de bits.</span><span class="sxs-lookup"><span data-stu-id="b1368-145">**✓ DO** use a singular type name for an enumeration unless its values are bit fields.</span></span>  
  
 <span data-ttu-id="b1368-146">**✓ DO** usar um nome de tipo no plural para uma enumeração com campos de bits como valores, também chamados de enum de sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="b1368-146">**✓ DO** use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>  
  
 <span data-ttu-id="b1368-147">**X DO NOT** use um sufixo "Enum" em nomes de tipo de enum.</span><span class="sxs-lookup"><span data-stu-id="b1368-147">**X DO NOT** use an "Enum" suffix in enum type names.</span></span>  
  
 <span data-ttu-id="b1368-148">**X DO NOT** usar "Sinalizador" ou nomes de tipo sufixos "Sinalizadores" em enum.</span><span class="sxs-lookup"><span data-stu-id="b1368-148">**X DO NOT** use "Flag" or "Flags" suffixes in enum type names.</span></span>  
  
 <span data-ttu-id="b1368-149">**X DO NOT** usar um prefixo nos nomes de valor de enumeração (por exemplo, "ad" para ADO enums.), "rtf" para enums RTF, etc.</span><span class="sxs-lookup"><span data-stu-id="b1368-149">**X DO NOT** use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>  
  
 <span data-ttu-id="b1368-150">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="b1368-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b1368-151">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="b1368-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1368-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1368-152">See Also</span></span>  
 [<span data-ttu-id="b1368-153">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="b1368-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="b1368-154">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="b1368-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
