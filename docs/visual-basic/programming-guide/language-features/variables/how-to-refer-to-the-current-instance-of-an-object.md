---
title: "Como: fazer referência à instância atual de um objeto (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances, referring to current
- current instance
- object variables
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4af75cf83bc065325398551401b51e9d4b0ee446
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="7d747-102">Como fazer referência à instância atual de um objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d747-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="7d747-103">O *atual instância* de um objeto é a instância na qual o código está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="7d747-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="7d747-104">Você usa o `Me` palavra-chave para se referir à instância atual.</span><span class="sxs-lookup"><span data-stu-id="7d747-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="7d747-105">Para fazer referência à instância atual</span><span class="sxs-lookup"><span data-stu-id="7d747-105">To refer to the current instance</span></span>  
  
-   <span data-ttu-id="7d747-106">Use o `Me` palavra-chave onde você normalmente usa o nome de uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="7d747-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="7d747-107">Embora `Me` se comporta como um objeto variável, você não pode declará-la ou atribuir algo a ela.</span><span class="sxs-lookup"><span data-stu-id="7d747-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="7d747-108">`Me`sempre refere-se à instância atual.</span><span class="sxs-lookup"><span data-stu-id="7d747-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d747-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d747-109">See Also</span></span>  
 <span data-ttu-id="7d747-110">[Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="7d747-110">[Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="7d747-111"> [Atribuição de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span><span class="sxs-lookup"><span data-stu-id="7d747-111"> [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span></span>  
<span data-ttu-id="7d747-112"> [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span><span class="sxs-lookup"><span data-stu-id="7d747-112"> [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span></span>
