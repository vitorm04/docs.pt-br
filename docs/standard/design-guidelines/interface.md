---
title: Design de interface
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dc7185f9541952d528de38b627052239f5d8b4ae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="interface-design"></a><span data-ttu-id="3d4e4-102">Design de interface</span><span class="sxs-lookup"><span data-stu-id="3d4e4-102">Interface Design</span></span>
<span data-ttu-id="3d4e4-103">Embora a maioria das APIs melhor são modelados usando classes e estruturas, há casos em que as interfaces são mais apropriados ou são a única opção.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>  
  
 <span data-ttu-id="3d4e4-104">O CLR não suporta herança múltipla (ou seja, classes CLR não podem herdar de mais de uma classe base), mas permite tipos implementar uma ou mais interfaces além de herdar de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="3d4e4-105">Portanto, as interfaces geralmente são usadas para obter o efeito de várias heranças.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="3d4e4-106">Por exemplo, <xref:System.IDisposable> é uma interface que permite tipos dar suporte a disposability independente de qualquer outra hierarquia de herança no qual deseja participar.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>  
  
 <span data-ttu-id="3d4e4-107">A outra situação em que define uma interface é apropriada está na criação de uma interface comum que pode ser compatível com vários tipos, incluindo alguns tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="3d4e4-108">Tipos de valor não podem herdar de tipos diferentes de <xref:System.ValueType>, mas elas podem implementar interfaces, portanto, usar uma interface é a única opção para fornecer um tipo de base comum.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>  
  
 <span data-ttu-id="3d4e4-109">**FAZER ✓** definir uma interface, se você precisar de algum API comuns para serem suportados por um conjunto de tipos que inclui os tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-109">**✓ DO** define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>  
  
 <span data-ttu-id="3d4e4-110">**✓ CONSIDERE** define uma interface, se você precisar oferecer suporte a sua funcionalidade em tipos que herdam já algum outro tipo.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-110">**✓ CONSIDER** defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>  
  
 <span data-ttu-id="3d4e4-111">**X Evite** usando as interfaces do marcador (interfaces com nenhum membro).</span><span class="sxs-lookup"><span data-stu-id="3d4e4-111">**X AVOID** using marker interfaces (interfaces with no members).</span></span>  
  
 <span data-ttu-id="3d4e4-112">Se você precisa marcar uma classe como tendo uma característica específica (marcador), em geral, use um atributo personalizado em vez de uma interface.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>  
  
 <span data-ttu-id="3d4e4-113">**FAZER ✓** fornecer pelo menos um tipo que é uma implementação de uma interface.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-113">**✓ DO** provide at least one type that is an implementation of an interface.</span></span>  
  
 <span data-ttu-id="3d4e4-114">Fazer isso ajuda a validar o design da interface.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="3d4e4-115">Por exemplo, <xref:System.Collections.Generic.List%601> é uma implementação do <xref:System.Collections.Generic.IList%601> interface.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>  
  
 <span data-ttu-id="3d4e4-116">**FAZER ✓** fornecer pelo menos uma API que consome cada interface que você definir (um método de interface como um parâmetro ou uma propriedade digitada como a interface).</span><span class="sxs-lookup"><span data-stu-id="3d4e4-116">**✓ DO** provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>  
  
 <span data-ttu-id="3d4e4-117">Fazer isso ajuda a validar o design de interface.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="3d4e4-118">Por exemplo, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consome o <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>  
  
 <span data-ttu-id="3d4e4-119">**X não** adicionar membros a uma interface que tiver enviado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-119">**X DO NOT** add members to an interface that has previously shipped.</span></span>  
  
 <span data-ttu-id="3d4e4-120">Isso interrompe implementações da interface.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="3d4e4-121">Você deve criar uma nova interface para evitar problemas de controle de versão.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-121">You should create a new interface in order to avoid versioning problems.</span></span>  
  
 <span data-ttu-id="3d4e4-122">Exceto situações descritas nessas diretrizes, você deve, em geral, escolher classes em vez de interfaces na criação de bibliotecas reutilizáveis de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3d4e4-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>  
  
 <span data-ttu-id="3d4e4-123">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="3d4e4-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="3d4e4-124">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="3d4e4-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d4e4-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d4e4-125">See Also</span></span>  
 [<span data-ttu-id="3d4e4-126">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="3d4e4-126">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="3d4e4-127">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="3d4e4-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
