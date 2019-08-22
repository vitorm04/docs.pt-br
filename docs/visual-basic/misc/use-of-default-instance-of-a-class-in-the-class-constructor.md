---
title: O uso da instância padrão de uma classe no construtor de classe pode levar à chamada recursiva infinita
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: cec3d3d462822ca571cab59a2e4d7e730d2aec46
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664375"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="eb1ae-102">O uso da instância padrão de uma classe no construtor de classe pode levar à chamada recursiva infinita</span><span class="sxs-lookup"><span data-stu-id="eb1ae-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="eb1ae-103">Uma instância padrão de uma classe foi usada no construtor da classe.</span><span class="sxs-lookup"><span data-stu-id="eb1ae-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="eb1ae-104">Isso pode levar a uma chamada recursiva infinita, também conhecida como um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="eb1ae-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eb1ae-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="eb1ae-105">To correct this error</span></span>  
  
- <span data-ttu-id="eb1ae-106">Remova a instância padrão do construtor de classe.</span><span class="sxs-lookup"><span data-stu-id="eb1ae-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb1ae-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb1ae-107">See also</span></span>

- [<span data-ttu-id="eb1ae-108">Construtores</span><span class="sxs-lookup"><span data-stu-id="eb1ae-108">Constructors</span></span>](../programming-guide/concepts/object-oriented-programming.md#constructors)
