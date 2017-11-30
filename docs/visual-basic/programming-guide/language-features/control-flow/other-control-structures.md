---
title: Outras estruturas de controle (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09e59d25b3b2fc89026295e8500c30dad7b75086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="8600b-102">Outras estruturas de controle (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8600b-102">Other Control Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="8600b-103">Fornece as estruturas de controle que ajudam você descartar um recurso ou reduzem o número de vezes que você precisa repetir uma referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="8600b-103"> provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="8600b-104">Usando... Usando a construção de término</span><span class="sxs-lookup"><span data-stu-id="8600b-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="8600b-105">O `Using...End Using` construção estabelece um bloco de instruções dentro do qual você faz uso de um recurso como uma conexão SQL.</span><span class="sxs-lookup"><span data-stu-id="8600b-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="8600b-106">Opcionalmente, você pode adquirir o recurso com o `Using` instrução.</span><span class="sxs-lookup"><span data-stu-id="8600b-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="8600b-107">Quando você fechar o `Using` bloco, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] descarta automaticamente o recurso para que ele está disponível para outro código usar.</span><span class="sxs-lookup"><span data-stu-id="8600b-107">When you exit the `Using` block, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="8600b-108">O recurso deve ser local e descartável.</span><span class="sxs-lookup"><span data-stu-id="8600b-108">The resource must be local and disposable.</span></span> <span data-ttu-id="8600b-109">Para obter mais informações, consulte [Instrução using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8600b-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="8600b-110">Com... Terminar com a construção</span><span class="sxs-lookup"><span data-stu-id="8600b-110">With...End With Construction</span></span>  
 <span data-ttu-id="8600b-111">O `With...End With` construção permite que você especifique uma referência de objeto uma vez e, em seguida, executar uma série de instruções que acessam seus membros.</span><span class="sxs-lookup"><span data-stu-id="8600b-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="8600b-112">Isso pode simplificar o seu código e melhorar o desempenho porque [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] não precisa restabelecer a referência para cada instrução que acessa-lo.</span><span class="sxs-lookup"><span data-stu-id="8600b-112">This can simplify your code and improve performance because [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="8600b-113">Para obter mais informações, consulte [com... Terminar com a instrução](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8600b-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8600b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8600b-114">See Also</span></span>  
 [<span data-ttu-id="8600b-115">Fluxo de Controle</span><span class="sxs-lookup"><span data-stu-id="8600b-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="8600b-116">Estruturas de Decisão</span><span class="sxs-lookup"><span data-stu-id="8600b-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="8600b-117">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="8600b-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="8600b-118">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="8600b-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="8600b-119">Instrução Using</span><span class="sxs-lookup"><span data-stu-id="8600b-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)  
 [<span data-ttu-id="8600b-120">Instrução With ... End With</span><span class="sxs-lookup"><span data-stu-id="8600b-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
