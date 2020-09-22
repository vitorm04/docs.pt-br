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
ms.openlocfilehash: 7c95cf76b1bac24e2a0f20857b8984d54ebbea85
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866167"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="07648-102">Cláusula Implements (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07648-102">Implements Clause (Visual Basic)</span></span>

<span data-ttu-id="07648-103">Indica que um membro de classe ou estrutura está fornecendo a implementação para um membro definido em uma interface.</span><span class="sxs-lookup"><span data-stu-id="07648-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07648-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="07648-104">Remarks</span></span>  

<span data-ttu-id="07648-105">A `Implements` palavra-chave não é a mesma que a [instrução Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="07648-105">The `Implements` keyword is not the same as the [Implements Statement](implements-statement.md).</span></span> <span data-ttu-id="07648-106">Você usa a `Implements` instrução para especificar que uma classe ou estrutura implementa uma ou mais interfaces e, em seguida, para cada membro, você usa a `Implements` palavra-chave para especificar qual interface e qual membro ele implementa.</span><span class="sxs-lookup"><span data-stu-id="07648-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="07648-107">Se uma classe ou estrutura implementa uma interface, ela deve incluir a `Implements` instrução imediatamente após a [instrução de classe](class-statement.md) ou a [instrução de estrutura](structure-statement.md)e deve implementar todos os membros definidos pela interface.</span><span class="sxs-lookup"><span data-stu-id="07648-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](class-statement.md) or [Structure Statement](structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="07648-108">Reimplementação</span><span class="sxs-lookup"><span data-stu-id="07648-108">Reimplementation</span></span>  

<span data-ttu-id="07648-109">Em uma classe derivada, você pode reimplementar um membro de interface que a classe base já tenha implementado.</span><span class="sxs-lookup"><span data-stu-id="07648-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="07648-110">Isso é diferente de substituir o membro da classe base nos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="07648-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="07648-111">O membro da classe base não precisa ser [substituível](../modifiers/overridable.md) para ser reimplementado.</span><span class="sxs-lookup"><span data-stu-id="07648-111">The base class member does not need to be [Overridable](../modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="07648-112">Você pode reimplementar o membro com um nome diferente.</span><span class="sxs-lookup"><span data-stu-id="07648-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="07648-113">A `Implements` palavra-chave pode ser usada nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="07648-113">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="07648-114">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="07648-114">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="07648-115">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="07648-115">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="07648-116">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="07648-116">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="07648-117">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="07648-117">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="07648-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="07648-118">See also</span></span>

- [<span data-ttu-id="07648-119">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="07648-119">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="07648-120">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="07648-120">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="07648-121">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="07648-121">Class Statement</span></span>](class-statement.md)
- [<span data-ttu-id="07648-122">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="07648-122">Structure Statement</span></span>](structure-statement.md)
