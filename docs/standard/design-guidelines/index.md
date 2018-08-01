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
ms.openlocfilehash: 2674acf14aae5e892dfb9707a19cca12b4797c90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572977"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="2b5de-102">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="2b5de-102">Framework Design Guidelines</span></span>
<span data-ttu-id="2b5de-103">Esta seção fornece diretrizes para a criação de bibliotecas que estendem e interagem com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b5de-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="2b5de-104">A meta é ajudar os designers de biblioteca a garantir a consistência de API e facilidade de uso, fornecendo um modelo de programação unificado que é independente da linguagem de programação usada para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="2b5de-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="2b5de-105">É recomendável que você siga estas diretrizes de design ao desenvolver classes e componentes que estendem o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b5de-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="2b5de-106">Projeto de biblioteca inconsistente negativamente afeta a produtividade do desenvolvedor e desencoraja adoção.</span><span class="sxs-lookup"><span data-stu-id="2b5de-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="2b5de-107">As diretrizes são organizadas como recomendações simples prefixadas com os termos de `Do`, `Consider`, `Avoid`, e `Do not`.</span><span class="sxs-lookup"><span data-stu-id="2b5de-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="2b5de-108">Estas diretrizes destinam-se para ajudar a entender as compensações entre as diferentes soluções de designers de biblioteca de classe.</span><span class="sxs-lookup"><span data-stu-id="2b5de-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="2b5de-109">Pode haver situações em que o design de boa biblioteca requer que violam essas diretrizes de design.</span><span class="sxs-lookup"><span data-stu-id="2b5de-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="2b5de-110">Tais casos devem ser raros, e é importante que você tenha um motivo claro e convincente para sua decisão.</span><span class="sxs-lookup"><span data-stu-id="2b5de-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="2b5de-111">Essas diretrizes foram extraídas do catálogo de *diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição*, Krzysztof Cwalina e Brad Abrams.</span><span class="sxs-lookup"><span data-stu-id="2b5de-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2b5de-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="2b5de-112">In This Section</span></span>  
 [<span data-ttu-id="2b5de-113">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="2b5de-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="2b5de-114">Fornece diretrizes de nomeação de assemblies, namespaces, tipos e membros em bibliotecas de classe.</span><span class="sxs-lookup"><span data-stu-id="2b5de-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="2b5de-115">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="2b5de-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="2b5de-116">Fornece diretrizes para usar classes estáticas e abstratos, interfaces, enumerações, estruturas e outros tipos.</span><span class="sxs-lookup"><span data-stu-id="2b5de-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="2b5de-117">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="2b5de-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="2b5de-118">Fornece diretrizes para criar e usar propriedades, métodos, construtores, campos, eventos, operadores e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2b5de-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="2b5de-119">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="2b5de-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="2b5de-120">Discute os mecanismos de extensibilidade, como subclassificação, usando membros virtuais, eventos e retornos de chamada e explica como escolher os mecanismos que melhor atende aos requisitos do framework.</span><span class="sxs-lookup"><span data-stu-id="2b5de-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="2b5de-121">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="2b5de-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="2b5de-122">Descreve as diretrizes de design para criação, gerar e capturar exceções.</span><span class="sxs-lookup"><span data-stu-id="2b5de-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="2b5de-123">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="2b5de-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="2b5de-124">Descreve as diretrizes para usar tipos comuns, como matrizes, atributos e coleções, dando suporte a serialização e sobrecarga de operadores de igualdade.</span><span class="sxs-lookup"><span data-stu-id="2b5de-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="2b5de-125">Padrões comuns de Design</span><span class="sxs-lookup"><span data-stu-id="2b5de-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="2b5de-126">Fornece diretrizes para escolher e implementar propriedades de dependência e o padrão dispose.</span><span class="sxs-lookup"><span data-stu-id="2b5de-126">Provides guidelines for choosing and implementing dependency properties and the dispose pattern.</span></span>  
  
 <span data-ttu-id="2b5de-127">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="2b5de-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2b5de-128">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="2b5de-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b5de-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b5de-129">See Also</span></span>  
 [<span data-ttu-id="2b5de-130">Visão geral</span><span class="sxs-lookup"><span data-stu-id="2b5de-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)  
 [<span data-ttu-id="2b5de-131">Roteiro para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2b5de-131">Roadmap for the .NET Framework</span></span>](https://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
 [<span data-ttu-id="2b5de-132">Guia de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="2b5de-132">Development Guide</span></span>](../../../docs/framework/development-guide.md)
