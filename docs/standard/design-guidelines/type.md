---
title: Diretrizes de Design de tipo
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: 17bd300277a039818a3d563c8f2d5f99eb2fc68d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289558"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="88d98-102">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="88d98-102">Type Design Guidelines</span></span>
<span data-ttu-id="88d98-103">Da perspectiva do CLR, há apenas duas categorias de tipos — tipos de referência e tipos de valor — mas, para fins de uma discussão sobre design de estrutura, dividimos os tipos em mais grupos lógicos, cada um com suas próprias regras de design específicas.</span><span class="sxs-lookup"><span data-stu-id="88d98-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>

 <span data-ttu-id="88d98-104">As classes são o caso geral dos tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="88d98-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="88d98-105">Eles compõem a massa de tipos na maioria das estruturas.</span><span class="sxs-lookup"><span data-stu-id="88d98-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="88d98-106">As classes conferem sua popularidade ao conjunto avançado de recursos orientados a objeto que dão suporte e à aplicabilidade geral.</span><span class="sxs-lookup"><span data-stu-id="88d98-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="88d98-107">As classes base e as classes abstratas são grupos lógicos especiais relacionados à extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="88d98-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>

 <span data-ttu-id="88d98-108">Interfaces são tipos que podem ser implementados por tipos de referência e tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="88d98-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="88d98-109">Assim, eles podem servir como raízes de hierarquias polimórficas de tipos de referência e tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="88d98-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="88d98-110">Além disso, as interfaces podem ser usadas para simular várias heranças, o que não tem suporte nativo do CLR.</span><span class="sxs-lookup"><span data-stu-id="88d98-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>

 <span data-ttu-id="88d98-111">As structs são o caso geral dos tipos de valor e devem ser reservadas para tipos pequenos e simples, semelhantes aos primitivos de linguagem.</span><span class="sxs-lookup"><span data-stu-id="88d98-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>

 <span data-ttu-id="88d98-112">Enums são um caso especial de tipos de valor usados para definir conjuntos curtos de valores, como dias da semana, cores do console e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="88d98-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>

 <span data-ttu-id="88d98-113">Classes estáticas são tipos destinados a contêineres para membros estáticos.</span><span class="sxs-lookup"><span data-stu-id="88d98-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="88d98-114">Normalmente, eles são usados para fornecer atalhos para outras operações.</span><span class="sxs-lookup"><span data-stu-id="88d98-114">They are commonly used to provide shortcuts to other operations.</span></span>

 <span data-ttu-id="88d98-115">Delegados, exceções, atributos, matrizes e coleções são casos especiais de tipos de referência destinados a usos específicos, e as diretrizes para seu design e uso são discutidas em outro lugar neste livro.</span><span class="sxs-lookup"><span data-stu-id="88d98-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>

 <span data-ttu-id="88d98-116">✔️ garantir que cada tipo seja um conjunto bem definido de membros relacionados, não apenas uma coleção aleatória de funcionalidades não relacionadas.</span><span class="sxs-lookup"><span data-stu-id="88d98-116">✔️ DO ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="88d98-117">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="88d98-117">In This Section</span></span>
 <span data-ttu-id="88d98-118">[Escolher entre](choosing-between-class-and-struct.md) classes [abstratas](abstract-class.md) de classe e struct design da classe [estática](static-class.md) [design de](interface.md) design [struct](struct.md) [design de](enum.md) design de estrutura [tipos aninhados](nested-types.md) *partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="88d98-118">[Choosing Between Class and Struct](choosing-between-class-and-struct.md) [Abstract Class Design](abstract-class.md) [Static Class Design](static-class.md) [Interface Design](interface.md) [Struct Design](struct.md) [Enum Design](enum.md) [Nested Types](nested-types.md) *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="88d98-119">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="88d98-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="88d98-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="88d98-120">See also</span></span>

- [<span data-ttu-id="88d98-121">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="88d98-121">Framework Design Guidelines</span></span>](index.md)
