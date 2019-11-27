---
title: Cláusula Implements
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: f114aee75356e59eafd9d3ba6af9c64402cb374f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345869"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="47820-102">Cláusula Implements (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47820-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="47820-103">Indica que um membro de classe ou estrutura está fornecendo a implementação para um membro definido em uma interface.</span><span class="sxs-lookup"><span data-stu-id="47820-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47820-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="47820-104">Remarks</span></span>  
<span data-ttu-id="47820-105">A palavra-chave `Implements` não é a mesma que a [instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="47820-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="47820-106">Use a instrução `Implements` para especificar que uma classe ou estrutura implementa uma ou mais interfaces e, em seguida, para cada membro, use a palavra-chave `Implements` para especificar qual interface e qual membro ele implementa.</span><span class="sxs-lookup"><span data-stu-id="47820-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="47820-107">Se uma classe ou estrutura implementa uma interface, ela deve incluir a instrução `Implements` imediatamente após a instrução de [classe](../../../visual-basic/language-reference/statements/class-statement.md) ou a [instrução de estrutura](../../../visual-basic/language-reference/statements/structure-statement.md), e deve implementar todos os membros definidos pela interface.</span><span class="sxs-lookup"><span data-stu-id="47820-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="47820-108">Reimplementação</span><span class="sxs-lookup"><span data-stu-id="47820-108">Reimplementation</span></span>  
<span data-ttu-id="47820-109">Em uma classe derivada, você pode reimplementar um membro de interface que a classe base já tenha implementado.</span><span class="sxs-lookup"><span data-stu-id="47820-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="47820-110">Isso é diferente de substituir o membro da classe base nos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="47820-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="47820-111">O membro da classe base não precisa ser [substituível](../../../visual-basic/language-reference/modifiers/overridable.md) para ser reimplementado.</span><span class="sxs-lookup"><span data-stu-id="47820-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="47820-112">Você pode reimplementar o membro com um nome diferente.</span><span class="sxs-lookup"><span data-stu-id="47820-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="47820-113">A palavra-chave `Implements` pode ser usada nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="47820-113">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="47820-114">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="47820-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="47820-115">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="47820-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="47820-116">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="47820-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="47820-117">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="47820-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="47820-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47820-118">See also</span></span>

- [<span data-ttu-id="47820-119">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="47820-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="47820-120">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="47820-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="47820-121">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="47820-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="47820-122">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="47820-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
