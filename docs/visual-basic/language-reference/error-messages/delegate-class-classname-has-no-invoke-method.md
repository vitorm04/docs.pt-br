---
title: Classe Delegate '<classname>' não tem nenhum método Invoke. Portanto, uma expressão desse tipo não pode ser o destino de uma chamada de método
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 27be97ba2930791bcb9012c824bc418a0089b037
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409706"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="219e8-102">Classe Delegate '\<classname>' não tem nenhum método Invoke. Portanto, uma expressão desse tipo não pode ser o destino de uma chamada de método</span><span class="sxs-lookup"><span data-stu-id="219e8-102">Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="219e8-103">Uma chamada para `Invoke` por meio de um delegado falhou porque `Invoke` não está implementada na classe delegate.</span><span class="sxs-lookup"><span data-stu-id="219e8-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="219e8-104">**ID do erro:** BC30220</span><span class="sxs-lookup"><span data-stu-id="219e8-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="219e8-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="219e8-105">To correct this error</span></span>  
  
1. <span data-ttu-id="219e8-106">Certifique-se de que uma instância da classe delegate tenha sido criada com uma `Dim` instrução e que um procedimento tenha sido atribuído à instância delegada com o `AddressOf` operador.</span><span class="sxs-lookup"><span data-stu-id="219e8-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2. <span data-ttu-id="219e8-107">Localize o código que implementa a classe delegada e verifique se ele implementa o `Invoke` procedimento.</span><span class="sxs-lookup"><span data-stu-id="219e8-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="219e8-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="219e8-108">See also</span></span>

- [<span data-ttu-id="219e8-109">Delegados</span><span class="sxs-lookup"><span data-stu-id="219e8-109">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="219e8-110">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="219e8-110">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="219e8-111">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="219e8-111">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="219e8-112">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="219e8-112">Dim Statement</span></span>](../statements/dim-statement.md)
