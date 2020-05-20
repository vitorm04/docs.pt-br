---
title: Nomes de classes, structs e interfaces
description: Use estas diretrizes para nomear classes, estruturas e interfaces como parte das diretrizes para criar bibliotecas que estendem e interajam com bibliotecas .NET.
ms.date: 10/22/2008
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
ms.openlocfilehash: e7eee414c5bf5c69f63543ef240e50a4d2d948a3
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419077"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="69e16-103">Nomes de classes, structs e interfaces</span><span class="sxs-lookup"><span data-stu-id="69e16-103">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="69e16-104">As diretrizes de nomenclatura a seguir se aplicam à nomenclatura de tipo geral.</span><span class="sxs-lookup"><span data-stu-id="69e16-104">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="69e16-105">✔️ as classes de nome e structs com frases substantivas ou substantivo, usando PascalCasing.</span><span class="sxs-lookup"><span data-stu-id="69e16-105">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="69e16-106">Isso distingue nomes de tipos de métodos, que são nomeados com frases de verbo.</span><span class="sxs-lookup"><span data-stu-id="69e16-106">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="69e16-107">✔️ as interfaces de nome com frases de adjetivo ou ocasionalmente com substantivos ou frases de substantivo.</span><span class="sxs-lookup"><span data-stu-id="69e16-107">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="69e16-108">As frases de substantivo e substantivo devem ser usadas raramente e podem indicar que o tipo deve ser uma classe abstrata, e não uma interface.</span><span class="sxs-lookup"><span data-stu-id="69e16-108">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="69e16-109">❌Não dê aos nomes de classe um prefixo (por exemplo, "C").</span><span class="sxs-lookup"><span data-stu-id="69e16-109">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="69e16-110">✔️ Considere encerrar o nome de classes derivadas com o nome da classe base.</span><span class="sxs-lookup"><span data-stu-id="69e16-110">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="69e16-111">Isso é muito legível e explica a relação claramente.</span><span class="sxs-lookup"><span data-stu-id="69e16-111">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="69e16-112">Alguns exemplos disso no código são: `ArgumentOutOfRangeException` , que é um tipo de `Exception` , e `SerializableAttribute` , que é um tipo de `Attribute` .</span><span class="sxs-lookup"><span data-stu-id="69e16-112">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="69e16-113">No entanto, é importante usar o julgamento razoável na aplicação dessa diretriz; por exemplo, a `Button` classe é um tipo de `Control` evento, embora `Control` não apareça em seu nome.</span><span class="sxs-lookup"><span data-stu-id="69e16-113">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="69e16-114">✔️ os nomes de interface de prefixo com a letra I, para indicar que o tipo é uma interface.</span><span class="sxs-lookup"><span data-stu-id="69e16-114">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="69e16-115">Por exemplo, `IComponent` (substantivo descritivo), `ICustomAttributeProvider` (frase de substantivo) e `IPersistable` (adjetivo) são nomes de interface apropriados.</span><span class="sxs-lookup"><span data-stu-id="69e16-115">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="69e16-116">Assim como ocorre com outros nomes de tipo, evite abreviações.</span><span class="sxs-lookup"><span data-stu-id="69e16-116">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="69e16-117">✔️ garantir que os nomes diferem somente pelo prefixo "I" no nome da interface quando você estiver definindo um par de interface – classe em que a classe é uma implementação padrão da interface.</span><span class="sxs-lookup"><span data-stu-id="69e16-117">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="69e16-118">Nomes de parâmetros de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="69e16-118">Names of Generic Type Parameters</span></span>
 <span data-ttu-id="69e16-119">Os genéricos foram adicionados ao .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="69e16-119">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="69e16-120">O recurso introduziu um novo tipo de identificador chamado *parâmetro de tipo*.</span><span class="sxs-lookup"><span data-stu-id="69e16-120">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="69e16-121">✔️ os parâmetros de tipo genérico de nome com nomes descritivos, a menos que um nome de letra única seja totalmente auto-explicativo e um nome descritivo não adicione valor.</span><span class="sxs-lookup"><span data-stu-id="69e16-121">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="69e16-122">✔️ Considere usar `T` como o nome do parâmetro de tipo para tipos com um parâmetro de tipo de letra única.</span><span class="sxs-lookup"><span data-stu-id="69e16-122">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="69e16-123">✔️ os nomes de parâmetro de tipo descritivo de prefixo com `T` .</span><span class="sxs-lookup"><span data-stu-id="69e16-123">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="69e16-124">✔️ CONSIDERAR a indicação de restrições colocadas em um parâmetro de tipo no nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="69e16-124">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="69e16-125">Por exemplo, um parâmetro restrito a `ISession` pode ser chamado `TSession` .</span><span class="sxs-lookup"><span data-stu-id="69e16-125">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="69e16-126">Nomes de tipos comuns</span><span class="sxs-lookup"><span data-stu-id="69e16-126">Names of Common Types</span></span>
 <span data-ttu-id="69e16-127">✔️ Siga as diretrizes descritas na tabela a seguir ao nomear tipos derivados ou implementando determinados tipos de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="69e16-127">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="69e16-128">Tipo base</span><span class="sxs-lookup"><span data-stu-id="69e16-128">Base Type</span></span>|<span data-ttu-id="69e16-129">Diretriz de tipo derivado/implementando</span><span class="sxs-lookup"><span data-stu-id="69e16-129">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="69e16-130">✔️ Adicionar o sufixo "Attribute" aos nomes das classes de atributo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="69e16-130">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="69e16-131">✔️ Adicionar o sufixo "EventHandler" aos nomes de delegados que são usados em eventos.</span><span class="sxs-lookup"><span data-stu-id="69e16-131">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="69e16-132">✔️ Adicionar o sufixo "callback" a nomes de delegados diferentes daqueles usados como manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="69e16-132">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="69e16-133">❌Não adicione o sufixo "delegate" a um delegado.</span><span class="sxs-lookup"><span data-stu-id="69e16-133">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="69e16-134">✔️ Adicionar o sufixo "EventArgs".</span><span class="sxs-lookup"><span data-stu-id="69e16-134">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="69e16-135">❌Não Derive dessa classe; em vez disso, use a palavra-chave com suporte no seu idioma; por exemplo, em C#, use a `enum` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="69e16-135">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="69e16-136">❌Não adicione o sufixo "enum" ou "Flag".</span><span class="sxs-lookup"><span data-stu-id="69e16-136">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="69e16-137">✔️ Adicionar o sufixo "Exception".</span><span class="sxs-lookup"><span data-stu-id="69e16-137">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="69e16-138">✔️ Adicionar o sufixo "Dictionary".</span><span class="sxs-lookup"><span data-stu-id="69e16-138">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="69e16-139">Observe que `IDictionary` é um tipo específico de coleção, mas essa diretriz tem precedência sobre a diretriz de coleções mais gerais a seguir.</span><span class="sxs-lookup"><span data-stu-id="69e16-139">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="69e16-140">✔️ Adicionar o sufixo "coleção".</span><span class="sxs-lookup"><span data-stu-id="69e16-140">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="69e16-141">✔️ Adicionar o sufixo "Stream".</span><span class="sxs-lookup"><span data-stu-id="69e16-141">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="69e16-142">✔️ Adicionar o sufixo "permissão".</span><span class="sxs-lookup"><span data-stu-id="69e16-142">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="69e16-143">Enumerações de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="69e16-143">Naming Enumerations</span></span>
 <span data-ttu-id="69e16-144">Os nomes dos tipos de enumeração (também chamados de enums) em geral devem seguir as regras de nomenclatura de tipo padrão (PascalCasing, etc.).</span><span class="sxs-lookup"><span data-stu-id="69e16-144">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="69e16-145">No entanto, há diretrizes adicionais que se aplicam especificamente a enums.</span><span class="sxs-lookup"><span data-stu-id="69e16-145">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="69e16-146">✔️ usar um nome de tipo singular para uma enumeração, a menos que seus valores sejam campos de bits.</span><span class="sxs-lookup"><span data-stu-id="69e16-146">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="69e16-147">✔️ usar um nome de tipo plural para uma enumeração com campos de bits como valores, também chamados de sinalizadores Enum.</span><span class="sxs-lookup"><span data-stu-id="69e16-147">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="69e16-148">❌Não use um sufixo "enum" em nomes de tipos de enumeração.</span><span class="sxs-lookup"><span data-stu-id="69e16-148">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="69e16-149">❌Não use os sufixos "Flag" ou "Flags" em nomes de tipo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="69e16-149">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="69e16-150">❌Não use um prefixo em nomes de valores de enumeração (por exemplo, "AD" para enums ADO, "RTF" para enums de Rich Text, etc.).</span><span class="sxs-lookup"><span data-stu-id="69e16-150">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="69e16-151">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="69e16-151">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="69e16-152">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="69e16-152">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="69e16-153">Veja também</span><span class="sxs-lookup"><span data-stu-id="69e16-153">See also</span></span>

- [<span data-ttu-id="69e16-154">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="69e16-154">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="69e16-155">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="69e16-155">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
