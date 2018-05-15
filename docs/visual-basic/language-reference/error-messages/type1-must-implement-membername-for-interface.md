---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39; deve implementar &#39; &lt;membername&gt; &#39; para interface &#39; &lt;interfacename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 0f93bd137bdc21268cbca139ae739843561350ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="f90e2-102">&lt;type1&gt;&#39;&lt;typename&gt; &#39; deve implementar &#39; &lt;membername&gt; &#39; para interface &#39; &lt;interfacename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="f90e2-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="f90e2-103">'\<typename >' deve implementar '\<membername >' para interface '\<interfacename >'.</span><span class="sxs-lookup"><span data-stu-id="f90e2-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="f90e2-104">Propriedade de implementação deve ter 'ReadOnly' / 'WriteOnly' especificadores.</span><span class="sxs-lookup"><span data-stu-id="f90e2-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="f90e2-105">Uma classe ou estrutura alega implementar uma interface mas não implementa um procedimento, propriedade ou evento definido pela interface.</span><span class="sxs-lookup"><span data-stu-id="f90e2-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="f90e2-106">Cada membro da interface deve ser implementado.</span><span class="sxs-lookup"><span data-stu-id="f90e2-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="f90e2-107">**ID do erro:** BC30154</span><span class="sxs-lookup"><span data-stu-id="f90e2-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f90e2-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f90e2-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="f90e2-109">Declare um membro com o mesmo nome e assinatura, conforme definido na interface.</span><span class="sxs-lookup"><span data-stu-id="f90e2-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="f90e2-110">Certifique-se de incluir pelo menos o `End Function`, `End Sub`, ou `End Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="f90e2-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="f90e2-111">Adicionar uma `Implements` cláusula ao final do `Function`, `Sub`, `Property`, ou `Event` instrução.</span><span class="sxs-lookup"><span data-stu-id="f90e2-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="f90e2-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f90e2-112">For example:</span></span>  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  <span data-ttu-id="f90e2-113">Ao implementar uma propriedade, certifique-se de que `ReadOnly` ou `WriteOnly` é usado da mesma maneira como a definição da interface.</span><span class="sxs-lookup"><span data-stu-id="f90e2-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4.  <span data-ttu-id="f90e2-114">Quando estiver implementando uma propriedade, declare `Get` e `Set` procedimentos, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="f90e2-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f90e2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f90e2-115">See Also</span></span>  
 [<span data-ttu-id="f90e2-116">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="f90e2-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="f90e2-117">Interfaces</span><span class="sxs-lookup"><span data-stu-id="f90e2-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
