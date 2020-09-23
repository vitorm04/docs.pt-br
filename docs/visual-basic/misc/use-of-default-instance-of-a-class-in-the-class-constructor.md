---
title: O uso de instância padrão de uma classe no construtor de classe pode levar a chamada recursiva infinita
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 5d239fdb7dcc5c488bf0341043b810ec7dadc083
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100315"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="b650e-102">O uso de instância padrão de uma classe no construtor de classe pode levar a chamada recursiva infinita</span><span class="sxs-lookup"><span data-stu-id="b650e-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>

<span data-ttu-id="b650e-103">Uma instância padrão de uma classe foi usada no construtor da classe.</span><span class="sxs-lookup"><span data-stu-id="b650e-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="b650e-104">Isso pode levar a uma chamada recursiva infinita, também conhecida como um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="b650e-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b650e-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b650e-105">To correct this error</span></span>  
  
- <span data-ttu-id="b650e-106">Remova a instância padrão do construtor de classe.</span><span class="sxs-lookup"><span data-stu-id="b650e-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b650e-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="b650e-107">See also</span></span>

- [<span data-ttu-id="b650e-108">Construtores</span><span class="sxs-lookup"><span data-stu-id="b650e-108">Constructors</span></span>](../programming-guide/concepts/object-oriented-programming.md#constructors)
