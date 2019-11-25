---
title: Outras estruturas de controle
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 758df361f421684655147ae288af3f350e53c4d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348129"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="d3d78-102">Outras estruturas de controle (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3d78-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="d3d78-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span><span class="sxs-lookup"><span data-stu-id="d3d78-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="d3d78-104">Using...End Using Construction</span><span class="sxs-lookup"><span data-stu-id="d3d78-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="d3d78-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span><span class="sxs-lookup"><span data-stu-id="d3d78-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="d3d78-106">You can optionally acquire the resource with the `Using` statement.</span><span class="sxs-lookup"><span data-stu-id="d3d78-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="d3d78-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span><span class="sxs-lookup"><span data-stu-id="d3d78-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="d3d78-108">The resource must be local and disposable.</span><span class="sxs-lookup"><span data-stu-id="d3d78-108">The resource must be local and disposable.</span></span> <span data-ttu-id="d3d78-109">Para obter mais informações, consulte [Instrução using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d3d78-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="d3d78-110">With...End With Construction</span><span class="sxs-lookup"><span data-stu-id="d3d78-110">With...End With Construction</span></span>  
 <span data-ttu-id="d3d78-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span><span class="sxs-lookup"><span data-stu-id="d3d78-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="d3d78-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span><span class="sxs-lookup"><span data-stu-id="d3d78-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="d3d78-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d3d78-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d78-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3d78-114">See also</span></span>

- [<span data-ttu-id="d3d78-115">Fluxo de Controle</span><span class="sxs-lookup"><span data-stu-id="d3d78-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="d3d78-116">Estruturas de Decisão</span><span class="sxs-lookup"><span data-stu-id="d3d78-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="d3d78-117">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="d3d78-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="d3d78-118">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="d3d78-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="d3d78-119">Instrução Using</span><span class="sxs-lookup"><span data-stu-id="d3d78-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
- [<span data-ttu-id="d3d78-120">Instrução With ... End With</span><span class="sxs-lookup"><span data-stu-id="d3d78-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
