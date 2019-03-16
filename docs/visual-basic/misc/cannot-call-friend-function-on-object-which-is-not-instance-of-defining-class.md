---
title: Não é possível chamar a função friend no objeto que não é uma instância da classe de definição
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: c65bbb5028cf042b702bb2b8336d40512c980790
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58018255"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="40161-102">Não é possível chamar a função friend no objeto que não é uma instância da classe de definição</span><span class="sxs-lookup"><span data-stu-id="40161-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="40161-103">Ou você tentou chamar as `Friend` procedimento de uma classe, ou você tentou acessar um `Friend` propriedade ou método entre processos ou entre threads.</span><span class="sxs-lookup"><span data-stu-id="40161-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="40161-104">Um `Friend` procedimento pode ser chamado de um módulo de fora da classe, mas é parte do projeto no qual a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="40161-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="40161-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="40161-105">To correct this error</span></span>  
  
-   <span data-ttu-id="40161-106">Certifique-se de que você estiver chamando ou acessando o procedimento a partir de um módulo que faz parte do projeto no qual a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="40161-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40161-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40161-107">See also</span></span>

- [<span data-ttu-id="40161-108">Friend</span><span class="sxs-lookup"><span data-stu-id="40161-108">Friend</span></span>](../../visual-basic/language-reference/modifiers/friend.md)
