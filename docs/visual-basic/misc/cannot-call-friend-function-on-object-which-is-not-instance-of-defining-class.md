---
title: Não é possível chamar a função friend no objeto que não é uma instância da classe de definição
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: a107b2a11f6f8324c3029e83c5eca64c2ee32ebf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742823"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="5d547-102">Não é possível chamar a função friend no objeto que não é uma instância da classe de definição</span><span class="sxs-lookup"><span data-stu-id="5d547-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="5d547-103">Ou você tentou chamar as `Friend` procedimento de uma classe, ou você tentou acessar um `Friend` propriedade ou método entre processos ou entre threads.</span><span class="sxs-lookup"><span data-stu-id="5d547-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="5d547-104">Um `Friend` procedimento pode ser chamado de um módulo de fora da classe, mas é parte do projeto no qual a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="5d547-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5d547-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5d547-105">To correct this error</span></span>  
  
-   <span data-ttu-id="5d547-106">Certifique-se de que você estiver chamando ou acessando o procedimento a partir de um módulo que faz parte do projeto no qual a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="5d547-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d547-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d547-107">See also</span></span>
- [<span data-ttu-id="5d547-108">Friend</span><span class="sxs-lookup"><span data-stu-id="5d547-108">Friend</span></span>](../../visual-basic/language-reference/modifiers/friend.md)
