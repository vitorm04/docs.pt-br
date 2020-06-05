---
title: Amigo Protegido
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 202d4f4a3a05a64ab1d74621268f28f6b55e8952
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404830"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="72263-102">Amigo protegido (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72263-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="72263-103">A combinação de palavras-chave `Protected Friend` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="72263-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="72263-104">Ele confere o acesso [Friend](friend.md) e o acesso [protegido](protected.md) nos elementos declarados, para que eles possam ser acessados de qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="72263-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="72263-105">Você pode especificar `Protected Friend` somente membros de classes; não é possível aplicar `Protected Friend` a membros de uma estrutura porque as estruturas não podem ser herdadas.</span><span class="sxs-lookup"><span data-stu-id="72263-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="72263-106">No Visual Studio, a seleção de ajuda F1 no `protected friend` fornece ajuda para o [protegido](protected.md) ou [amigo](friend.md).</span><span class="sxs-lookup"><span data-stu-id="72263-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="72263-107">O IDE escolhe o único token sob o cursor em vez da palavra composta.</span><span class="sxs-lookup"><span data-stu-id="72263-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="72263-108">Regras</span><span class="sxs-lookup"><span data-stu-id="72263-108">Rules</span></span>

<span data-ttu-id="72263-109">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="72263-109">**Declaration Context.**</span></span> <span data-ttu-id="72263-110">Você pode usar `Protected Friend` somente no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="72263-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="72263-111">Isso significa que o contexto de declaração para um `Protected` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="72263-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="72263-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="72263-112">See also</span></span>

- [<span data-ttu-id="72263-113">Pública</span><span class="sxs-lookup"><span data-stu-id="72263-113">Public</span></span>](public.md)
- [<span data-ttu-id="72263-114">Protected</span><span class="sxs-lookup"><span data-stu-id="72263-114">Protected</span></span>](protected.md)
- [<span data-ttu-id="72263-115">Público</span><span class="sxs-lookup"><span data-stu-id="72263-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="72263-116">Privada</span><span class="sxs-lookup"><span data-stu-id="72263-116">Private</span></span>](private.md)
- [<span data-ttu-id="72263-117">Particular protegido</span><span class="sxs-lookup"><span data-stu-id="72263-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="72263-118">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72263-118">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="72263-119">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="72263-119">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="72263-120">Estruturas</span><span class="sxs-lookup"><span data-stu-id="72263-120">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="72263-121">Objetos e classes</span><span class="sxs-lookup"><span data-stu-id="72263-121">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
