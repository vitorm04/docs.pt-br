---
title: Modificadores de acesso – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 5568d79c4a13b7b0db5a46bb4ebb2168ea66a2c9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606099"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="a9b5e-102">Modificadores de acesso (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a9b5e-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="a9b5e-103">Os modificadores de acesso são palavras-chave usadas para especificar a acessibilidade declarada de um membro ou de um tipo.</span><span class="sxs-lookup"><span data-stu-id="a9b5e-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="a9b5e-104">Esta seção apresenta os quatro modificadores de acesso:</span><span class="sxs-lookup"><span data-stu-id="a9b5e-104">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="a9b5e-105">Os seis seguintes níveis de acessibilidade podem ser especificados usando os modificadores de acesso:</span><span class="sxs-lookup"><span data-stu-id="a9b5e-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="a9b5e-106">[`public`](public.md): O acesso não é restrito.</span><span class="sxs-lookup"><span data-stu-id="a9b5e-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="a9b5e-107">[`protected`](protected.md): O acesso é limitado à classe que os contém ou aos tipos derivados da classe que os contém.</span><span class="sxs-lookup"><span data-stu-id="a9b5e-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="a9b5e-108">[`internal`](internal.md): O acesso é limitado ao assembly atual.</span><span class="sxs-lookup"><span data-stu-id="a9b5e-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="a9b5e-109">[`protected internal`](protected-internal.md): O acesso é limitado ao assembly atual ou aos tipos derivados da classe que os contém.</span><span class="sxs-lookup"><span data-stu-id="a9b5e-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="a9b5e-110">[`private`](private.md): O acesso é limitado ao tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="a9b5e-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="a9b5e-111">[`private protected`](private-protected.md): O acesso é limitado à classe que o contém ou a tipos derivados da classe que o contém no assembly atual.</span><span class="sxs-lookup"><span data-stu-id="a9b5e-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="a9b5e-112">Esta seção também apresenta o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a9b5e-112">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="a9b5e-113">[Níveis de acessibilidade](./accessibility-levels.md): utilização dos quatro modificadores de acesso para declarar seis níveis de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="a9b5e-113">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="a9b5e-114">[Domínio de acessibilidade](./accessibility-domain.md): especifica em que lugar, nas seções do programa, um membro pode ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="a9b5e-114">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="a9b5e-115">[Restrições ao uso de níveis de acessibilidade](./restrictions-on-using-accessibility-levels.md): um resumo das restrições sobre o uso de níveis de acessibilidade declarados.</span><span class="sxs-lookup"><span data-stu-id="a9b5e-115">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9b5e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9b5e-116">See also</span></span>

- [<span data-ttu-id="a9b5e-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a9b5e-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a9b5e-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a9b5e-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a9b5e-119">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="a9b5e-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="a9b5e-120">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="a9b5e-120">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="a9b5e-121">Palavras-chave de acesso</span><span class="sxs-lookup"><span data-stu-id="a9b5e-121">Access Keywords</span></span>](./access-keywords.md)
- [<span data-ttu-id="a9b5e-122">Modificadores</span><span class="sxs-lookup"><span data-stu-id="a9b5e-122">Modifiers</span></span>](./modifiers.md)
