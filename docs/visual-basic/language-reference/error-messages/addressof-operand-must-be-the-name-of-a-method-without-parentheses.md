---
title: O operando 'AddressOf' deve ter o mesmo nome de um método (sem parênteses)
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: b8c67c2390df91c6a4af66e020365544e6bf369b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323818"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="cf908-102">O operando 'AddressOf' deve ter o mesmo nome de um método (sem parênteses)</span><span class="sxs-lookup"><span data-stu-id="cf908-102">'AddressOf' operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="cf908-103">O `AddressOf` operador cria uma instância de procedimento delegado que faz referência a um procedimento específico.</span><span class="sxs-lookup"><span data-stu-id="cf908-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="cf908-104">A sintaxe é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="cf908-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="cf908-105">`AddressOf` `procedurename`</span><span class="sxs-lookup"><span data-stu-id="cf908-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="cf908-106">Você inseriu o seguinte argumento entre parênteses `AddressOf`, em que nenhuma é necessária.</span><span class="sxs-lookup"><span data-stu-id="cf908-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="cf908-107">**ID do erro:** BC30577</span><span class="sxs-lookup"><span data-stu-id="cf908-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cf908-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="cf908-108">To correct this error</span></span>  
  
1. <span data-ttu-id="cf908-109">Remova os parênteses que delimitam o seguinte argumento `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="cf908-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2. <span data-ttu-id="cf908-110">Verifique se que o argumento é um nome de método.</span><span class="sxs-lookup"><span data-stu-id="cf908-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf908-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf908-111">See also</span></span>

- [<span data-ttu-id="cf908-112">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="cf908-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="cf908-113">Delegados</span><span class="sxs-lookup"><span data-stu-id="cf908-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
