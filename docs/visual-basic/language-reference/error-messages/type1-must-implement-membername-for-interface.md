---
title: <type1>'<typename>' deve implementar '<membername>' para interface '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 4ffe18e11c388a8c69ef0592bde1b78f5b219680
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386848"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="d939c-102">\<type1>'\<typename>' deve implementar '\<membername>' para interface '\<interfacename>'</span><span class="sxs-lookup"><span data-stu-id="d939c-102">\<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="d939c-103">' \<typename> ' deve implementar ' \<membername> ' para a interface ' \<interfacename> '.</span><span class="sxs-lookup"><span data-stu-id="d939c-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="d939c-104">A implementação da propriedade deve ter especificadores ' ReadOnly '/' WriteOnly ' correspondentes.</span><span class="sxs-lookup"><span data-stu-id="d939c-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="d939c-105">Declarações de classe ou estrutura para implementar uma interface, mas não implementa um procedimento, propriedade ou evento definido pela interface.</span><span class="sxs-lookup"><span data-stu-id="d939c-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="d939c-106">Todos os membros da interface devem ser implementados.</span><span class="sxs-lookup"><span data-stu-id="d939c-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="d939c-107">**ID do erro:** BC30154</span><span class="sxs-lookup"><span data-stu-id="d939c-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d939c-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d939c-108">To correct this error</span></span>  
  
1. <span data-ttu-id="d939c-109">Declare um membro com o mesmo nome e assinatura, conforme definido na interface.</span><span class="sxs-lookup"><span data-stu-id="d939c-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="d939c-110">Certifique-se de incluir pelo menos `End Function` a `End Sub` instrução, ou `End Property` .</span><span class="sxs-lookup"><span data-stu-id="d939c-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2. <span data-ttu-id="d939c-111">Adicione uma `Implements` cláusula ao final da `Function` instrução,, `Sub` `Property` ou `Event` .</span><span class="sxs-lookup"><span data-stu-id="d939c-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="d939c-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d939c-112">For example:</span></span>  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. <span data-ttu-id="d939c-113">Ao implementar uma propriedade, verifique se o `ReadOnly` ou o `WriteOnly` é usado da mesma maneira que na definição da interface.</span><span class="sxs-lookup"><span data-stu-id="d939c-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4. <span data-ttu-id="d939c-114">Ao implementar uma propriedade, declare `Get` e `Set` procedimentos, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="d939c-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d939c-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="d939c-115">See also</span></span>

- [<span data-ttu-id="d939c-116">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="d939c-116">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="d939c-117">Interfaces</span><span class="sxs-lookup"><span data-stu-id="d939c-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
