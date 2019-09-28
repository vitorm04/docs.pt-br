---
title: <type1>'<typename>' deve implementar '<methodname>' para interface '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c387b0225375f4675042bef593b23a084305b4fd
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591591"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="97b80-102">\<type1 > ' \<typename > ' deve implementar ' \<methodname > ' para a interface ' \<interfacename > '</span><span class="sxs-lookup"><span data-stu-id="97b80-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="97b80-103">Uma classe ou estrutura alega implementar uma interface, mas não implementa um procedimento definido pela interface.</span><span class="sxs-lookup"><span data-stu-id="97b80-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="97b80-104">Todos os membros da interface devem ser implementados.</span><span class="sxs-lookup"><span data-stu-id="97b80-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="97b80-105">**ID do erro:** BC30149</span><span class="sxs-lookup"><span data-stu-id="97b80-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="97b80-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="97b80-106">To correct this error</span></span>  
  
1. <span data-ttu-id="97b80-107">Declare um procedimento com o mesmo nome e assinatura, conforme definido na interface.</span><span class="sxs-lookup"><span data-stu-id="97b80-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="97b80-108">Certifique-se de incluir pelo menos a instrução `End Function` ou `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="97b80-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="97b80-109">Adicione uma cláusula `Implements` ao final da instrução `Function` ou `Sub`.</span><span class="sxs-lookup"><span data-stu-id="97b80-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="97b80-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="97b80-110">For example:</span></span>  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="97b80-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97b80-111">See also</span></span>

- [<span data-ttu-id="97b80-112">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="97b80-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="97b80-113">Interfaces</span><span class="sxs-lookup"><span data-stu-id="97b80-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
