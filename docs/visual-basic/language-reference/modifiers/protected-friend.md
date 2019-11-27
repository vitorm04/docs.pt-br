---
title: Amigo Protegido
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: f92021f5f0dab9762470c270bdd5182187d587e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351318"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="9de3c-102">Amigo protegido (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9de3c-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="9de3c-103">A combinação de palavras-chave `Protected Friend` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="9de3c-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="9de3c-104">Ele confere o acesso [Friend](friend.md) e o acesso [protegido](protected.md) nos elementos declarados, para que eles possam ser acessados de qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="9de3c-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="9de3c-105">Você pode especificar `Protected Friend` somente em membros de classes; Você não pode aplicar `Protected Friend` aos membros de uma estrutura porque as estruturas não podem ser herdadas.</span><span class="sxs-lookup"><span data-stu-id="9de3c-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="9de3c-106">No Visual Studio, a seleção de ajuda F1 no `protected friend` fornece ajuda para o [Protected](protected.md) ou o [Friend](friend.md).</span><span class="sxs-lookup"><span data-stu-id="9de3c-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="9de3c-107">O IDE escolhe o único token sob o cursor em vez da palavra composta.</span><span class="sxs-lookup"><span data-stu-id="9de3c-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="9de3c-108">Regras</span><span class="sxs-lookup"><span data-stu-id="9de3c-108">Rules</span></span>

<span data-ttu-id="9de3c-109">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="9de3c-109">**Declaration Context.**</span></span> <span data-ttu-id="9de3c-110">Você pode usar `Protected Friend` apenas no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="9de3c-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="9de3c-111">Isso significa que o contexto de declaração para um elemento de `Protected` deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="9de3c-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="9de3c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9de3c-112">See also</span></span>

- [<span data-ttu-id="9de3c-113">Público</span><span class="sxs-lookup"><span data-stu-id="9de3c-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="9de3c-114">Protegido</span><span class="sxs-lookup"><span data-stu-id="9de3c-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="9de3c-115">Friend</span><span class="sxs-lookup"><span data-stu-id="9de3c-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="9de3c-116">Privado</span><span class="sxs-lookup"><span data-stu-id="9de3c-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="9de3c-117">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="9de3c-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="9de3c-118">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9de3c-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="9de3c-119">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="9de3c-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="9de3c-120">Estruturas</span><span class="sxs-lookup"><span data-stu-id="9de3c-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="9de3c-121">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="9de3c-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
