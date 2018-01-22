---
title: Diretrizes de design de estrutura
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c48b3cbaae4155a894ba77263505b2ca85238427
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="5319b-102">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="5319b-102">Framework Design Guidelines</span></span>
<span data-ttu-id="5319b-103">Esta seção fornece diretrizes para a criação de bibliotecas que estendem e interagem com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5319b-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="5319b-104">A meta é ajudar os designers de biblioteca a garantir a consistência de API e facilidade de uso, fornecendo um modelo de programação unificado que é independente da linguagem de programação usada para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="5319b-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="5319b-105">É recomendável que você siga estas diretrizes de design ao desenvolver classes e componentes que estendem o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5319b-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="5319b-106">Projeto de biblioteca inconsistente negativamente afeta a produtividade do desenvolvedor e desencoraja adoção.</span><span class="sxs-lookup"><span data-stu-id="5319b-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="5319b-107">As diretrizes são organizadas como recomendações simples prefixadas com os termos de `Do`, `Consider`, `Avoid`, e `Do not`.</span><span class="sxs-lookup"><span data-stu-id="5319b-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="5319b-108">Estas diretrizes destinam-se para ajudar a entender as compensações entre as diferentes soluções de designers de biblioteca de classe.</span><span class="sxs-lookup"><span data-stu-id="5319b-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="5319b-109">Pode haver situações em que o design de boa biblioteca requer que violam essas diretrizes de design.</span><span class="sxs-lookup"><span data-stu-id="5319b-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="5319b-110">Tais casos devem ser raros, e é importante que você tenha um motivo claro e convincente para sua decisão.</span><span class="sxs-lookup"><span data-stu-id="5319b-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="5319b-111">Essas diretrizes foram extraídas do catálogo de *diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição*, Krzysztof Cwalina e Brad Abrams.</span><span class="sxs-lookup"><span data-stu-id="5319b-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5319b-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="5319b-112">In This Section</span></span>  
 [<span data-ttu-id="5319b-113">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="5319b-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="5319b-114">Fornece diretrizes de nomeação de assemblies, namespaces, tipos e membros em bibliotecas de classe.</span><span class="sxs-lookup"><span data-stu-id="5319b-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="5319b-115">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="5319b-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="5319b-116">Fornece diretrizes para usar classes estáticas e abstratos, interfaces, enumerações, estruturas e outros tipos.</span><span class="sxs-lookup"><span data-stu-id="5319b-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="5319b-117">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="5319b-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="5319b-118">Fornece diretrizes para criar e usar propriedades, métodos, construtores, campos, eventos, operadores e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5319b-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="5319b-119">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="5319b-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="5319b-120">Discute os mecanismos de extensibilidade, como subclassificação, usando membros virtuais, eventos e retornos de chamada e explica como escolher os mecanismos que melhor atende aos requisitos do framework.</span><span class="sxs-lookup"><span data-stu-id="5319b-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="5319b-121">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="5319b-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="5319b-122">Descreve as diretrizes de design para criação, gerar e capturar exceções.</span><span class="sxs-lookup"><span data-stu-id="5319b-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="5319b-123">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="5319b-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="5319b-124">Descreve as diretrizes para usar tipos comuns, como matrizes, atributos e coleções, dando suporte a serialização e sobrecarga de operadores de igualdade.</span><span class="sxs-lookup"><span data-stu-id="5319b-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="5319b-125">Padrões comuns de Design</span><span class="sxs-lookup"><span data-stu-id="5319b-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="5319b-126">Fornece diretrizes para escolher e implementar propriedades de dependência e o padrão dispose.</span><span class="sxs-lookup"><span data-stu-id="5319b-126">Provides guidelines for choosing and implementing dependency properties and the dispose pattern.</span></span>  
  
 <span data-ttu-id="5319b-127">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="5319b-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="5319b-128">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="5319b-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5319b-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5319b-129">See Also</span></span>  
 [<span data-ttu-id="5319b-130">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="5319b-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)  
 [<span data-ttu-id="5319b-131">Roteiro para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5319b-131">Roadmap for the .NET Framework</span></span>](http://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
 [<span data-ttu-id="5319b-132">Guia de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="5319b-132">Development Guide</span></span>](../../../docs/framework/development-guide.md)
