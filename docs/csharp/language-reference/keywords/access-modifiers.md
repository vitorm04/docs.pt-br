---
title: "Modificadores de acesso (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23f99d0925aefde7ef43888d16e888a0943dfc21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="1dc6b-102">Modificadores de acesso (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1dc6b-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="1dc6b-103">Os modificadores de acesso são palavras-chave usadas para especificar a acessibilidade declarada de um membro ou de um tipo.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="1dc6b-104">Esta seção apresenta os quatro modificadores de acesso:</span><span class="sxs-lookup"><span data-stu-id="1dc6b-104">This section introduces the four access modifiers:</span></span>  
  
-   [<span data-ttu-id="1dc6b-105">public</span><span class="sxs-lookup"><span data-stu-id="1dc6b-105">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
-   [<span data-ttu-id="1dc6b-106">protected</span><span class="sxs-lookup"><span data-stu-id="1dc6b-106">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
-   [<span data-ttu-id="1dc6b-107">internal</span><span class="sxs-lookup"><span data-stu-id="1dc6b-107">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
-   [<span data-ttu-id="1dc6b-108">private</span><span class="sxs-lookup"><span data-stu-id="1dc6b-108">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
 <span data-ttu-id="1dc6b-109">Os seguintes níveis de acessibilidade seis podem ser especificados usando os modificadores de acesso:</span><span class="sxs-lookup"><span data-stu-id="1dc6b-109">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
 <span data-ttu-id="1dc6b-110">`public`: o acesso não é restrito.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-110">`public`: Access is not restricted.</span></span>  
  
 <span data-ttu-id="1dc6b-111">`protected`: o acesso é limitado à classe que os contém ou aos tipos derivados da classe que os contém.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-111">`protected`: Access is limited to the containing class or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="1dc6b-112">`internal`: o acesso é limitado ao assembly atual.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-112">`internal`: Access is limited to the current assembly.</span></span>  
  
 <span data-ttu-id="1dc6b-113">[`protected internal`](../../../csharp/language-reference/keywords/protected-internal.md): O acesso é limitado ao conjunto atual ou tipos derivados da classe que contém.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-113">[`protected internal`](../../../csharp/language-reference/keywords/protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="1dc6b-114">`private`: o acesso é limitado ao tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-114">`private`: Access is limited to the containing type.</span></span>  

 <span data-ttu-id="1dc6b-115">[`private protected`](../../../csharp/language-reference/keywords/private-protected.md): O acesso é limitado à classe que contém ou tipos derivados da classe recipiente dentro do assembly atual.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-115">[`private protected`](../../../csharp/language-reference/keywords/private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="1dc6b-116">Esta seção também apresenta o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1dc6b-116">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="1dc6b-117">[Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md): usando os modificadores de acesso de quatro para declarar seis níveis de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-117">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="1dc6b-118">[Domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md): especifica em que lugar, nas seções do programa, um membro pode ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-118">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="1dc6b-119">[Restrições no uso de níveis de acessibilidade](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): um resumo das restrições sobre o uso de níveis de acessibilidade declarados.</span><span class="sxs-lookup"><span data-stu-id="1dc6b-119">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc6b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1dc6b-120">See Also</span></span>  
 [<span data-ttu-id="1dc6b-121">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1dc6b-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1dc6b-122">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1dc6b-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1dc6b-123">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="1dc6b-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1dc6b-124">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="1dc6b-124">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="1dc6b-125">Palavras-chave de acesso</span><span class="sxs-lookup"><span data-stu-id="1dc6b-125">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
 [<span data-ttu-id="1dc6b-126">Modificadores</span><span class="sxs-lookup"><span data-stu-id="1dc6b-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
