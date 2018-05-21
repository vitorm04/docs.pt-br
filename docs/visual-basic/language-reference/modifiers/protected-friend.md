---
title: Friend protegido (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: b72cbee0394043620e792d1c014bfe55121e175e
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/18/2018
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="81910-102">Friend protegido (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81910-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="81910-103">O `Protected Friend` combinação de palavra-chave é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="81910-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="81910-104">Ele confere ambos [Friend](friend.md) acesso e [protegidos](protected.md) acesso os elementos declarados, para que eles são acessíveis de qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="81910-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="81910-105">Você pode especificar `Protected Friend` somente em membros de classes; não é possível aplicar `Protected Friend` para membros de uma estrutura como estruturas não podem ser herdadas.</span><span class="sxs-lookup"><span data-stu-id="81910-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="81910-106">No Visual Studio, selecionando Ajuda F1 em `protected friend` fornece ajuda para o [protegido](protected.md) ou [friend](friend.md).</span><span class="sxs-lookup"><span data-stu-id="81910-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="81910-107">O IDE adota o token único sob o cursor em vez da palavra composta.</span><span class="sxs-lookup"><span data-stu-id="81910-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="81910-108">Regras</span><span class="sxs-lookup"><span data-stu-id="81910-108">Rules</span></span>

- <span data-ttu-id="81910-109">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="81910-109">**Declaration Context.**</span></span> <span data-ttu-id="81910-110">Você pode usar `Protected Friend` somente no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="81910-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="81910-111">Isso significa que o contexto da declaração para um `Protected` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="81910-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span> 


## <a name="see-also"></a><span data-ttu-id="81910-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81910-112">See Also</span></span>

[<span data-ttu-id="81910-113">Público</span><span class="sxs-lookup"><span data-stu-id="81910-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
[<span data-ttu-id="81910-114">Protegido</span><span class="sxs-lookup"><span data-stu-id="81910-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
<span data-ttu-id="81910-115">[Friend](friend.md) </span><span class="sxs-lookup"><span data-stu-id="81910-115">[Friend](friend.md) </span></span>  
[<span data-ttu-id="81910-116">Privado</span><span class="sxs-lookup"><span data-stu-id="81910-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
<span data-ttu-id="81910-117">[Privado protegido](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="81910-117">[Private Protected](./private-protected.md) </span></span>  
[<span data-ttu-id="81910-118">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81910-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[<span data-ttu-id="81910-119">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="81910-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[<span data-ttu-id="81910-120">Estruturas</span><span class="sxs-lookup"><span data-stu-id="81910-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[<span data-ttu-id="81910-121">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="81910-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
