---
title: Diretrizes de design de estrutura
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 623391de63891c1695a63482a424bb76a861deba
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709303"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="f7f55-102">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="f7f55-102">Framework Design Guidelines</span></span>
<span data-ttu-id="f7f55-103">Esta seção fornece diretrizes para a criação de bibliotecas que estendem e interagem com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f7f55-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="f7f55-104">O objetivo é ajudar os designers de biblioteca a garantir a consistência da API e a facilidade de uso, fornecendo um modelo de programação unificado que é independente da linguagem de programação usada para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="f7f55-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="f7f55-105">Recomendamos que você siga essas diretrizes de design ao desenvolver classes e componentes que estendam o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f7f55-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="f7f55-106">O design de biblioteca inconsistente afeta negativamente a produtividade do desenvolvedor e não incentiva a adoção.</span><span class="sxs-lookup"><span data-stu-id="f7f55-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="f7f55-107">As diretrizes são organizadas como recomendações simples prefixadas com os termos `Do`, `Consider`, `Avoid`e `Do not`.</span><span class="sxs-lookup"><span data-stu-id="f7f55-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="f7f55-108">Essas diretrizes destinam-se a ajudar os designers de biblioteca de classes a entender as compensações entre diferentes soluções.</span><span class="sxs-lookup"><span data-stu-id="f7f55-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="f7f55-109">Pode haver situações em que um bom design de biblioteca exija que você viole essas diretrizes de design.</span><span class="sxs-lookup"><span data-stu-id="f7f55-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="f7f55-110">Esses casos devem ser raros, e é importante que você tenha um motivo claro e convincente para sua decisão.</span><span class="sxs-lookup"><span data-stu-id="f7f55-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="f7f55-111">Essas diretrizes são extraídas das diretrizes de *design da estrutura de livros: convenções, idiomas e padrões para bibliotecas .net reutilizáveis, 2ª edição*, por Krzysztof Cwalina e Brad Abrams.</span><span class="sxs-lookup"><span data-stu-id="f7f55-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7f55-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f7f55-112">In This Section</span></span>  
 [<span data-ttu-id="f7f55-113">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="f7f55-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="f7f55-114">Fornece diretrizes para nomear assemblies, namespaces, tipos e membros em bibliotecas de classes.</span><span class="sxs-lookup"><span data-stu-id="f7f55-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="f7f55-115">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="f7f55-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="f7f55-116">Fornece diretrizes para usar classes estáticas e abstratas, interfaces, enumerações, estruturas e outros tipos.</span><span class="sxs-lookup"><span data-stu-id="f7f55-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="f7f55-117">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="f7f55-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="f7f55-118">Fornece diretrizes para criar e usar propriedades, métodos, construtores, campos, eventos, operadores e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f7f55-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="f7f55-119">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="f7f55-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="f7f55-120">Discute mecanismos de extensibilidade, como subclasses, uso de eventos, membros virtuais e retornos de chamada, e explica como escolher os mecanismos que melhor atendem aos requisitos da estrutura.</span><span class="sxs-lookup"><span data-stu-id="f7f55-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="f7f55-121">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="f7f55-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="f7f55-122">Descreve as diretrizes de design para criar, lançar e capturar exceções.</span><span class="sxs-lookup"><span data-stu-id="f7f55-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="f7f55-123">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="f7f55-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="f7f55-124">Descreve as diretrizes para o uso de tipos comuns, como matrizes, atributos e coleções, suporte à serialização e sobrecarga de operadores de igualdade.</span><span class="sxs-lookup"><span data-stu-id="f7f55-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="f7f55-125">Padrões comuns de Design</span><span class="sxs-lookup"><span data-stu-id="f7f55-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="f7f55-126">Fornece diretrizes para escolher e implementar propriedades de dependência.</span><span class="sxs-lookup"><span data-stu-id="f7f55-126">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="f7f55-127">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="f7f55-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f7f55-128">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="f7f55-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7f55-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="f7f55-129">See also</span></span>

- [<span data-ttu-id="f7f55-130">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="f7f55-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)
- [<span data-ttu-id="f7f55-131">Guia de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="f7f55-131">Development Guide</span></span>](../../../docs/framework/development-guide.md)
