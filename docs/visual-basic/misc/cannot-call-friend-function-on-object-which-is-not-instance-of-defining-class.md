---
title: Não é possível chamar a função friend no objeto que não é uma instância da classe de definição
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: c18c04470c4c49113e8195b92185326c5c4197c1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400842"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="852d9-102">Não é possível chamar a função friend no objeto que não é uma instância da classe de definição</span><span class="sxs-lookup"><span data-stu-id="852d9-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="852d9-103">Você tentou chamar o `Friend` procedimento de uma classe ou tentou acessar uma `Friend` propriedade ou um método entre processos ou entre threads.</span><span class="sxs-lookup"><span data-stu-id="852d9-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="852d9-104">Um `Friend` procedimento é chamado de um módulo fora da classe, mas faz parte do projeto no qual a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="852d9-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="852d9-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="852d9-105">To correct this error</span></span>  
  
- <span data-ttu-id="852d9-106">Certifique-se de que você está chamando ou acessando o procedimento a partir de um módulo que faz parte do projeto no qual a classe está definida.</span><span class="sxs-lookup"><span data-stu-id="852d9-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="852d9-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="852d9-107">See also</span></span>

- [<span data-ttu-id="852d9-108">Público</span><span class="sxs-lookup"><span data-stu-id="852d9-108">Friend</span></span>](../language-reference/modifiers/friend.md)
