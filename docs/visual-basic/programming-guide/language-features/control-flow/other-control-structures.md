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
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="95446-102">Outras estruturas de controle (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95446-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="95446-103">Visual Basic fornece estruturas de controle que ajudam você a descartar um recurso ou reduzir o número de vezes que você precisa repetir uma referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="95446-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="95446-104">Usando... Terminar usando construção</span><span class="sxs-lookup"><span data-stu-id="95446-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="95446-105">A construção `Using...End Using` estabelece um bloco de instruções no qual você usa um recurso, como uma conexão SQL.</span><span class="sxs-lookup"><span data-stu-id="95446-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="95446-106">Opcionalmente, você pode adquirir o recurso com a instrução `Using`.</span><span class="sxs-lookup"><span data-stu-id="95446-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="95446-107">Quando você sai do bloco de `Using`, Visual Basic descarta automaticamente o recurso para que ele esteja disponível para uso por outro código.</span><span class="sxs-lookup"><span data-stu-id="95446-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="95446-108">O recurso deve ser local e descartável.</span><span class="sxs-lookup"><span data-stu-id="95446-108">The resource must be local and disposable.</span></span> <span data-ttu-id="95446-109">Para obter mais informações, consulte [Instrução using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="95446-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="95446-110">Com... Terminar com construção</span><span class="sxs-lookup"><span data-stu-id="95446-110">With...End With Construction</span></span>  
 <span data-ttu-id="95446-111">A construção `With...End With` permite especificar uma referência de objeto uma vez e, em seguida, executar uma série de instruções que acessam seus membros.</span><span class="sxs-lookup"><span data-stu-id="95446-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="95446-112">Isso pode simplificar seu código e melhorar o desempenho porque Visual Basic não precisa restabelecer a referência para cada instrução que a acessa.</span><span class="sxs-lookup"><span data-stu-id="95446-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="95446-113">Para obter mais informações, consulte [com... Instrução End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="95446-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95446-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95446-114">See also</span></span>

- [<span data-ttu-id="95446-115">Fluxo de Controle</span><span class="sxs-lookup"><span data-stu-id="95446-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="95446-116">Estruturas de Decisão</span><span class="sxs-lookup"><span data-stu-id="95446-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="95446-117">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="95446-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="95446-118">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="95446-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="95446-119">Instrução Using</span><span class="sxs-lookup"><span data-stu-id="95446-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
- [<span data-ttu-id="95446-120">Instrução With ... End With</span><span class="sxs-lookup"><span data-stu-id="95446-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
