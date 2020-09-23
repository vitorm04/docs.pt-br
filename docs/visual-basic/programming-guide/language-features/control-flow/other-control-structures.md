---
title: Outras estruturas de controle
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 8e7ca699e532ac7cfbe7918d850e7a28d1b27bcf
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058606"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="009e4-102">Outras estruturas de controle (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="009e4-102">Other Control Structures (Visual Basic)</span></span>

<span data-ttu-id="009e4-103">Visual Basic fornece estruturas de controle que ajudam você a descartar um recurso ou reduzir o número de vezes que você precisa repetir uma referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="009e4-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="009e4-104">Usando... Terminar usando construção</span><span class="sxs-lookup"><span data-stu-id="009e4-104">Using...End Using Construction</span></span>  

 <span data-ttu-id="009e4-105">A `Using...End Using` construção estabelece um bloco de instruções no qual você faz uso de um recurso, como uma conexão SQL.</span><span class="sxs-lookup"><span data-stu-id="009e4-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="009e4-106">Opcionalmente, você pode adquirir o recurso com a `Using` instrução.</span><span class="sxs-lookup"><span data-stu-id="009e4-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="009e4-107">Quando você sai do `Using` bloco, Visual Basic descarta automaticamente o recurso para que ele esteja disponível para uso por outro código.</span><span class="sxs-lookup"><span data-stu-id="009e4-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="009e4-108">O recurso deve ser local e descartável.</span><span class="sxs-lookup"><span data-stu-id="009e4-108">The resource must be local and disposable.</span></span> <span data-ttu-id="009e4-109">Para obter mais informações, consulte [usando a instrução](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="009e4-109">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="009e4-110">Com... Terminar com construção</span><span class="sxs-lookup"><span data-stu-id="009e4-110">With...End With Construction</span></span>  

 <span data-ttu-id="009e4-111">A `With...End With` construção permite especificar uma referência de objeto uma vez e, em seguida, executar uma série de instruções que acessam seus membros.</span><span class="sxs-lookup"><span data-stu-id="009e4-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="009e4-112">Isso pode simplificar seu código e melhorar o desempenho porque Visual Basic não precisa restabelecer a referência para cada instrução que a acessa.</span><span class="sxs-lookup"><span data-stu-id="009e4-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="009e4-113">Para obter mais informações, consulte [com... Instrução End With](../../../language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="009e4-113">For more information, see [With...End With Statement](../../../language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="009e4-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="009e4-114">See also</span></span>

- [<span data-ttu-id="009e4-115">Fluxo de Controle</span><span class="sxs-lookup"><span data-stu-id="009e4-115">Control Flow</span></span>](index.md)
- [<span data-ttu-id="009e4-116">Estruturas de Decisão</span><span class="sxs-lookup"><span data-stu-id="009e4-116">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="009e4-117">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="009e4-117">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="009e4-118">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="009e4-118">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="009e4-119">Instrução using</span><span class="sxs-lookup"><span data-stu-id="009e4-119">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
- [<span data-ttu-id="009e4-120">Instrução With...End With</span><span class="sxs-lookup"><span data-stu-id="009e4-120">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
