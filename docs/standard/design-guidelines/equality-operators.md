---
title: Operadores de igualdade
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 34fc8eef5270369419b76899f0dbe1ace106caf6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741699"
---
# <a name="equality-operators"></a><span data-ttu-id="2ac8d-102">Operadores de igualdade</span><span class="sxs-lookup"><span data-stu-id="2ac8d-102">Equality Operators</span></span>
<span data-ttu-id="2ac8d-103">Esta seção discute como sobrecarregar operadores de igualdade e refere-se a `operator==` e `operator!=` como operadores de igualdade.</span><span class="sxs-lookup"><span data-stu-id="2ac8d-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>

 <span data-ttu-id="2ac8d-104">❌ não sobrecarregar um dos operadores de igualdade e não o outro.</span><span class="sxs-lookup"><span data-stu-id="2ac8d-104">❌ DO NOT overload one of the equality operators and not the other.</span></span>

 <span data-ttu-id="2ac8d-105">✔️ garantir que <xref:System.Object.Equals%2A?displayProperty=nameWithType> e os operadores de igualdade tenham exatamente a mesma semântica e características de desempenho semelhantes.</span><span class="sxs-lookup"><span data-stu-id="2ac8d-105">✔️ DO ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>

 <span data-ttu-id="2ac8d-106">Isso geralmente significa que `Object.Equals` precisa ser substituído quando os operadores de igualdade estão sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="2ac8d-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>

 <span data-ttu-id="2ac8d-107">❌ evitar lançar exceções de operadores de igualdade.</span><span class="sxs-lookup"><span data-stu-id="2ac8d-107">❌ AVOID throwing exceptions from equality operators.</span></span>

 <span data-ttu-id="2ac8d-108">Por exemplo, retorne FALSE se um dos argumentos for nulo em vez de lançar `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="2ac8d-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>

## <a name="equality-operators-on-value-types"></a><span data-ttu-id="2ac8d-109">Operadores de igualdade em tipos de valor</span><span class="sxs-lookup"><span data-stu-id="2ac8d-109">Equality Operators on Value Types</span></span>
 <span data-ttu-id="2ac8d-110">✔️ sobrecarregar os operadores de igualdade em tipos de valor, se a igualdade for significativa.</span><span class="sxs-lookup"><span data-stu-id="2ac8d-110">✔️ DO overload the equality operators on value types, if equality is meaningful.</span></span>

 <span data-ttu-id="2ac8d-111">Na maioria das linguagens de programação, não há implementação padrão de `operator==` para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="2ac8d-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>

## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="2ac8d-112">Operadores de igualdade em tipos de referência</span><span class="sxs-lookup"><span data-stu-id="2ac8d-112">Equality Operators on Reference Types</span></span>
 <span data-ttu-id="2ac8d-113">❌ evitar sobrecarregar operadores de igualdade em tipos de referência mutáveis.</span><span class="sxs-lookup"><span data-stu-id="2ac8d-113">❌ AVOID overloading equality operators on mutable reference types.</span></span>

 <span data-ttu-id="2ac8d-114">Muitas linguagens têm operadores de igualdade internos para tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="2ac8d-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="2ac8d-115">Os operadores internos geralmente implementam a igualdade de referência e muitos desenvolvedores ficam surpresos quando o comportamento padrão é alterado para a igualdade do valor.</span><span class="sxs-lookup"><span data-stu-id="2ac8d-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>

 <span data-ttu-id="2ac8d-116">Esse problema é mitigado para tipos de referência imutáveis porque a imutabilidade torna muito mais difícil observar a diferença entre igualdade de referência e igualdade de valor.</span><span class="sxs-lookup"><span data-stu-id="2ac8d-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>

 <span data-ttu-id="2ac8d-117">❌ evitar sobrecarregar operadores de igualdade em tipos de referência se a implementação for significativamente mais lenta do que a de igualdade de referência.</span><span class="sxs-lookup"><span data-stu-id="2ac8d-117">❌ AVOID overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>

 <span data-ttu-id="2ac8d-118">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="2ac8d-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="2ac8d-119">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="2ac8d-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="2ac8d-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="2ac8d-120">See also</span></span>

- [<span data-ttu-id="2ac8d-121">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="2ac8d-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="2ac8d-122">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="2ac8d-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
