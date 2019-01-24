---
title: 'Como: Fazer referência à instância atual de um objeto (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: d166ce62a2bb0522d1ca7011aeff7afe076c2d8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542191"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="36ef3-102">Como: Fazer referência à instância atual de um objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36ef3-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="36ef3-103">O *instância atual* de um objeto é a instância na qual o código está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="36ef3-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="36ef3-104">Você usa o `Me` palavra-chave para referir-se à instância atual.</span><span class="sxs-lookup"><span data-stu-id="36ef3-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="36ef3-105">Para fazer referência à instância atual</span><span class="sxs-lookup"><span data-stu-id="36ef3-105">To refer to the current instance</span></span>  
  
-   <span data-ttu-id="36ef3-106">Use o `Me` palavra-chave em que você normalmente usaria o nome de uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="36ef3-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="36ef3-107">Embora `Me` se comporta como um objeto variável, você não pode declará-la ou atribuir algo a ela.</span><span class="sxs-lookup"><span data-stu-id="36ef3-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="36ef3-108">`Me` sempre refere-se à instância atual.</span><span class="sxs-lookup"><span data-stu-id="36ef3-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36ef3-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36ef3-109">See also</span></span>
- [<span data-ttu-id="36ef3-110">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="36ef3-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="36ef3-111">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="36ef3-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="36ef3-112">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="36ef3-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
