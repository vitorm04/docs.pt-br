---
title: Tipos aninhados (Guia de Programação em C#)
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: f99b84d5b21261fa81c02d028d1f913be7290dbb
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43740160"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="288db-102">Tipos aninhados (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="288db-102">Nested Types (C# Programming Guide)</span></span>
<span data-ttu-id="288db-103">Um tipo definido em uma [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md) é denominado tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="288db-103">A type defined within a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is called a nested type.</span></span> <span data-ttu-id="288db-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="288db-104">For example:</span></span>  
  
[!code-csharp[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]  
  
<span data-ttu-id="288db-105">Independentemente de o tipo externo ser uma classe ou uma estrutura, tipos aninhados tornam-se [privados](../../../csharp/language-reference/keywords/private.md) por padrão; eles são acessíveis somente de seu tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="288db-105">Regardless of whether the outer type is a class or a struct, nested types default to [private](../../../csharp/language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="288db-106">No exemplo anterior, a classe `Nested` é inacessível para tipos externos.</span><span class="sxs-lookup"><span data-stu-id="288db-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span> 

<span data-ttu-id="288db-107">Você também pode especificar um [modificador de acesso](../../language-reference/keywords/access-modifiers.md) para definir a acessibilidade de um tipo aninhado, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="288db-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="288db-108">Os tipos aninhados de uma **classe** podem ser [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md), [private](../../../csharp/language-reference/keywords/private.md) ou [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="288db-108">Nested types of a **class** can be [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md), [private](../../../csharp/language-reference/keywords/private.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> 

   <span data-ttu-id="288db-109">No entanto, a definição de uma classe aninhada `protected`, `protected internal` ou `private protected` dentro de uma [classe selada](../../language-reference/keywords/sealed.md) gera um aviso do compilador [CS0628](../../misc/cs0628.md), "novo membro protegido declarado na classe selada".</span><span class="sxs-lookup"><span data-stu-id="288db-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="288db-110">Tipos aninhados de um **struct** podem ser [públicos](../../../csharp/language-reference/keywords/public.md), [internos](../../../csharp/language-reference/keywords/internal.md) ou [particulares](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="288db-110">Nested types of a **struct** can be [public](../../../csharp/language-reference/keywords/public.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md).</span></span>
  
<span data-ttu-id="288db-111">O exemplo a seguir torna a classe `Nested` pública:</span><span class="sxs-lookup"><span data-stu-id="288db-111">The following example makes the `Nested` class public:</span></span>
  
[!code-csharp[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]  
  
 <span data-ttu-id="288db-112">O tipo aninhado ou interno pode acessar o tipo recipiente ou externo.</span><span class="sxs-lookup"><span data-stu-id="288db-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="288db-113">Para acessar o tipo recipiente, passe-o como um argumento ao construtor do tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="288db-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="288db-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="288db-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]  
  
 <span data-ttu-id="288db-115">Um tipo aninhado tem acesso a todos os membros acessíveis ao seu tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="288db-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="288db-116">Ele pode acessar membros privados e protegidos do tipo recipiente, incluindo quaisquer membros protegidos herdados.</span><span class="sxs-lookup"><span data-stu-id="288db-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>  
  
 <span data-ttu-id="288db-117">Na declaração anterior, o nome completo da classe `Nested` é `Container.Nested`.</span><span class="sxs-lookup"><span data-stu-id="288db-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="288db-118">Este é o nome usado para criar uma nova instância da classe aninhada, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="288db-118">This is the name used to create a new instance of the nested class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="288db-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="288db-119">See Also</span></span>

- [<span data-ttu-id="288db-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="288db-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="288db-121">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="288db-121">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="288db-122">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="288db-122">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [<span data-ttu-id="288db-123">Construtores</span><span class="sxs-lookup"><span data-stu-id="288db-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
