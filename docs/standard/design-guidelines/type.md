---
title: Diretrizes de Design de tipo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6b02abef0180b6de82e26837863849cce35c994f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="type-design-guidelines"></a><span data-ttu-id="78e15-102">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="78e15-102">Type Design Guidelines</span></span>
<span data-ttu-id="78e15-103">Da perspectiva do CLR, há apenas duas categorias de tipos — referenciar tipos e tipos de valor —, mas com a finalidade de uma discussão sobre o design de estrutura, dividimos tipos em grupos mais lógicos, cada um com suas próprias regras de design específico.</span><span class="sxs-lookup"><span data-stu-id="78e15-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="78e15-104">As classes são o caso geral de tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="78e15-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="78e15-105">Eles formam a maior parte dos tipos na maioria das estruturas.</span><span class="sxs-lookup"><span data-stu-id="78e15-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="78e15-106">Classes devem sua popularidade, para o sofisticado conjunto de recursos orientados a objeto que oferecem suporte e sua aplicabilidade geral.</span><span class="sxs-lookup"><span data-stu-id="78e15-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="78e15-107">Classes base e classes abstratas são grupos lógicos especiais relacionados à extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="78e15-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="78e15-108">Interfaces são tipos que podem ser implementados por tipos de referência e tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="78e15-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="78e15-109">Portanto, elas podem servir como raízes de polimórficas hierarquias de tipos de referência e tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="78e15-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="78e15-110">Além disso, as interfaces podem ser usadas para simular a herança múltipla, que não tem suporte nativo pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="78e15-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="78e15-111">Estruturas são o caso geral de tipos de valor e devem ser reservadas para tipos de pequenos e simples, semelhantes a primitivos de linguagem.</span><span class="sxs-lookup"><span data-stu-id="78e15-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="78e15-112">Enumerações são um caso especial de tipos de valor usado para definir conjuntos de curtos de valores, como dias da semana, cores de console e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="78e15-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="78e15-113">Classes static são tipos devem ser contêineres para membros estáticos.</span><span class="sxs-lookup"><span data-stu-id="78e15-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="78e15-114">Eles são usados para fornecer atalhos para outras operações.</span><span class="sxs-lookup"><span data-stu-id="78e15-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="78e15-115">Delegados, exceções, atributos, matrizes e coleções são todos os casos especiais de tipos de referência que se destina para usos específicos e diretrizes de design e uso são discutidas em outro lugar neste livro.</span><span class="sxs-lookup"><span data-stu-id="78e15-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="78e15-116">**FAZER ✓** Certifique-se de que cada tipo é um conjunto bem definido de membros relacionados, não apenas um conjunto aleatório de funcionalidades relacionadas.</span><span class="sxs-lookup"><span data-stu-id="78e15-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78e15-117">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="78e15-117">In This Section</span></span>  
 [<span data-ttu-id="78e15-118">Escolhendo entre a classe e Struct</span><span class="sxs-lookup"><span data-stu-id="78e15-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="78e15-119">Design de classe abstrata</span><span class="sxs-lookup"><span data-stu-id="78e15-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="78e15-120">Design de classe estática</span><span class="sxs-lookup"><span data-stu-id="78e15-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="78e15-121">Design de interface</span><span class="sxs-lookup"><span data-stu-id="78e15-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="78e15-122">Design de Struct</span><span class="sxs-lookup"><span data-stu-id="78e15-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="78e15-123">Design de enumeração</span><span class="sxs-lookup"><span data-stu-id="78e15-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="78e15-124">Tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="78e15-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="78e15-125">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="78e15-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="78e15-126">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="78e15-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e15-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78e15-127">See Also</span></span>  
 [<span data-ttu-id="78e15-128">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="78e15-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
