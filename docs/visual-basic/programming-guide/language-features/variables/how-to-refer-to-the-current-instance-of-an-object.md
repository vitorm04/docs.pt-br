---
title: Como fazer referência à instância atual de um objeto
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 43bfd54592fb1d26cbf7f268b7e098e01e3745d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410419"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="5f59b-102">Como fazer referência à instância atual de um objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f59b-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="5f59b-103">A *instância atual* de um objeto é a instância na qual o código está sendo executado no momento.</span><span class="sxs-lookup"><span data-stu-id="5f59b-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="5f59b-104">Você usa a `Me` palavra-chave para se referir à instância atual.</span><span class="sxs-lookup"><span data-stu-id="5f59b-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="5f59b-105">Para fazer referência à instância atual</span><span class="sxs-lookup"><span data-stu-id="5f59b-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="5f59b-106">Use a `Me` palavra-chave onde você normalmente usaria o nome de uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="5f59b-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="5f59b-107">Embora `Me` o se comporta como uma variável de objeto, você não pode declará-lo nem atribuir nada a ele.</span><span class="sxs-lookup"><span data-stu-id="5f59b-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="5f59b-108">`Me`sempre refere-se à instância atual.</span><span class="sxs-lookup"><span data-stu-id="5f59b-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f59b-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="5f59b-109">See also</span></span>

- [<span data-ttu-id="5f59b-110">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="5f59b-110">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="5f59b-111">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="5f59b-111">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="5f59b-112">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="5f59b-112">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
