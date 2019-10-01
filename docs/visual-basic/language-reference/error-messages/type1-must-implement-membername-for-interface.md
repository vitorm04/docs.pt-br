---
title: <type1>'<typename>' deve implementar '<membername>' para interface '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: a824b66eaad964049ced5cae5eb2cc370d00ba7f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696889"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="7ff2d-102">\<type1 > ' \<typename > ' deve implementar ' \<membername > ' para a interface ' \<interfacename > '</span><span class="sxs-lookup"><span data-stu-id="7ff2d-102">\<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="7ff2d-103">' \<typename > ' deve implementar ' \<membername > ' para a interface ' \<interfacename > '.</span><span class="sxs-lookup"><span data-stu-id="7ff2d-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="7ff2d-104">A implementação da propriedade deve ter especificadores ' ReadOnly '/' WriteOnly ' correspondentes.</span><span class="sxs-lookup"><span data-stu-id="7ff2d-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="7ff2d-105">Declarações de classe ou estrutura para implementar uma interface, mas não implementa um procedimento, propriedade ou evento definido pela interface.</span><span class="sxs-lookup"><span data-stu-id="7ff2d-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="7ff2d-106">Todos os membros da interface devem ser implementados.</span><span class="sxs-lookup"><span data-stu-id="7ff2d-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="7ff2d-107">**ID do erro:** BC30154</span><span class="sxs-lookup"><span data-stu-id="7ff2d-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7ff2d-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7ff2d-108">To correct this error</span></span>  
  
1. <span data-ttu-id="7ff2d-109">Declare um membro com o mesmo nome e assinatura, conforme definido na interface.</span><span class="sxs-lookup"><span data-stu-id="7ff2d-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="7ff2d-110">Certifique-se de incluir pelo menos a instrução `End Function`, `End Sub` ou `End Property`.</span><span class="sxs-lookup"><span data-stu-id="7ff2d-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2. <span data-ttu-id="7ff2d-111">Adicione uma cláusula `Implements` ao final da instrução `Function`, `Sub`, `Property` ou `Event`.</span><span class="sxs-lookup"><span data-stu-id="7ff2d-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="7ff2d-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7ff2d-112">For example:</span></span>  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. <span data-ttu-id="7ff2d-113">Ao implementar uma propriedade, certifique-se de que `ReadOnly` ou `WriteOnly` seja usado da mesma maneira como na definição da interface.</span><span class="sxs-lookup"><span data-stu-id="7ff2d-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4. <span data-ttu-id="7ff2d-114">Ao implementar uma propriedade, declare os procedimentos `Get` e `Set`, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="7ff2d-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff2d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ff2d-115">See also</span></span>

- [<span data-ttu-id="7ff2d-116">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="7ff2d-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="7ff2d-117">Interfaces</span><span class="sxs-lookup"><span data-stu-id="7ff2d-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
