---
title: <type1>'<typename>'deve implementar'<membername>'para interface'<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 86b0d46e0e27b2fd8d1fccb37f4a3c45e95f5f63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792087"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="fe95f-102">\<type1 >'\<typename >' deve implementar '\<membername >' para interface '\<interfacename >'</span><span class="sxs-lookup"><span data-stu-id="fe95f-102">\<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="fe95f-103">'\<typename >' deve implementar '\<membername >' para interface '\<interfacename >'.</span><span class="sxs-lookup"><span data-stu-id="fe95f-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="fe95f-104">Implementação de propriedade deve ter 'ReadOnly' / 'WriteOnly' especificadores.</span><span class="sxs-lookup"><span data-stu-id="fe95f-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="fe95f-105">Uma classe ou estrutura para implementar uma interface de declarações, mas não implementa um procedimento, propriedade ou evento definido pela interface.</span><span class="sxs-lookup"><span data-stu-id="fe95f-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="fe95f-106">Todos os membros da interface devem ser implementado.</span><span class="sxs-lookup"><span data-stu-id="fe95f-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="fe95f-107">**ID do erro:** BC30154</span><span class="sxs-lookup"><span data-stu-id="fe95f-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fe95f-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="fe95f-108">To correct this error</span></span>  
  
1. <span data-ttu-id="fe95f-109">Declare um membro com o mesmo nome e assinatura, conforme definido na interface.</span><span class="sxs-lookup"><span data-stu-id="fe95f-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="fe95f-110">Não se esqueça de incluir pelo menos o `End Function`, `End Sub`, ou `End Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="fe95f-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2. <span data-ttu-id="fe95f-111">Adicionar um `Implements` cláusula no final dos `Function`, `Sub`, `Property`, ou `Event` instrução.</span><span class="sxs-lookup"><span data-stu-id="fe95f-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="fe95f-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="fe95f-112">For example:</span></span>  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. <span data-ttu-id="fe95f-113">Ao implementar uma propriedade, certifique-se de que `ReadOnly` ou `WriteOnly` é usado da mesma forma como a definição de interface.</span><span class="sxs-lookup"><span data-stu-id="fe95f-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4. <span data-ttu-id="fe95f-114">Quando estiver implementando uma propriedade, declare `Get` e `Set` procedimentos, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="fe95f-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe95f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe95f-115">See also</span></span>

- [<span data-ttu-id="fe95f-116">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="fe95f-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="fe95f-117">Interfaces</span><span class="sxs-lookup"><span data-stu-id="fe95f-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
