---
title: <type1>'<typename>' deve implementar '<membername>' para interface '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: a036097d778daae59ef3bbd74ab8507cd16e6e24
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161849"
---
# <a name="bc30154-type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="4c4c3-102">BC30154: \<type1> ' \<typename> ' deve implementar ' \<membername> ' para a interface ' \<interfacename> '</span><span class="sxs-lookup"><span data-stu-id="4c4c3-102">BC30154: \<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="4c4c3-103">' \<typename> ' deve implementar ' \<membername> ' para a interface ' \<interfacename> '.</span><span class="sxs-lookup"><span data-stu-id="4c4c3-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="4c4c3-104">A implementação da propriedade deve ter especificadores ' ReadOnly '/' WriteOnly ' correspondentes.</span><span class="sxs-lookup"><span data-stu-id="4c4c3-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>

 <span data-ttu-id="4c4c3-105">Declarações de classe ou estrutura para implementar uma interface, mas não implementa um procedimento, propriedade ou evento definido pela interface.</span><span class="sxs-lookup"><span data-stu-id="4c4c3-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="4c4c3-106">Todos os membros da interface devem ser implementados.</span><span class="sxs-lookup"><span data-stu-id="4c4c3-106">Every member of the interface must be implemented.</span></span>

 <span data-ttu-id="4c4c3-107">**ID do erro:** BC30154</span><span class="sxs-lookup"><span data-stu-id="4c4c3-107">**Error ID:** BC30154</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4c4c3-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="4c4c3-108">To correct this error</span></span>

1. <span data-ttu-id="4c4c3-109">Declare um membro com o mesmo nome e assinatura, conforme definido na interface.</span><span class="sxs-lookup"><span data-stu-id="4c4c3-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="4c4c3-110">Certifique-se de incluir pelo menos `End Function` a `End Sub` instrução, ou `End Property` .</span><span class="sxs-lookup"><span data-stu-id="4c4c3-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>

2. <span data-ttu-id="4c4c3-111">Adicione uma `Implements` cláusula ao final da `Function` instrução,, `Sub` `Property` ou `Event` .</span><span class="sxs-lookup"><span data-stu-id="4c4c3-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="4c4c3-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4c4c3-112">For example:</span></span>

    ```vb
    Public Event ItHappened() Implements IBaseInterface.ItHappened
    ```

3. <span data-ttu-id="4c4c3-113">Ao implementar uma propriedade, verifique se o `ReadOnly` ou o `WriteOnly` é usado da mesma maneira que na definição da interface.</span><span class="sxs-lookup"><span data-stu-id="4c4c3-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>

4. <span data-ttu-id="4c4c3-114">Ao implementar uma propriedade, declare `Get` e `Set` procedimentos, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="4c4c3-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c4c3-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="4c4c3-115">See also</span></span>

- [<span data-ttu-id="4c4c3-116">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="4c4c3-116">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="4c4c3-117">Interfaces</span><span class="sxs-lookup"><span data-stu-id="4c4c3-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
