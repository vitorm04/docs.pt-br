---
title: Tipos aninhados – Guia de Programação em C#
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 12e44ccc1254424c152a238c8390f133550fa54c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626484"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="52f9c-102">Tipos aninhados (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="52f9c-102">Nested Types (C# Programming Guide)</span></span>

<span data-ttu-id="52f9c-103">Um tipo definido dentro de uma [classe](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), ou [interface](../../language-reference/keywords/interface.md) é chamado de um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="52f9c-103">A type defined within a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) is called a nested type.</span></span> <span data-ttu-id="52f9c-104">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="52f9c-104">For example</span></span>

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

<span data-ttu-id="52f9c-105">Independentemente de o tipo externo ser uma classe, interface ou struct, tipos aninhados padrão para [privados;](../../language-reference/keywords/private.md) eles são acessíveis apenas a partir de seu tipo contendo.</span><span class="sxs-lookup"><span data-stu-id="52f9c-105">Regardless of whether the outer type is a class, interface, or struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="52f9c-106">No exemplo anterior, a classe `Nested` é inacessível para tipos externos.</span><span class="sxs-lookup"><span data-stu-id="52f9c-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span>

<span data-ttu-id="52f9c-107">Você também pode especificar um [modificador de acesso](../../language-reference/keywords/access-modifiers.md) para definir a acessibilidade de um tipo aninhado, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="52f9c-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="52f9c-108">Os tipos aninhados de uma **classe** podem ser [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) ou [private protected](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="52f9c-108">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span>

   <span data-ttu-id="52f9c-109">No entanto, a definição de uma classe aninhada `protected`, `protected internal` ou `private protected` dentro de uma [classe selada](../../language-reference/keywords/sealed.md) gera um aviso do compilador [CS0628](../../misc/cs0628.md), "novo membro protegido declarado na classe selada".</span><span class="sxs-lookup"><span data-stu-id="52f9c-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="52f9c-110">Tipos aninhados de um **struct** podem ser [públicos](../../language-reference/keywords/public.md), [internos](../../language-reference/keywords/internal.md) ou [particulares](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="52f9c-110">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>

<span data-ttu-id="52f9c-111">O exemplo a seguir torna a classe `Nested` pública:</span><span class="sxs-lookup"><span data-stu-id="52f9c-111">The following example makes the `Nested` class public:</span></span>

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

<span data-ttu-id="52f9c-112">O tipo aninhado ou interno pode acessar o tipo recipiente ou externo.</span><span class="sxs-lookup"><span data-stu-id="52f9c-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="52f9c-113">Para acessar o tipo recipiente, passe-o como um argumento ao construtor do tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="52f9c-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="52f9c-114">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="52f9c-114">For example:</span></span>

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

<span data-ttu-id="52f9c-115">Um tipo aninhado tem acesso a todos os membros acessíveis ao seu tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="52f9c-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="52f9c-116">Ele pode acessar membros privados e protegidos do tipo recipiente, incluindo quaisquer membros protegidos herdados.</span><span class="sxs-lookup"><span data-stu-id="52f9c-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>

<span data-ttu-id="52f9c-117">Na declaração anterior, o nome completo da classe `Nested` é `Container.Nested`.</span><span class="sxs-lookup"><span data-stu-id="52f9c-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="52f9c-118">Este é o nome usado para criar uma nova instância da classe aninhada, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="52f9c-118">This is the name used to create a new instance of the nested class, as follows:</span></span>

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a><span data-ttu-id="52f9c-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="52f9c-119">See also</span></span>

- [<span data-ttu-id="52f9c-120">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="52f9c-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="52f9c-121">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="52f9c-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="52f9c-122">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="52f9c-122">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="52f9c-123">Construtores</span><span class="sxs-lookup"><span data-stu-id="52f9c-123">Constructors</span></span>](./constructors.md)
