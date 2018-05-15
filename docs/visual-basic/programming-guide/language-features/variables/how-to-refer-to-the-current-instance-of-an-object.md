---
title: Como fazer referência à instância atual de um objeto (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: c1b79f1b6a9768941d6fe966c5b5886ea742f808
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="c1127-102">Como fazer referência à instância atual de um objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1127-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="c1127-103">O *atual instância* de um objeto é a instância na qual o código está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="c1127-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="c1127-104">Você usa o `Me` palavra-chave para referir-se à instância atual.</span><span class="sxs-lookup"><span data-stu-id="c1127-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="c1127-105">Para fazer referência à instância atual</span><span class="sxs-lookup"><span data-stu-id="c1127-105">To refer to the current instance</span></span>  
  
-   <span data-ttu-id="c1127-106">Use o `Me` palavra-chave em que normalmente usaria o nome de uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="c1127-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="c1127-107">Embora `Me` se comporta como um objeto variável, você não pode declará-la ou atribuir algo a ela.</span><span class="sxs-lookup"><span data-stu-id="c1127-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="c1127-108">`Me` sempre refere-se à instância atual.</span><span class="sxs-lookup"><span data-stu-id="c1127-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1127-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1127-109">See Also</span></span>  
 [<span data-ttu-id="c1127-110">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="c1127-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="c1127-111">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="c1127-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="c1127-112">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="c1127-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
