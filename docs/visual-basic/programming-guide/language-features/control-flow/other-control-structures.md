---
title: Outras estruturas de controle (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e1ea44cf2f0405dc55f8df60fb842691e50a9a0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="77e59-102">Outras estruturas de controle (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77e59-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="77e59-103">Visual Basic fornece estruturas de controle que ajudam você descartar um recurso ou reduzem o número de vezes que você precisa repetir uma referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="77e59-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="77e59-104">Usando... Usando a construção de término</span><span class="sxs-lookup"><span data-stu-id="77e59-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="77e59-105">O `Using...End Using` construção estabelece um bloco de instruções dentro do qual você faz uso de um recurso como uma conexão SQL.</span><span class="sxs-lookup"><span data-stu-id="77e59-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="77e59-106">Opcionalmente, você pode adquirir o recurso com o `Using` instrução.</span><span class="sxs-lookup"><span data-stu-id="77e59-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="77e59-107">Quando você fechar o `Using` bloco, Visual Basic descarta automaticamente do recurso para que ele está disponível para outro código usar.</span><span class="sxs-lookup"><span data-stu-id="77e59-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="77e59-108">O recurso deve ser local e descartável.</span><span class="sxs-lookup"><span data-stu-id="77e59-108">The resource must be local and disposable.</span></span> <span data-ttu-id="77e59-109">Para obter mais informações, consulte [Instrução using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="77e59-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="77e59-110">Com... Terminar com a construção</span><span class="sxs-lookup"><span data-stu-id="77e59-110">With...End With Construction</span></span>  
 <span data-ttu-id="77e59-111">O `With...End With` construção permite que você especifique uma referência de objeto uma vez e, em seguida, executar uma série de instruções que acessam seus membros.</span><span class="sxs-lookup"><span data-stu-id="77e59-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="77e59-112">Isso pode simplificar seu código e melhorar o desempenho porque o Visual Basic não precisa restabelecer a referência para cada instrução que acessa-lo.</span><span class="sxs-lookup"><span data-stu-id="77e59-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="77e59-113">Para obter mais informações, consulte [com... Terminar com a instrução](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="77e59-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e59-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77e59-114">See Also</span></span>  
 [<span data-ttu-id="77e59-115">Fluxo de Controle</span><span class="sxs-lookup"><span data-stu-id="77e59-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="77e59-116">Estruturas de Decisão</span><span class="sxs-lookup"><span data-stu-id="77e59-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="77e59-117">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="77e59-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="77e59-118">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="77e59-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="77e59-119">Instrução Using</span><span class="sxs-lookup"><span data-stu-id="77e59-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)  
 [<span data-ttu-id="77e59-120">Instrução With ... End With</span><span class="sxs-lookup"><span data-stu-id="77e59-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
