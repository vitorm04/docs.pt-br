---
title: Operadores de igualdade
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cd740e9b7a5d38229b3564bfeca003fc4d189624
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="equality-operators"></a><span data-ttu-id="18952-102">Operadores de igualdade</span><span class="sxs-lookup"><span data-stu-id="18952-102">Equality Operators</span></span>
<span data-ttu-id="18952-103">Esta seção discute a sobrecarga de operadores de igualdade e refere-se ao `operator==` e `operator!=` como operadores de igualdade.</span><span class="sxs-lookup"><span data-stu-id="18952-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>  
  
 <span data-ttu-id="18952-104">**X não** sobrecarregar os operadores de igualdade e não o outro.</span><span class="sxs-lookup"><span data-stu-id="18952-104">**X DO NOT** overload one of the equality operators and not the other.</span></span>  
  
 <span data-ttu-id="18952-105">**FAZER ✓** Certifique-se de que <xref:System.Object.Equals%2A?displayProperty=nameWithType> e os operadores de igualdade têm exatamente a mesma semântica e as características de desempenho semelhante.</span><span class="sxs-lookup"><span data-stu-id="18952-105">**✓ DO** ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>  
  
 <span data-ttu-id="18952-106">Isso geralmente significa que `Object.Equals` precisa ser substituído quando os operadores de igualdade estão sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="18952-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>  
  
 <span data-ttu-id="18952-107">**X Evite** Lançando exceções de operadores de igualdade.</span><span class="sxs-lookup"><span data-stu-id="18952-107">**X AVOID** throwing exceptions from equality operators.</span></span>  
  
 <span data-ttu-id="18952-108">Por exemplo, retornará false se um dos argumentos for nulo, em vez de gerar `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="18952-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>  
  
## <a name="equality-operators-on-value-types"></a><span data-ttu-id="18952-109">Operadores de igualdade em tipos de valor</span><span class="sxs-lookup"><span data-stu-id="18952-109">Equality Operators on Value Types</span></span>  
 <span data-ttu-id="18952-110">**FAZER ✓** sobrecarregar os operadores de igualdade em tipos de valor, se a igualdade é significativa.</span><span class="sxs-lookup"><span data-stu-id="18952-110">**✓ DO** overload the equality operators on value types, if equality is meaningful.</span></span>  
  
 <span data-ttu-id="18952-111">Na maioria das linguagens de programação, não há nenhuma implementação padrão de `operator==` para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="18952-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>  
  
## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="18952-112">Operadores de igualdade em tipos de referência</span><span class="sxs-lookup"><span data-stu-id="18952-112">Equality Operators on Reference Types</span></span>  
 <span data-ttu-id="18952-113">**X Evite** sobrecarregar os operadores de igualdade em tipos de referência mutável.</span><span class="sxs-lookup"><span data-stu-id="18952-113">**X AVOID** overloading equality operators on mutable reference types.</span></span>  
  
 <span data-ttu-id="18952-114">Muitos idiomas tem operadores de igualdade internos para tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="18952-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="18952-115">Os operadores internos geralmente implementam a igualdade de referência e muitos desenvolvedores estão surpresos quando o comportamento padrão é alterado para a igualdade de valor.</span><span class="sxs-lookup"><span data-stu-id="18952-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>  
  
 <span data-ttu-id="18952-116">Esse problema é reduzido para tipos de referência imutável porque imutabilidade torna muito mais difícil observar a diferença entre a igualdade de referência e de igualdade de valor.</span><span class="sxs-lookup"><span data-stu-id="18952-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>  
  
 <span data-ttu-id="18952-117">**X Evite** sobrecarregar os operadores de igualdade em tipos de referência, se a implementação seria significativamente mais lenta do que o de igualdade de referência.</span><span class="sxs-lookup"><span data-stu-id="18952-117">**X AVOID** overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>  
  
 <span data-ttu-id="18952-118">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="18952-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="18952-119">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="18952-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18952-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18952-120">See Also</span></span>  
 [<span data-ttu-id="18952-121">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="18952-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="18952-122">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="18952-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
