---
title: Diretrizes de design de estrutura
description: Consulte Diretrizes de design de estrutura para criar bibliotecas que estendem e interajam com o .NET, para garantir a consistência da API e a facilidade de uso.
titleSuffix: ''
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 17998adb1d18579f6763a80a82944e742e284e4e
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769061"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="3a667-103">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="3a667-103">Framework Design Guidelines</span></span>
<span data-ttu-id="3a667-104">Esta seção fornece diretrizes para a criação de bibliotecas que estendem e interagem com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3a667-104">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="3a667-105">O objetivo é ajudar os designers de biblioteca a garantir a consistência da API e a facilidade de uso, fornecendo um modelo de programação unificado que é independente da linguagem de programação usada para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3a667-105">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="3a667-106">Recomendamos que você siga essas diretrizes de design ao desenvolver classes e componentes que estendam o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3a667-106">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="3a667-107">O design de biblioteca inconsistente afeta negativamente a produtividade do desenvolvedor e não incentiva a adoção.</span><span class="sxs-lookup"><span data-stu-id="3a667-107">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="3a667-108">As diretrizes são organizadas como recomendações simples prefixadas com os termos `Do` , `Consider` , `Avoid` e `Do not` .</span><span class="sxs-lookup"><span data-stu-id="3a667-108">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="3a667-109">Essas diretrizes destinam-se a ajudar os designers de biblioteca de classes a entender as compensações entre diferentes soluções.</span><span class="sxs-lookup"><span data-stu-id="3a667-109">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="3a667-110">Pode haver situações em que um bom design de biblioteca exija que você viole essas diretrizes de design.</span><span class="sxs-lookup"><span data-stu-id="3a667-110">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="3a667-111">Esses casos devem ser raros, e é importante que você tenha um motivo claro e convincente para sua decisão.</span><span class="sxs-lookup"><span data-stu-id="3a667-111">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="3a667-112">Essas diretrizes são extraídas das diretrizes de *design da estrutura de livros: convenções, idiomas e padrões para bibliotecas .net reutilizáveis, 2ª edição*, por Krzysztof Cwalina e Brad Abrams.</span><span class="sxs-lookup"><span data-stu-id="3a667-112">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3a667-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3a667-113">In This Section</span></span>  
 [<span data-ttu-id="3a667-114">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="3a667-114">Naming Guidelines</span></span>](naming-guidelines.md)  
 <span data-ttu-id="3a667-115">Fornece diretrizes para nomear assemblies, namespaces, tipos e membros em bibliotecas de classes.</span><span class="sxs-lookup"><span data-stu-id="3a667-115">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="3a667-116">Diretrizes de design de tipo</span><span class="sxs-lookup"><span data-stu-id="3a667-116">Type Design Guidelines</span></span>](type.md)  
 <span data-ttu-id="3a667-117">Fornece diretrizes para usar classes estáticas e abstratas, interfaces, enumerações, estruturas e outros tipos.</span><span class="sxs-lookup"><span data-stu-id="3a667-117">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="3a667-118">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="3a667-118">Member Design Guidelines</span></span>](member.md)  
 <span data-ttu-id="3a667-119">Fornece diretrizes para criar e usar propriedades, métodos, construtores, campos, eventos, operadores e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3a667-119">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="3a667-120">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="3a667-120">Designing for Extensibility</span></span>](designing-for-extensibility.md)  
 <span data-ttu-id="3a667-121">Discute mecanismos de extensibilidade, como subclasses, uso de eventos, membros virtuais e retornos de chamada, e explica como escolher os mecanismos que melhor atendem aos requisitos da estrutura.</span><span class="sxs-lookup"><span data-stu-id="3a667-121">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="3a667-122">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="3a667-122">Design Guidelines for Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="3a667-123">Descreve as diretrizes de design para criar, lançar e capturar exceções.</span><span class="sxs-lookup"><span data-stu-id="3a667-123">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="3a667-124">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="3a667-124">Usage Guidelines</span></span>](usage-guidelines.md)  
 <span data-ttu-id="3a667-125">Descreve as diretrizes para o uso de tipos comuns, como matrizes, atributos e coleções, suporte à serialização e sobrecarga de operadores de igualdade.</span><span class="sxs-lookup"><span data-stu-id="3a667-125">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="3a667-126">Padrões de design comuns</span><span class="sxs-lookup"><span data-stu-id="3a667-126">Common Design Patterns</span></span>](common-design-patterns.md)  
 <span data-ttu-id="3a667-127">Fornece diretrizes para escolher e implementar propriedades de dependência.</span><span class="sxs-lookup"><span data-stu-id="3a667-127">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="3a667-128">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="3a667-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="3a667-129">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="3a667-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a667-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="3a667-130">See also</span></span>

- [<span data-ttu-id="3a667-131">Visão geral</span><span class="sxs-lookup"><span data-stu-id="3a667-131">Overview</span></span>](../../framework/get-started/overview.md)
- [<span data-ttu-id="3a667-132">Guia de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="3a667-132">Development Guide</span></span>](../../framework/development-guide.md)
