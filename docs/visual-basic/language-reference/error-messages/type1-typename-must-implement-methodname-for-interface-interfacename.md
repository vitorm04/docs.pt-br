---
title: <type1>'<typename>' deve implementar '<methodname>' para interface '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 68c6f65e6be229cc74458fa56fe3d3aa889c18f7
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161862"
---
# <a name="bc30149-type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="1e6f0-102">BC30149: \<type1> ' \<typename> ' deve implementar ' \<methodname> ' para a interface ' \<interfacename> '</span><span class="sxs-lookup"><span data-stu-id="1e6f0-102">BC30149: \<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="1e6f0-103">Uma classe ou estrutura alega implementar uma interface, mas não implementa um procedimento definido pela interface.</span><span class="sxs-lookup"><span data-stu-id="1e6f0-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="1e6f0-104">Todos os membros da interface devem ser implementados.</span><span class="sxs-lookup"><span data-stu-id="1e6f0-104">Every member of the interface must be implemented.</span></span>

 <span data-ttu-id="1e6f0-105">**ID do erro:** BC30149</span><span class="sxs-lookup"><span data-stu-id="1e6f0-105">**Error ID:** BC30149</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1e6f0-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="1e6f0-106">To correct this error</span></span>

1. <span data-ttu-id="1e6f0-107">Declare um procedimento com o mesmo nome e assinatura, conforme definido na interface.</span><span class="sxs-lookup"><span data-stu-id="1e6f0-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="1e6f0-108">Certifique-se de incluir pelo menos `End Function` a `End Sub` instrução ou.</span><span class="sxs-lookup"><span data-stu-id="1e6f0-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="1e6f0-109">Adicione uma `Implements` cláusula ao final da `Function` `Sub` instrução ou.</span><span class="sxs-lookup"><span data-stu-id="1e6f0-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="1e6f0-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1e6f0-110">For example:</span></span>

    ```vb
    Public Sub DoSomething() Implements IBaseInterface.DoSomething
    ```

## <a name="see-also"></a><span data-ttu-id="1e6f0-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="1e6f0-111">See also</span></span>

- [<span data-ttu-id="1e6f0-112">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="1e6f0-112">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="1e6f0-113">Interfaces</span><span class="sxs-lookup"><span data-stu-id="1e6f0-113">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
