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
ms.openlocfilehash: a7fb9964d0e542c0937c55ae65bd88b3f7149fa8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187933"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="c1576-102">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="c1576-102">Type Design Guidelines</span></span>
<span data-ttu-id="c1576-103">Da perspectiva do CLR, há apenas duas categorias de tipos — fazer referência a tipos e tipos de valor — mas com a finalidade de uma discussão sobre o design de estrutura, dividimos tipos em grupos mais lógicos, cada um com suas próprias regras de design específico.</span><span class="sxs-lookup"><span data-stu-id="c1576-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="c1576-104">As classes são o caso geral de tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="c1576-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="c1576-105">Eles formam a maior parte dos tipos na maioria das estruturas.</span><span class="sxs-lookup"><span data-stu-id="c1576-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="c1576-106">Classes deve sua popularidade, para o amplo conjunto de recursos orientados a objeto, que oferecem suporte e sua aplicabilidade geral.</span><span class="sxs-lookup"><span data-stu-id="c1576-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="c1576-107">Classes base e classes abstratas são grupos lógicos especiais relacionados à extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="c1576-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="c1576-108">Interfaces são tipos que podem ser implementados por tipos de referência e tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="c1576-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="c1576-109">Assim, elas servem como raízes de polimórficas hierarquias de tipos de referência e tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="c1576-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="c1576-110">Além disso, as interfaces podem ser usadas para simular a herança múltipla, que não tem suporte nativo pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="c1576-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="c1576-111">Structs são o caso geral de tipos de valor e deve ser reservados para tipos de pequenos e simples, semelhantes a primitivos de linguagem.</span><span class="sxs-lookup"><span data-stu-id="c1576-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="c1576-112">Enumerações são um caso especial de tipos de valor usados para definir conjuntos de curtos de valores, como dias da semana, cores de console e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="c1576-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="c1576-113">Classes estáticas são tipos que se destina a ser contêineres para membros estáticos.</span><span class="sxs-lookup"><span data-stu-id="c1576-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="c1576-114">Normalmente, eles são usados para fornecer atalhos para outras operações.</span><span class="sxs-lookup"><span data-stu-id="c1576-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="c1576-115">Delegados, exceções, atributos, matrizes e coleções são todos os casos especiais de tipos de referência que se destina para usos específicos, e diretrizes para design e uso são discutidas em outro lugar neste livro.</span><span class="sxs-lookup"><span data-stu-id="c1576-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="c1576-116">**✓ DO** Certifique-se de que cada tipo é um conjunto bem definido de membros relacionados, não apenas um conjunto aleatório de funcionalidades relacionadas.</span><span class="sxs-lookup"><span data-stu-id="c1576-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1576-117">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c1576-117">In This Section</span></span>  
 [<span data-ttu-id="c1576-118">Escolhendo entre a classe e Struct</span><span class="sxs-lookup"><span data-stu-id="c1576-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="c1576-119">Design de classe abstrata</span><span class="sxs-lookup"><span data-stu-id="c1576-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="c1576-120">Design de classe estática</span><span class="sxs-lookup"><span data-stu-id="c1576-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="c1576-121">Design de interface</span><span class="sxs-lookup"><span data-stu-id="c1576-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="c1576-122">Design de Struct</span><span class="sxs-lookup"><span data-stu-id="c1576-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="c1576-123">Design de enumeração</span><span class="sxs-lookup"><span data-stu-id="c1576-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="c1576-124">Tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="c1576-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="c1576-125">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="c1576-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c1576-126">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c1576-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1576-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1576-127">See also</span></span>

- [<span data-ttu-id="c1576-128">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="c1576-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
