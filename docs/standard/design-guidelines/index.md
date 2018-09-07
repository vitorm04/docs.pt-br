---
title: Diretrizes de design de estrutura
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df2ccf3d778e26e16937554304ae847f624cfec0
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085628"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="db682-102">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="db682-102">Framework Design Guidelines</span></span>
<span data-ttu-id="db682-103">Esta seção fornece diretrizes para a criação de bibliotecas que estendem e interagem com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db682-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="db682-104">O objetivo é ajudar os designers de bibliotecas a garantir a consistência de API e facilidade de uso, fornecendo um modelo de programação unificado que é independente da linguagem de programação usada para o desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="db682-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="db682-105">É recomendável que você siga estas diretrizes de design ao desenvolver classes e componentes que estendam o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db682-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="db682-106">Design de bibliotecas inconsistente negativamente afeta a produtividade do desenvolvedor e desencoraja a adoção.</span><span class="sxs-lookup"><span data-stu-id="db682-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="db682-107">As diretrizes são organizadas como recomendações simples prefixadas com os termos `Do`, `Consider`, `Avoid`, e `Do not`.</span><span class="sxs-lookup"><span data-stu-id="db682-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="db682-108">Estas diretrizes destinam-se a ajudar os designers de biblioteca de classes a entender as compensações entre as diferentes soluções.</span><span class="sxs-lookup"><span data-stu-id="db682-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="db682-109">Pode haver situações em que o design de boa biblioteca requer que você viole essas diretrizes de design.</span><span class="sxs-lookup"><span data-stu-id="db682-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="db682-110">Nesses casos, devem ser raros, e é importante que você tenha um motivo claro e convincente para sua decisão.</span><span class="sxs-lookup"><span data-stu-id="db682-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="db682-111">Estas diretrizes foram extraídas do livro *diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition*, por Krzysztof Cwalina e Brad Abrams.</span><span class="sxs-lookup"><span data-stu-id="db682-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db682-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="db682-112">In This Section</span></span>  
 [<span data-ttu-id="db682-113">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="db682-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="db682-114">Fornece diretrizes para a nomeação de assemblies, namespaces, tipos e membros em bibliotecas de classes.</span><span class="sxs-lookup"><span data-stu-id="db682-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="db682-115">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="db682-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="db682-116">Fornece diretrizes para usar classes abstratas e estáticas, interfaces, enumerações, estruturas e outros tipos.</span><span class="sxs-lookup"><span data-stu-id="db682-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="db682-117">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="db682-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="db682-118">Fornece diretrizes para criação e uso de propriedades, métodos, construtores, campos, eventos, operadores e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="db682-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="db682-119">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="db682-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="db682-120">Discute os mecanismos de extensibilidade, como a criação de subclasses, usando eventos, os membros virtuais e retornos de chamada e explica como escolher os mecanismos que melhor atendem aos requisitos da sua estrutura.</span><span class="sxs-lookup"><span data-stu-id="db682-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="db682-121">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="db682-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="db682-122">Descreve as diretrizes de design para projetar, lançar e capturar exceções.</span><span class="sxs-lookup"><span data-stu-id="db682-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="db682-123">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="db682-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="db682-124">Descreve diretrizes para usando tipos comuns, como matrizes, atributos e coleções, suporte à serialização e sobrecarga de operadores de igualdade.</span><span class="sxs-lookup"><span data-stu-id="db682-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="db682-125">Padrões comuns de Design</span><span class="sxs-lookup"><span data-stu-id="db682-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="db682-126">Fornece diretrizes para escolher e implementar as propriedades de dependência e o padrão de descarte.</span><span class="sxs-lookup"><span data-stu-id="db682-126">Provides guidelines for choosing and implementing dependency properties and the dispose pattern.</span></span>  
  
 <span data-ttu-id="db682-127">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="db682-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="db682-128">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="db682-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db682-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db682-129">See also</span></span>

- [<span data-ttu-id="db682-130">Visão geral</span><span class="sxs-lookup"><span data-stu-id="db682-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)  
- [<span data-ttu-id="db682-131">Roteiro para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="db682-131">Roadmap for the .NET Framework</span></span>](https://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
- [<span data-ttu-id="db682-132">Guia de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="db682-132">Development Guide</span></span>](../../../docs/framework/development-guide.md)
