---
title: "Níveis de acessibilidade (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 796802a407c486c1df5332d5b4920467f3a1171b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="4d855-102">Níveis de acessibilidade (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4d855-102">Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="4d855-103">Use os modificadores de acesso, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou [private](../../../csharp/language-reference/keywords/private.md), para especificar um dos seguintes níveis de acessibilidade declarada de membros.</span><span class="sxs-lookup"><span data-stu-id="4d855-103">Use the access modifiers, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md), to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="4d855-104">Acessibilidade declarada</span><span class="sxs-lookup"><span data-stu-id="4d855-104">Declared accessibility</span></span>|<span data-ttu-id="4d855-105">Significado</span><span class="sxs-lookup"><span data-stu-id="4d855-105">Meaning</span></span>|  
|----------------------------|-------------|  
|`public`|<span data-ttu-id="4d855-106">O acesso não é restrito.</span><span class="sxs-lookup"><span data-stu-id="4d855-106">Access is not restricted.</span></span>|  
|`protected`|<span data-ttu-id="4d855-107">O acesso é limitado à classe que os contém ou aos tipos derivados da classe que os contém.</span><span class="sxs-lookup"><span data-stu-id="4d855-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|`internal`|<span data-ttu-id="4d855-108">O acesso é limitado ao assembly atual.</span><span class="sxs-lookup"><span data-stu-id="4d855-108">Access is limited to the current assembly.</span></span>|  
|`protected internal`|<span data-ttu-id="4d855-109">O acesso é limitado ao assembly atual ou aos tipos derivados da classe que os contém.</span><span class="sxs-lookup"><span data-stu-id="4d855-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|`private`|<span data-ttu-id="4d855-110">O acesso é limitado ao tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="4d855-110">Access is limited to the containing type.</span></span>|  
  
 <span data-ttu-id="4d855-111">Apenas um modificador de acesso é permitido para um membro ou tipo, exceto quando você usa a combinação `protected internal`.</span><span class="sxs-lookup"><span data-stu-id="4d855-111">Only one access modifier is allowed for a member or type, except when you use the `protected internal` combination.</span></span>  
  
 <span data-ttu-id="4d855-112">Os modificadores de acesso não são permitidos em namespaces.</span><span class="sxs-lookup"><span data-stu-id="4d855-112">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="4d855-113">Namespaces não têm nenhuma restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="4d855-113">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="4d855-114">Dependendo do contexto no qual ocorre uma declaração de membro, apenas algumas acessibilidades declaradas são permitidas.</span><span class="sxs-lookup"><span data-stu-id="4d855-114">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="4d855-115">Se não for especificado nenhum modificador de acesso em uma declaração de membro, uma acessibilidade padrão será usada.</span><span class="sxs-lookup"><span data-stu-id="4d855-115">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="4d855-116">Os tipos de nível superior, que não estão aninhados em outros tipos, podem ter apenas a acessibilidade `internal` ou `public`.</span><span class="sxs-lookup"><span data-stu-id="4d855-116">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="4d855-117">A acessibilidade de padrão para esses tipos é `internal`.</span><span class="sxs-lookup"><span data-stu-id="4d855-117">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="4d855-118">Tipos aninhados, que são membros de outros tipos, podem ter acessibilidades declaradas conforme indicado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="4d855-118">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="4d855-119">Membros de</span><span class="sxs-lookup"><span data-stu-id="4d855-119">Members of</span></span>|<span data-ttu-id="4d855-120">Acessibilidade de membro padrão</span><span class="sxs-lookup"><span data-stu-id="4d855-120">Default member accessibility</span></span>|<span data-ttu-id="4d855-121">Acessibilidade declarada permitida do membro</span><span class="sxs-lookup"><span data-stu-id="4d855-121">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="4d855-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4d855-122">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal`|  
|`interface`|`public`|<span data-ttu-id="4d855-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4d855-123">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="4d855-124">A acessibilidade de um tipo aninhado depende do [domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md), que é determinado pela acessibilidade declarada do membro e pelo domínio da acessibilidade do tipo imediatamente contido.</span><span class="sxs-lookup"><span data-stu-id="4d855-124">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="4d855-125">Entretanto, o domínio de acessibilidade de um tipo aninhado não pode exceder o do tipo contido.</span><span class="sxs-lookup"><span data-stu-id="4d855-125">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4d855-126">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="4d855-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4d855-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d855-127">See Also</span></span>  
 <span data-ttu-id="4d855-128">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4d855-128">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="4d855-129">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4d855-129">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4d855-130">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="4d855-130">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="4d855-131">[Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="4d855-131">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="4d855-132">[Domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md) </span><span class="sxs-lookup"><span data-stu-id="4d855-132">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md) </span></span>  
 <span data-ttu-id="4d855-133">[Restrições ao uso de níveis de acessibilidade](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="4d855-133">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) </span></span>  
 <span data-ttu-id="4d855-134">[Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="4d855-134">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="4d855-135">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="4d855-135">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="4d855-136">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="4d855-136">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="4d855-137">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="4d855-137">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 [<span data-ttu-id="4d855-138">internal</span><span class="sxs-lookup"><span data-stu-id="4d855-138">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

