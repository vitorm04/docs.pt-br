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
ms.openlocfilehash: 64d21fe4aaf6fd34bf880373a7ab3067fb67820e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077053"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="90880-102">Como fazer referência à instância atual de um objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90880-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>

<span data-ttu-id="90880-103">A *instância atual* de um objeto é a instância na qual o código está sendo executado no momento.</span><span class="sxs-lookup"><span data-stu-id="90880-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="90880-104">Você usa a `Me` palavra-chave para se referir à instância atual.</span><span class="sxs-lookup"><span data-stu-id="90880-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="90880-105">Para fazer referência à instância atual</span><span class="sxs-lookup"><span data-stu-id="90880-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="90880-106">Use a `Me` palavra-chave onde você normalmente usaria o nome de uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="90880-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="90880-107">Embora `Me` o se comporta como uma variável de objeto, você não pode declará-lo nem atribuir nada a ele.</span><span class="sxs-lookup"><span data-stu-id="90880-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="90880-108">`Me` sempre refere-se à instância atual.</span><span class="sxs-lookup"><span data-stu-id="90880-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90880-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="90880-109">See also</span></span>

- [<span data-ttu-id="90880-110">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="90880-110">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="90880-111">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="90880-111">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="90880-112">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="90880-112">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
