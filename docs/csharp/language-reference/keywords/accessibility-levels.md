---
title: Níveis de acessibilidade (Referência de C#)
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 4679fd2564454e7f1ade5cb4813729b65f433012
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44194720"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="270d4-102">Níveis de acessibilidade (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="270d4-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="270d4-103">Use os modificadores de acesso, `public`, `protected`, `internal` ou `private`, para especificar um dos níveis de acessibilidade declarada a seguir para membros.</span><span class="sxs-lookup"><span data-stu-id="270d4-103">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="270d4-104">Acessibilidade declarada</span><span class="sxs-lookup"><span data-stu-id="270d4-104">Declared accessibility</span></span>|<span data-ttu-id="270d4-105">Significado</span><span class="sxs-lookup"><span data-stu-id="270d4-105">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="270d4-106">O acesso não é restrito.</span><span class="sxs-lookup"><span data-stu-id="270d4-106">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="270d4-107">O acesso é limitado à classe que os contém ou aos tipos derivados da classe que os contém.</span><span class="sxs-lookup"><span data-stu-id="270d4-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="270d4-108">O acesso é limitado ao assembly atual.</span><span class="sxs-lookup"><span data-stu-id="270d4-108">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="270d4-109">O acesso é limitado ao assembly atual ou aos tipos derivados da classe que os contém.</span><span class="sxs-lookup"><span data-stu-id="270d4-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="270d4-110">O acesso é limitado ao tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="270d4-110">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="270d4-111">O acesso é limitado à classe que o contém ou a tipos derivados da classe que o contém no assembly atual.</span><span class="sxs-lookup"><span data-stu-id="270d4-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="270d4-112">Disponível desde o C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="270d4-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="270d4-113">Apenas um modificador de acesso é permitido para um membro ou tipo, exceto quando você usa as combinações `protected internal` e `private protected`.</span><span class="sxs-lookup"><span data-stu-id="270d4-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="270d4-114">Os modificadores de acesso não são permitidos em namespaces.</span><span class="sxs-lookup"><span data-stu-id="270d4-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="270d4-115">Namespaces não têm nenhuma restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="270d4-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="270d4-116">Dependendo do contexto no qual ocorre uma declaração de membro, apenas algumas acessibilidades declaradas são permitidas.</span><span class="sxs-lookup"><span data-stu-id="270d4-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="270d4-117">Se não for especificado nenhum modificador de acesso em uma declaração de membro, uma acessibilidade padrão será usada.</span><span class="sxs-lookup"><span data-stu-id="270d4-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="270d4-118">Os tipos de nível superior, que não estão aninhados em outros tipos, podem ter apenas a acessibilidade `internal` ou `public`.</span><span class="sxs-lookup"><span data-stu-id="270d4-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="270d4-119">A acessibilidade de padrão para esses tipos é `internal`.</span><span class="sxs-lookup"><span data-stu-id="270d4-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="270d4-120">Tipos aninhados, que são membros de outros tipos, podem ter acessibilidades declaradas conforme indicado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="270d4-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="270d4-121">Membros de</span><span class="sxs-lookup"><span data-stu-id="270d4-121">Members of</span></span>|<span data-ttu-id="270d4-122">Acessibilidade de membro padrão</span><span class="sxs-lookup"><span data-stu-id="270d4-122">Default member accessibility</span></span>|<span data-ttu-id="270d4-123">Acessibilidade declarada permitida do membro</span><span class="sxs-lookup"><span data-stu-id="270d4-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="270d4-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="270d4-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="270d4-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="270d4-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="270d4-126">A acessibilidade de um tipo aninhado depende do [domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md), que é determinado pela acessibilidade declarada do membro e pelo domínio da acessibilidade do tipo imediatamente contido.</span><span class="sxs-lookup"><span data-stu-id="270d4-126">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="270d4-127">Entretanto, o domínio de acessibilidade de um tipo aninhado não pode exceder o do tipo contido.</span><span class="sxs-lookup"><span data-stu-id="270d4-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="270d4-128">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="270d4-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="270d4-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="270d4-129">See Also</span></span>  
- [<span data-ttu-id="270d4-130">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="270d4-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="270d4-131">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="270d4-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="270d4-132">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="270d4-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="270d4-133">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="270d4-133">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [<span data-ttu-id="270d4-134">Domínio de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="270d4-134">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
- [<span data-ttu-id="270d4-135">Restrições ao uso de níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="270d4-135">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
- [<span data-ttu-id="270d4-136">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="270d4-136">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [<span data-ttu-id="270d4-137">public</span><span class="sxs-lookup"><span data-stu-id="270d4-137">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
- [<span data-ttu-id="270d4-138">private</span><span class="sxs-lookup"><span data-stu-id="270d4-138">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
- [<span data-ttu-id="270d4-139">protected</span><span class="sxs-lookup"><span data-stu-id="270d4-139">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
- [<span data-ttu-id="270d4-140">internal</span><span class="sxs-lookup"><span data-stu-id="270d4-140">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
