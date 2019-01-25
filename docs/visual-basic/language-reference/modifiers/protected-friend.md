---
title: Friend protegido (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 1858411e5543448e6d822c97b6e5c18da4a6c11e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639595"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="98cfa-102">Friend protegido (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98cfa-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="98cfa-103">A combinação de palavras-chave `Protected Friend` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="98cfa-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="98cfa-104">Ele confere ambos [amigo](friend.md) acesso e [protegido](protected.md) acesso os elementos declarados, portanto, eles são acessíveis de qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="98cfa-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="98cfa-105">Você pode especificar `Protected Friend` somente em membros de classes; não é possível aplicar `Protected Friend` aos membros de uma estrutura porque as estruturas não podem ser herdadas.</span><span class="sxs-lookup"><span data-stu-id="98cfa-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="98cfa-106">No Visual Studio, selecionando a Ajuda de F1 na `protected friend` fornece ajuda para o [protegidos](protected.md) ou [amigo](friend.md).</span><span class="sxs-lookup"><span data-stu-id="98cfa-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="98cfa-107">O IDE escolherá o token único sob o cursor em vez da palavra composta.</span><span class="sxs-lookup"><span data-stu-id="98cfa-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="98cfa-108">Regras</span><span class="sxs-lookup"><span data-stu-id="98cfa-108">Rules</span></span>

- <span data-ttu-id="98cfa-109">**Contexto da declaração.**</span><span class="sxs-lookup"><span data-stu-id="98cfa-109">**Declaration Context.**</span></span> <span data-ttu-id="98cfa-110">Você pode usar `Protected Friend` somente no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="98cfa-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="98cfa-111">Isso significa que o contexto da declaração para um `Protected` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, estrutura, módulo ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="98cfa-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span> 


## <a name="see-also"></a><span data-ttu-id="98cfa-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98cfa-112">See also</span></span>

- [<span data-ttu-id="98cfa-113">Público</span><span class="sxs-lookup"><span data-stu-id="98cfa-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="98cfa-114">Protegido</span><span class="sxs-lookup"><span data-stu-id="98cfa-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="98cfa-115">Friend</span><span class="sxs-lookup"><span data-stu-id="98cfa-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="98cfa-116">Privado</span><span class="sxs-lookup"><span data-stu-id="98cfa-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="98cfa-117">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="98cfa-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="98cfa-118">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="98cfa-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="98cfa-119">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="98cfa-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="98cfa-120">Estruturas</span><span class="sxs-lookup"><span data-stu-id="98cfa-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="98cfa-121">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="98cfa-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
