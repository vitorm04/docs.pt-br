---
title: 'Como: Consulte a instância atual de um objeto (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 6c216dbc59bcad7a9f24bb01f856c3d29c288dbb
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005661"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="7fe77-102">Como: Consulte a instância atual de um objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fe77-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="7fe77-103">A *instância atual* de um objeto é a instância na qual o código está sendo executado no momento.</span><span class="sxs-lookup"><span data-stu-id="7fe77-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="7fe77-104">Use a palavra-chave `Me` para fazer referência à instância atual.</span><span class="sxs-lookup"><span data-stu-id="7fe77-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="7fe77-105">Para fazer referência à instância atual</span><span class="sxs-lookup"><span data-stu-id="7fe77-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="7fe77-106">Use a palavra-chave `Me`, em que você normalmente usaria o nome de uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="7fe77-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="7fe77-107">Embora `Me` se comporta como uma variável de objeto, você não pode declará-la nem atribuir nada a ela.</span><span class="sxs-lookup"><span data-stu-id="7fe77-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="7fe77-108">`Me` sempre se refere à instância atual.</span><span class="sxs-lookup"><span data-stu-id="7fe77-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe77-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fe77-109">See also</span></span>

- [<span data-ttu-id="7fe77-110">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="7fe77-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="7fe77-111">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="7fe77-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="7fe77-112">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="7fe77-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
