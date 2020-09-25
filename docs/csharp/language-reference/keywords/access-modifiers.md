---
description: Modificadores de acesso – Referência de C#
title: Modificadores de acesso – Referência de C#
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: e941fc673c508f10863ee49b6544d6886bd594a3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168810"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="9e54a-103">Modificadores de acesso (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="9e54a-103">Access Modifiers (C# Reference)</span></span>

<span data-ttu-id="9e54a-104">Os modificadores de acesso são palavras-chave usadas para especificar a acessibilidade declarada de um membro ou de um tipo.</span><span class="sxs-lookup"><span data-stu-id="9e54a-104">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="9e54a-105">Esta seção apresenta os quatro modificadores de acesso:</span><span class="sxs-lookup"><span data-stu-id="9e54a-105">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="9e54a-106">Os seis seguintes níveis de acessibilidade podem ser especificados usando os modificadores de acesso:</span><span class="sxs-lookup"><span data-stu-id="9e54a-106">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="9e54a-107">[`public`](public.md): O acesso não é restrito.</span><span class="sxs-lookup"><span data-stu-id="9e54a-107">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="9e54a-108">[`protected`](protected.md): O acesso é limitado à classe que a contém ou aos tipos derivados da classe que a contém.</span><span class="sxs-lookup"><span data-stu-id="9e54a-108">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="9e54a-109">[`internal`](internal.md): O acesso é limitado ao assembly atual.</span><span class="sxs-lookup"><span data-stu-id="9e54a-109">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="9e54a-110">[`protected internal`](protected-internal.md): O acesso é limitado ao assembly ou tipos atuais derivados da classe que a contém.</span><span class="sxs-lookup"><span data-stu-id="9e54a-110">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="9e54a-111">[`private`](private.md): O acesso é limitado ao tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="9e54a-111">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="9e54a-112">[`private protected`](private-protected.md): O acesso é limitado à classe que a contém ou aos tipos derivados da classe que a contém dentro do assembly atual.</span><span class="sxs-lookup"><span data-stu-id="9e54a-112">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="9e54a-113">Esta seção também apresenta o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9e54a-113">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="9e54a-114">[Níveis de acessibilidade](./accessibility-levels.md): utilização dos quatro modificadores de acesso para declarar seis níveis de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="9e54a-114">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="9e54a-115">[Domínio de acessibilidade](./accessibility-domain.md): especifica em que lugar, nas seções do programa, um membro pode ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="9e54a-115">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="9e54a-116">[Restrições no uso de níveis de acessibilidade](./restrictions-on-using-accessibility-levels.md): um resumo das restrições sobre o uso de níveis de acessibilidade declarados.</span><span class="sxs-lookup"><span data-stu-id="9e54a-116">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e54a-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="9e54a-117">See also</span></span>

- [<span data-ttu-id="9e54a-118">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="9e54a-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9e54a-119">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="9e54a-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9e54a-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="9e54a-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="9e54a-121">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="9e54a-121">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="9e54a-122">Palavras-chave de acesso</span><span class="sxs-lookup"><span data-stu-id="9e54a-122">Access Keywords</span></span>](base.md)
- [<span data-ttu-id="9e54a-123">Modificadores</span><span class="sxs-lookup"><span data-stu-id="9e54a-123">Modifiers</span></span>](index.md)
