---
title: Diretrizes de Design de tipo
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af7511f4159fdbfe2d3f972dc927e9ee11fd586f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="type-design-guidelines"></a><span data-ttu-id="77f94-102">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="77f94-102">Type Design Guidelines</span></span>
<span data-ttu-id="77f94-103">Da perspectiva do CLR, há apenas duas categorias de tipos — referenciar tipos e tipos de valor —, mas com a finalidade de uma discussão sobre o design de estrutura, dividimos tipos em grupos mais lógicos, cada um com suas próprias regras de design específico.</span><span class="sxs-lookup"><span data-stu-id="77f94-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="77f94-104">As classes são o caso geral de tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="77f94-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="77f94-105">Eles formam a maior parte dos tipos na maioria das estruturas.</span><span class="sxs-lookup"><span data-stu-id="77f94-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="77f94-106">Classes devem sua popularidade, para o sofisticado conjunto de recursos orientados a objeto que oferecem suporte e sua aplicabilidade geral.</span><span class="sxs-lookup"><span data-stu-id="77f94-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="77f94-107">Classes base e classes abstratas são grupos lógicos especiais relacionados à extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="77f94-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="77f94-108">Interfaces são tipos que podem ser implementados por tipos de referência e tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="77f94-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="77f94-109">Portanto, elas podem servir como raízes de polimórficas hierarquias de tipos de referência e tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="77f94-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="77f94-110">Além disso, as interfaces podem ser usadas para simular a herança múltipla, que não tem suporte nativo pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="77f94-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="77f94-111">Estruturas são o caso geral de tipos de valor e devem ser reservadas para tipos de pequenos e simples, semelhantes a primitivos de linguagem.</span><span class="sxs-lookup"><span data-stu-id="77f94-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="77f94-112">Enumerações são um caso especial de tipos de valor usado para definir conjuntos de curtos de valores, como dias da semana, cores de console e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="77f94-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="77f94-113">Classes static são tipos devem ser contêineres para membros estáticos.</span><span class="sxs-lookup"><span data-stu-id="77f94-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="77f94-114">Eles são usados para fornecer atalhos para outras operações.</span><span class="sxs-lookup"><span data-stu-id="77f94-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="77f94-115">Delegados, exceções, atributos, matrizes e coleções são todos os casos especiais de tipos de referência que se destina para usos específicos e diretrizes de design e uso são discutidas em outro lugar neste livro.</span><span class="sxs-lookup"><span data-stu-id="77f94-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="77f94-116">**FAZER ✓** Certifique-se de que cada tipo é um conjunto bem definido de membros relacionados, não apenas um conjunto aleatório de funcionalidades relacionadas.</span><span class="sxs-lookup"><span data-stu-id="77f94-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="77f94-117">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="77f94-117">In This Section</span></span>  
 [<span data-ttu-id="77f94-118">Escolhendo entre a classe e Struct</span><span class="sxs-lookup"><span data-stu-id="77f94-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="77f94-119">Design de classe abstrata</span><span class="sxs-lookup"><span data-stu-id="77f94-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="77f94-120">Design de classe estática</span><span class="sxs-lookup"><span data-stu-id="77f94-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="77f94-121">Design de interface</span><span class="sxs-lookup"><span data-stu-id="77f94-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="77f94-122">Design de Struct</span><span class="sxs-lookup"><span data-stu-id="77f94-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="77f94-123">Design de enumeração</span><span class="sxs-lookup"><span data-stu-id="77f94-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="77f94-124">Tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="77f94-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="77f94-125">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="77f94-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="77f94-126">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="77f94-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f94-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77f94-127">See Also</span></span>  
 [<span data-ttu-id="77f94-128">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="77f94-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
