---
title: Outras estruturas de controle (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8f8bd57f193be0d7f410f7325355ffc47ab10e3f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="9b754-102">Outras estruturas de controle (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b754-102">Other Control Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="9b754-103">fornece estruturas de controle que ajudam você descartar um recurso ou reduzem o número de vezes que você terá que repetir uma referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="9b754-103"> provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="9b754-104">Usando... End usando a construção</span><span class="sxs-lookup"><span data-stu-id="9b754-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="9b754-105">O `Using...End Using` construção estabelece um bloco de declaração dentro do qual você faz usar de um recurso, como uma conexão SQL.</span><span class="sxs-lookup"><span data-stu-id="9b754-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="9b754-106">Opcionalmente, você pode adquirir o recurso com o `Using` instrução.</span><span class="sxs-lookup"><span data-stu-id="9b754-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="9b754-107">Quando você sai do `Using` bloco, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automaticamente descarta o recurso para que ele esteja disponível para outro código usar.</span><span class="sxs-lookup"><span data-stu-id="9b754-107">When you exit the `Using` block, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="9b754-108">O recurso deve ser local e descartável.</span><span class="sxs-lookup"><span data-stu-id="9b754-108">The resource must be local and disposable.</span></span> <span data-ttu-id="9b754-109">Para obter mais informações, consulte [usando instrução](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9b754-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="9b754-110">Com... Terminar com a construção</span><span class="sxs-lookup"><span data-stu-id="9b754-110">With...End With Construction</span></span>  
 <span data-ttu-id="9b754-111">O `With...End With` construção permite que você especifique uma referência de objeto uma vez e, em seguida, executar uma série de instruções que acessam seus membros.</span><span class="sxs-lookup"><span data-stu-id="9b754-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="9b754-112">Isso pode simplificar o seu código e melhorar o desempenho porque [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não precisa restabelecer a referência para cada instrução que acessa-lo.</span><span class="sxs-lookup"><span data-stu-id="9b754-112">This can simplify your code and improve performance because [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="9b754-113">Para obter mais informações, consulte [com... Terminar com a instrução](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9b754-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b754-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b754-114">See Also</span></span>  
 <span data-ttu-id="9b754-115">[Fluxo de controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span><span class="sxs-lookup"><span data-stu-id="9b754-115">[Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span></span>  
<span data-ttu-id="9b754-116"> [Estruturas de decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span><span class="sxs-lookup"><span data-stu-id="9b754-116"> [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span></span>  
<span data-ttu-id="9b754-117"> [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="9b754-117"> [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="9b754-118"> [Estruturas de controle aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="9b754-118"> [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span></span>  
<span data-ttu-id="9b754-119"> [Instrução Using](../../../../visual-basic/language-reference/statements/using-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9b754-119"> [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md) </span></span>  
<span data-ttu-id="9b754-120"> [Instrução With ... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span><span class="sxs-lookup"><span data-stu-id="9b754-120"> [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span></span>
