---
title: Modificadores de acesso (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d63cf724a2364059e5f3327254a9ec95f7493e5e
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="caad3-102">Modificadores de acesso (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="caad3-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="caad3-103">Os modificadores de acesso são palavras-chave usadas para especificar a acessibilidade declarada de um membro ou de um tipo.</span><span class="sxs-lookup"><span data-stu-id="caad3-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="caad3-104">Esta seção apresenta os quatro modificadores de acesso:</span><span class="sxs-lookup"><span data-stu-id="caad3-104">This section introduces the four access modifiers:</span></span>  
  
-   `public`
-   `protected`
-   `internal`
-   `private`
  
 <span data-ttu-id="caad3-105">Os seis seguintes níveis de acessibilidade podem ser especificados usando os modificadores de acesso:</span><span class="sxs-lookup"><span data-stu-id="caad3-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="caad3-106">[`public`](public.md): o acesso não é restrito.</span><span class="sxs-lookup"><span data-stu-id="caad3-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="caad3-107">[`protected`](protected.md): o acesso é limitado à classe que os contém ou aos tipos derivados da classe que os contém.</span><span class="sxs-lookup"><span data-stu-id="caad3-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="caad3-108">[`internal`](internal.md): o acesso é limitado ao assembly atual.</span><span class="sxs-lookup"><span data-stu-id="caad3-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="caad3-109">[`protected internal`](protected-internal.md): o acesso é limitado ao assembly atual ou aos tipos derivados da classe que os contém.</span><span class="sxs-lookup"><span data-stu-id="caad3-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="caad3-110">[`private`](private.md): o acesso é limitado ao tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="caad3-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="caad3-111">[`private protected`](private-protected.md): o acesso é limitado à classe que o contém ou a tipos derivados da classe que o contém no assembly atual.</span><span class="sxs-lookup"><span data-stu-id="caad3-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="caad3-112">Esta seção também apresenta o seguinte:</span><span class="sxs-lookup"><span data-stu-id="caad3-112">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="caad3-113">[Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md): utilização dos quatro modificadores de acesso para declarar seis níveis de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="caad3-113">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="caad3-114">[Domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md): especifica em que lugar, nas seções do programa, um membro pode ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="caad3-114">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="caad3-115">[Restrições no uso de níveis de acessibilidade](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): um resumo das restrições sobre o uso de níveis de acessibilidade declarados.</span><span class="sxs-lookup"><span data-stu-id="caad3-115">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caad3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="caad3-116">See Also</span></span>  
 [<span data-ttu-id="caad3-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="caad3-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="caad3-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="caad3-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="caad3-119">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="caad3-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="caad3-120">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="caad3-120">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="caad3-121">Palavras-chave de acesso</span><span class="sxs-lookup"><span data-stu-id="caad3-121">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
 [<span data-ttu-id="caad3-122">Modificadores</span><span class="sxs-lookup"><span data-stu-id="caad3-122">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
