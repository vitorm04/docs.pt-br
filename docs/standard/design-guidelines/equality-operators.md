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
author: KrzysztofCwalina
ms.openlocfilehash: ef1a0aff1ac59434d9d9a6f0371bf236f637050e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960324"
---
# <a name="equality-operators"></a><span data-ttu-id="cb34c-102">Operadores de igualdade</span><span class="sxs-lookup"><span data-stu-id="cb34c-102">Equality Operators</span></span>
<span data-ttu-id="cb34c-103">Esta seção discute a sobrecarga de operadores de igualdade e refere-se ao `operator==` e `operator!=` como operadores de igualdade.</span><span class="sxs-lookup"><span data-stu-id="cb34c-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>  
  
 <span data-ttu-id="cb34c-104">**X DO NOT** sobrecarregar os operadores de igualdade e não o outro.</span><span class="sxs-lookup"><span data-stu-id="cb34c-104">**X DO NOT** overload one of the equality operators and not the other.</span></span>  
  
 <span data-ttu-id="cb34c-105">**✓ DO** Certifique-se de que <xref:System.Object.Equals%2A?displayProperty=nameWithType> e os operadores de igualdade têm exatamente a mesma semântica e as características de desempenho semelhante.</span><span class="sxs-lookup"><span data-stu-id="cb34c-105">**✓ DO** ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>  
  
 <span data-ttu-id="cb34c-106">Isso significa que muitas vezes `Object.Equals` precisa ser substituído quando os operadores de igualdade são sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="cb34c-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>  
  
 <span data-ttu-id="cb34c-107">**X AVOID** Lançando exceções de operadores de igualdade.</span><span class="sxs-lookup"><span data-stu-id="cb34c-107">**X AVOID** throwing exceptions from equality operators.</span></span>  
  
 <span data-ttu-id="cb34c-108">Por exemplo, retornar false se um dos argumentos for nulo em vez de gerar `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="cb34c-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>  
  
## <a name="equality-operators-on-value-types"></a><span data-ttu-id="cb34c-109">Operadores de igualdade em tipos de valor</span><span class="sxs-lookup"><span data-stu-id="cb34c-109">Equality Operators on Value Types</span></span>  
 <span data-ttu-id="cb34c-110">**✓ DO** sobrecarregar os operadores de igualdade em tipos de valor, se a igualdade é significativa.</span><span class="sxs-lookup"><span data-stu-id="cb34c-110">**✓ DO** overload the equality operators on value types, if equality is meaningful.</span></span>  
  
 <span data-ttu-id="cb34c-111">Na maioria das linguagens de programação, não há nenhuma implementação padrão de `operator==` para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="cb34c-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>  
  
## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="cb34c-112">Operadores de igualdade em tipos de referência</span><span class="sxs-lookup"><span data-stu-id="cb34c-112">Equality Operators on Reference Types</span></span>  
 <span data-ttu-id="cb34c-113">**X AVOID** sobrecarregar os operadores de igualdade em tipos de referência mutável.</span><span class="sxs-lookup"><span data-stu-id="cb34c-113">**X AVOID** overloading equality operators on mutable reference types.</span></span>  
  
 <span data-ttu-id="cb34c-114">Muitos idiomas têm operadores de igualdade interna para tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="cb34c-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="cb34c-115">Os operadores internos geralmente implementam a igualdade de referência, e muitos desenvolvedores estão surpresos quando o comportamento padrão é alterado para a igualdade de valor.</span><span class="sxs-lookup"><span data-stu-id="cb34c-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>  
  
 <span data-ttu-id="cb34c-116">Esse problema é reduzido para tipos de referência imutável porque imutabilidade torna muito difícil observar a diferença entre a igualdade de referência e de igualdade de valor.</span><span class="sxs-lookup"><span data-stu-id="cb34c-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>  
  
 <span data-ttu-id="cb34c-117">**X AVOID** sobrecarregar os operadores de igualdade em tipos de referência, se a implementação seria significativamente mais lenta do que o de igualdade de referência.</span><span class="sxs-lookup"><span data-stu-id="cb34c-117">**X AVOID** overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>  
  
 <span data-ttu-id="cb34c-118">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="cb34c-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="cb34c-119">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="cb34c-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb34c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb34c-120">See also</span></span>

- [<span data-ttu-id="cb34c-121">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="cb34c-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="cb34c-122">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="cb34c-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
