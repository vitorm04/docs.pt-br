---
title: Classe Delegate '<classname>' não tem nenhum método Invoke. Portanto, uma expressão desse tipo não pode ser o destino de uma chamada de método
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 8339d038f845b8568f31f3068a98ccccf580aeae
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286644"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="9ed3d-102">Classe delegate\<classname >' não tem método Invoke, portanto, uma expressão desse tipo não pode ser o destino de uma chamada de método</span><span class="sxs-lookup"><span data-stu-id="9ed3d-102">Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="9ed3d-103">Uma chamada para `Invoke` através de um delegado falhou porque `Invoke` não está implementado na classe de delegado.</span><span class="sxs-lookup"><span data-stu-id="9ed3d-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="9ed3d-104">**ID do erro:** BC30220</span><span class="sxs-lookup"><span data-stu-id="9ed3d-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9ed3d-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9ed3d-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="9ed3d-106">Certifique-se de que uma instância da classe de delegado foi criada com uma `Dim` instrução e que um procedimento foi designado para a instância de delegado com o `AddressOf` operador.</span><span class="sxs-lookup"><span data-stu-id="9ed3d-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2.  <span data-ttu-id="9ed3d-107">Localize o código que implementa a classe delegada e verifique se ele implementa o `Invoke` procedimento.</span><span class="sxs-lookup"><span data-stu-id="9ed3d-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed3d-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ed3d-108">See also</span></span>
- [<span data-ttu-id="9ed3d-109">Delegados</span><span class="sxs-lookup"><span data-stu-id="9ed3d-109">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="9ed3d-110">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="9ed3d-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="9ed3d-111">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="9ed3d-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="9ed3d-112">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="9ed3d-112">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
