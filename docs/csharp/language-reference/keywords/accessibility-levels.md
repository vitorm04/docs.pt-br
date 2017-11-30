---
title: "Níveis de acessibilidade (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 77124554d7a0b38414e154e024aceddbfffcfbd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="556a0-102">Níveis de acessibilidade (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="556a0-102">Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="556a0-103">Use os modificadores de acesso, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou [private](../../../csharp/language-reference/keywords/private.md), para especificar um dos seguintes níveis de acessibilidade declarada de membros.</span><span class="sxs-lookup"><span data-stu-id="556a0-103">Use the access modifiers, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md), to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="556a0-104">Acessibilidade declarada</span><span class="sxs-lookup"><span data-stu-id="556a0-104">Declared accessibility</span></span>|<span data-ttu-id="556a0-105">Significado</span><span class="sxs-lookup"><span data-stu-id="556a0-105">Meaning</span></span>|  
|----------------------------|-------------|  
|`public`|<span data-ttu-id="556a0-106">O acesso não é restrito.</span><span class="sxs-lookup"><span data-stu-id="556a0-106">Access is not restricted.</span></span>|  
|`protected`|<span data-ttu-id="556a0-107">O acesso é limitado à classe que os contém ou aos tipos derivados da classe que os contém.</span><span class="sxs-lookup"><span data-stu-id="556a0-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|`internal`|<span data-ttu-id="556a0-108">O acesso é limitado ao assembly atual.</span><span class="sxs-lookup"><span data-stu-id="556a0-108">Access is limited to the current assembly.</span></span>|  
|`protected internal`|<span data-ttu-id="556a0-109">O acesso é limitado ao assembly atual ou aos tipos derivados da classe que os contém.</span><span class="sxs-lookup"><span data-stu-id="556a0-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|`private`|<span data-ttu-id="556a0-110">O acesso é limitado ao tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="556a0-110">Access is limited to the containing type.</span></span>|  
|`private protected`|<span data-ttu-id="556a0-111">O acesso é limitado à classe que contém ou tipos derivados da classe recipiente dentro do assembly atual.</span><span class="sxs-lookup"><span data-stu-id="556a0-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>|  
  
 <span data-ttu-id="556a0-112">Modificador de acesso de somente uma é permitida para um membro ou tipo, exceto quando você usa o `protected internal` ou `private protected` combinações.</span><span class="sxs-lookup"><span data-stu-id="556a0-112">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="556a0-113">Os modificadores de acesso não são permitidos em namespaces.</span><span class="sxs-lookup"><span data-stu-id="556a0-113">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="556a0-114">Namespaces não têm nenhuma restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="556a0-114">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="556a0-115">Dependendo do contexto no qual ocorre uma declaração de membro, apenas algumas acessibilidades declaradas são permitidas.</span><span class="sxs-lookup"><span data-stu-id="556a0-115">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="556a0-116">Se não for especificado nenhum modificador de acesso em uma declaração de membro, uma acessibilidade padrão será usada.</span><span class="sxs-lookup"><span data-stu-id="556a0-116">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="556a0-117">Os tipos de nível superior, que não estão aninhados em outros tipos, podem ter apenas a acessibilidade `internal` ou `public`.</span><span class="sxs-lookup"><span data-stu-id="556a0-117">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="556a0-118">A acessibilidade de padrão para esses tipos é `internal`.</span><span class="sxs-lookup"><span data-stu-id="556a0-118">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="556a0-119">Tipos aninhados, que são membros de outros tipos, podem ter acessibilidades declaradas conforme indicado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="556a0-119">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="556a0-120">Membros de</span><span class="sxs-lookup"><span data-stu-id="556a0-120">Members of</span></span>|<span data-ttu-id="556a0-121">Acessibilidade de membro padrão</span><span class="sxs-lookup"><span data-stu-id="556a0-121">Default member accessibility</span></span>|<span data-ttu-id="556a0-122">Acessibilidade declarada permitida do membro</span><span class="sxs-lookup"><span data-stu-id="556a0-122">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="556a0-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="556a0-123">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="556a0-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="556a0-124">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="556a0-125">A acessibilidade de um tipo aninhado depende do [domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md), que é determinado pela acessibilidade declarada do membro e pelo domínio da acessibilidade do tipo imediatamente contido.</span><span class="sxs-lookup"><span data-stu-id="556a0-125">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="556a0-126">Entretanto, o domínio de acessibilidade de um tipo aninhado não pode exceder o do tipo contido.</span><span class="sxs-lookup"><span data-stu-id="556a0-126">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="556a0-127">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="556a0-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="556a0-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="556a0-128">See Also</span></span>  
 [<span data-ttu-id="556a0-129">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="556a0-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="556a0-130">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="556a0-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="556a0-131">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="556a0-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="556a0-132">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="556a0-132">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="556a0-133">Domínio de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="556a0-133">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="556a0-134">Restrições ao uso de níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="556a0-134">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [<span data-ttu-id="556a0-135">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="556a0-135">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="556a0-136">public</span><span class="sxs-lookup"><span data-stu-id="556a0-136">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="556a0-137">private</span><span class="sxs-lookup"><span data-stu-id="556a0-137">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="556a0-138">protected</span><span class="sxs-lookup"><span data-stu-id="556a0-138">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="556a0-139">internal</span><span class="sxs-lookup"><span data-stu-id="556a0-139">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
