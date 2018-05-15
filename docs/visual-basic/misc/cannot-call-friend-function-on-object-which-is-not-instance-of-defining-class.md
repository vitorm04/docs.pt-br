---
title: Não é possível chamar a função friend no objeto que não é uma instância da classe de definição
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: a655207110d512805490b693e413b1d22b0367ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="b8eab-102">Não é possível chamar a função friend no objeto que não é uma instância da classe de definição</span><span class="sxs-lookup"><span data-stu-id="b8eab-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="b8eab-103">Ou você tentar chamar o `Friend` procedimento de uma classe, ou você tentou acessar uma `Friend` propriedade ou método entre processos ou entre threads.</span><span class="sxs-lookup"><span data-stu-id="b8eab-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="b8eab-104">Um `Friend` procedimento é chamado de um módulo fora da classe, mas faz parte do projeto no qual a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="b8eab-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b8eab-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b8eab-105">To correct this error</span></span>  
  
-   <span data-ttu-id="b8eab-106">Certifique-se de que você está chamando ou acessar o procedimento a partir de um módulo que faz parte do projeto no qual a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="b8eab-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8eab-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8eab-107">See Also</span></span>  
 [<span data-ttu-id="b8eab-108">Friend</span><span class="sxs-lookup"><span data-stu-id="b8eab-108">Friend</span></span>](../../visual-basic/language-reference/modifiers/friend.md)
