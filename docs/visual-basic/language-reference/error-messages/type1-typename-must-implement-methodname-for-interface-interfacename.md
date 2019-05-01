---
title: <type1>'<typename>'deve implementar'<methodname>'para interface'<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 432f089bc77928308820d7456d930fba8dc513f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013602"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="8751a-102">\<type1 >'\<typename >' deve implementar '\<methodname >' para interface '\<interfacename >'</span><span class="sxs-lookup"><span data-stu-id="8751a-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="8751a-103">Uma classe ou estrutura para implementar uma interface de declarações, mas não implementa um procedimento definido pela interface.</span><span class="sxs-lookup"><span data-stu-id="8751a-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="8751a-104">Todos os membros da interface devem ser implementado.</span><span class="sxs-lookup"><span data-stu-id="8751a-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="8751a-105">**ID do erro:** BC30149</span><span class="sxs-lookup"><span data-stu-id="8751a-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8751a-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8751a-106">To correct this error</span></span>  
  
1. <span data-ttu-id="8751a-107">Declara um procedimento com o mesmo nome e assinatura, conforme definido na interface.</span><span class="sxs-lookup"><span data-stu-id="8751a-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="8751a-108">Não se esqueça de incluir pelo menos o `End Function` ou `End Sub` instrução.</span><span class="sxs-lookup"><span data-stu-id="8751a-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="8751a-109">Adicionar um `Implements` cláusula no final dos `Function` ou `Sub` instrução.</span><span class="sxs-lookup"><span data-stu-id="8751a-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="8751a-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8751a-110">For example:</span></span>  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8751a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8751a-111">See also</span></span>

- [<span data-ttu-id="8751a-112">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="8751a-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="8751a-113">Interfaces</span><span class="sxs-lookup"><span data-stu-id="8751a-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
