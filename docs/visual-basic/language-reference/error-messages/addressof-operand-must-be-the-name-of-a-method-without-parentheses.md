---
title: O operando 'AddressOf' deve ter o mesmo nome de um método (sem parênteses)
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 37b02ab76730458b757835fda37b8cb145ed93ad
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262108"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="e80b5-102">O operando 'AddressOf' deve ter o mesmo nome de um método (sem parênteses)</span><span class="sxs-lookup"><span data-stu-id="e80b5-102">'AddressOf' operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="e80b5-103">O `AddressOf` operador cria uma instância de procedimento delegado que faz referência a um procedimento específico.</span><span class="sxs-lookup"><span data-stu-id="e80b5-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="e80b5-104">A sintaxe é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="e80b5-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="e80b5-105">`AddressOf` `procedurename`</span><span class="sxs-lookup"><span data-stu-id="e80b5-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="e80b5-106">Você inseriu o seguinte argumento entre parênteses `AddressOf`, em que nenhuma é necessária.</span><span class="sxs-lookup"><span data-stu-id="e80b5-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="e80b5-107">**ID do erro:** BC30577</span><span class="sxs-lookup"><span data-stu-id="e80b5-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e80b5-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e80b5-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="e80b5-109">Remova os parênteses que delimitam o seguinte argumento `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="e80b5-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="e80b5-110">Verifique se que o argumento é um nome de método.</span><span class="sxs-lookup"><span data-stu-id="e80b5-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e80b5-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e80b5-111">See also</span></span>
- [<span data-ttu-id="e80b5-112">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="e80b5-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="e80b5-113">Delegados</span><span class="sxs-lookup"><span data-stu-id="e80b5-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
