---
title: Uso de instância padrão de uma classe no construtor da classe pode levar a chamada recursiva infinita
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 14c498bf3067415f8de2afaeaaa57cf3f28ae857
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022448"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="2d2e0-102">Uso de instância padrão de uma classe no construtor da classe pode levar a chamada recursiva infinita</span><span class="sxs-lookup"><span data-stu-id="2d2e0-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="2d2e0-103">Uma instância padrão de uma classe foi usada no construtor da classe.</span><span class="sxs-lookup"><span data-stu-id="2d2e0-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="2d2e0-104">Isso pode levar a uma chamada recursiva infinita, também conhecido como um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="2d2e0-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2d2e0-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2d2e0-105">To correct this error</span></span>  
  
- <span data-ttu-id="2d2e0-106">Remova a instância padrão do construtor da classe.</span><span class="sxs-lookup"><span data-stu-id="2d2e0-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d2e0-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d2e0-107">See also</span></span>

- [<span data-ttu-id="2d2e0-108">Construtores</span><span class="sxs-lookup"><span data-stu-id="2d2e0-108">Constructors</span></span>](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
