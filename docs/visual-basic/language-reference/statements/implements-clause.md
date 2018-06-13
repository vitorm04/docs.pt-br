---
title: Cláusula Implements (Visual Basic)
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
ms.openlocfilehash: 1e34245ac528e9e2463afbfd07dff91bf693830b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603399"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="77227-102">Cláusula Implements (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77227-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="77227-103">Indica que um membro de classe ou estrutura está fornecendo a implementação de um membro definido em uma interface.</span><span class="sxs-lookup"><span data-stu-id="77227-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77227-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="77227-104">Remarks</span></span>  
<span data-ttu-id="77227-105">O `Implements` palavra-chave não é igual a [instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="77227-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="77227-106">Você usa o `Implements` instrução para especificar que uma classe ou estrutura implementa uma ou mais interfaces, e, em seguida, para cada membro que você usar o `Implements` palavra-chave para especificar qual interface e qual membro ele implementa.</span><span class="sxs-lookup"><span data-stu-id="77227-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="77227-107">Se uma classe ou estrutura implementa uma interface, ele deve incluir o `Implements` instrução imediatamente após o [instrução Class](../../../visual-basic/language-reference/statements/class-statement.md) ou [instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md), e ela deve implementar todos os membros definidos pela interface.</span><span class="sxs-lookup"><span data-stu-id="77227-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="77227-108">Reimplementação</span><span class="sxs-lookup"><span data-stu-id="77227-108">Reimplementation</span></span>  
<span data-ttu-id="77227-109">Em uma classe derivada, você pode reimplementar um membro de interface que a classe base já tenha implementado.</span><span class="sxs-lookup"><span data-stu-id="77227-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="77227-110">Isso é diferente de substituir o membro de classe base nos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="77227-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="77227-111">O membro de classe base não precisa ser [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) para ser reimplementado.</span><span class="sxs-lookup"><span data-stu-id="77227-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="77227-112">Você pode reimplementar o membro com um nome diferente.</span><span class="sxs-lookup"><span data-stu-id="77227-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="77227-113">O `Implements` palavra-chave pode ser usada nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="77227-113">The `Implements` keyword can be used in the following contexts:</span></span>
- [<span data-ttu-id="77227-114">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="77227-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="77227-115">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="77227-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="77227-116">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="77227-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="77227-117">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="77227-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="77227-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77227-118">See Also</span></span>  
 [<span data-ttu-id="77227-119">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="77227-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="77227-120">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="77227-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="77227-121">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="77227-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="77227-122">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="77227-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
