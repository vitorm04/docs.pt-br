---
title: "Não é possível chamar a função friend no objeto que não é uma instância da classe de definição | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: feb66206a07092e5f0334f23e12f6803f765e213
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="2ab11-102">Não é possível chamar a função friend no objeto que não é uma instância de definição de classe</span><span class="sxs-lookup"><span data-stu-id="2ab11-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="2ab11-103">Ou você tentou chamar o `Friend` procedimento de uma classe, ou você tentou acessar uma `Friend` propriedade ou método entre processos ou entre threads.</span><span class="sxs-lookup"><span data-stu-id="2ab11-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="2ab11-104">Um `Friend` procedimento pode ser chamado a partir de um módulo fora da classe, mas faz parte do projeto no qual a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="2ab11-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ab11-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2ab11-105">To correct this error</span></span>  
  
-   <span data-ttu-id="2ab11-106">Certifique-se de que você está chamando ou acessando o procedimento de um módulo que faz parte do projeto no qual a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="2ab11-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ab11-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ab11-107">See Also</span></span>  
 [<span data-ttu-id="2ab11-108">Friend</span><span class="sxs-lookup"><span data-stu-id="2ab11-108">Friend</span></span>](../../visual-basic/language-reference/modifiers/friend.md)
