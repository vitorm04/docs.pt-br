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
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7d7b8f5e4b81ddc5d5320da55705f818c79f6f24
ms.lasthandoff: 03/13/2017

---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>Não é possível chamar a função friend no objeto que não é uma instância de definição de classe
Ou você tentou chamar o `Friend` procedimento de uma classe, ou você tentou acessar uma `Friend` propriedade ou método entre processos ou entre threads. Um `Friend` procedimento pode ser chamado a partir de um módulo fora da classe, mas faz parte do projeto no qual a classe é definida.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que você está chamando ou acessando o procedimento de um módulo que faz parte do projeto no qual a classe é definida.  
  
## <a name="see-also"></a>Consulte também  
 [Friend](../../visual-basic/language-reference/modifiers/friend.md)
