---
title: Tipos aninhados – Guia de Programação em C#
description: Um tipo definido em uma classe, struct ou interface é chamado de tipo aninhado em C#.
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 9e1c6c1e8b22b5447d43915ab02984aa13146301
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864937"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="4b3b6-103">Tipos aninhados (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="4b3b6-103">Nested Types (C# Programming Guide)</span></span>

<span data-ttu-id="4b3b6-104">Um tipo definido em uma [classe](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md)ou [interface](../../language-reference/keywords/interface.md) é chamado de tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="4b3b6-104">A type defined within a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) is called a nested type.</span></span> <span data-ttu-id="4b3b6-105">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="4b3b6-105">For example</span></span>

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

<span data-ttu-id="4b3b6-106">Independentemente de o tipo externo ser uma classe, interface ou struct, os tipos aninhados são padrão para [privado](../../language-reference/keywords/private.md); Eles são acessíveis somente de seu tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="4b3b6-106">Regardless of whether the outer type is a class, interface, or struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="4b3b6-107">No exemplo anterior, a classe `Nested` é inacessível para tipos externos.</span><span class="sxs-lookup"><span data-stu-id="4b3b6-107">In the previous example, the `Nested` class is inaccessible to external types.</span></span>

<span data-ttu-id="4b3b6-108">Você também pode especificar um [modificador de acesso](../../language-reference/keywords/access-modifiers.md) para definir a acessibilidade de um tipo aninhado, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4b3b6-108">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="4b3b6-109">Os tipos aninhados de uma **classe** podem ser [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) ou [private protected](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="4b3b6-109">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span>

   <span data-ttu-id="4b3b6-110">No entanto, a definição de uma classe aninhada `protected`, `protected internal` ou `private protected` dentro de uma [classe selada](../../language-reference/keywords/sealed.md) gera um aviso do compilador [CS0628](../../misc/cs0628.md), "novo membro protegido declarado na classe selada".</span><span class="sxs-lookup"><span data-stu-id="4b3b6-110">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="4b3b6-111">Tipos aninhados de um **struct** podem ser [públicos](../../language-reference/keywords/public.md), [internos](../../language-reference/keywords/internal.md) ou [particulares](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="4b3b6-111">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>

<span data-ttu-id="4b3b6-112">O exemplo a seguir torna a classe `Nested` pública:</span><span class="sxs-lookup"><span data-stu-id="4b3b6-112">The following example makes the `Nested` class public:</span></span>

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

<span data-ttu-id="4b3b6-113">O tipo aninhado ou interno pode acessar o tipo recipiente ou externo.</span><span class="sxs-lookup"><span data-stu-id="4b3b6-113">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="4b3b6-114">Para acessar o tipo recipiente, passe-o como um argumento ao construtor do tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="4b3b6-114">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="4b3b6-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4b3b6-115">For example:</span></span>

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

<span data-ttu-id="4b3b6-116">Um tipo aninhado tem acesso a todos os membros acessíveis ao seu tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="4b3b6-116">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="4b3b6-117">Ele pode acessar membros privados e protegidos do tipo recipiente, incluindo quaisquer membros protegidos herdados.</span><span class="sxs-lookup"><span data-stu-id="4b3b6-117">It can access private and protected members of the containing type, including any inherited protected members.</span></span>

<span data-ttu-id="4b3b6-118">Na declaração anterior, o nome completo da classe `Nested` é `Container.Nested`.</span><span class="sxs-lookup"><span data-stu-id="4b3b6-118">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="4b3b6-119">Este é o nome usado para criar uma nova instância da classe aninhada, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4b3b6-119">This is the name used to create a new instance of the nested class, as follows:</span></span>

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a><span data-ttu-id="4b3b6-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="4b3b6-120">See also</span></span>

- [<span data-ttu-id="4b3b6-121">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="4b3b6-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4b3b6-122">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="4b3b6-122">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="4b3b6-123">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="4b3b6-123">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="4b3b6-124">Construtores</span><span class="sxs-lookup"><span data-stu-id="4b3b6-124">Constructors</span></span>](./constructors.md)
