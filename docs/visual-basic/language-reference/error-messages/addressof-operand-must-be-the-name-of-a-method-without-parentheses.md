---
title: '&#39;AddressOf&#39; operando deve ser o nome de um método (sem parênteses)'
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 701d86e03d9b14236eec8436d99ec40cebbbcd44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="fbe92-102">&#39;AddressOf&#39; operando deve ser o nome de um método (sem parênteses)</span><span class="sxs-lookup"><span data-stu-id="fbe92-102">&#39;AddressOf&#39; operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="fbe92-103">O `AddressOf` operador cria uma instância de delegado de procedimento que faz referência a um procedimento específico.</span><span class="sxs-lookup"><span data-stu-id="fbe92-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="fbe92-104">A sintaxe é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="fbe92-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="fbe92-105">`AddressOf` `procedurename`</span><span class="sxs-lookup"><span data-stu-id="fbe92-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="fbe92-106">Você inseriu o seguinte argumento entre parênteses `AddressOf`, onde nenhuma é necessária.</span><span class="sxs-lookup"><span data-stu-id="fbe92-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="fbe92-107">**ID do erro:** BC30577</span><span class="sxs-lookup"><span data-stu-id="fbe92-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fbe92-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="fbe92-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="fbe92-109">Remova os parênteses que delimitam o seguinte argumento `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="fbe92-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="fbe92-110">Verifique se que o argumento é um nome de método.</span><span class="sxs-lookup"><span data-stu-id="fbe92-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbe92-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbe92-111">See Also</span></span>  
 [<span data-ttu-id="fbe92-112">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="fbe92-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="fbe92-113">Delegados</span><span class="sxs-lookup"><span data-stu-id="fbe92-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
