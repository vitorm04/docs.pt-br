---
title: "Não é possível chamar a função friend no objeto que não é uma instância da classe de definição"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f1ac1ea14efb0cdf0d8ca03257e4da33d35e368
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>Não é possível chamar a função friend no objeto que não é uma instância da classe de definição
Ou você tentar chamar o `Friend` procedimento de uma classe, ou você tentou acessar uma `Friend` propriedade ou método entre processos ou entre threads. Um `Friend` procedimento é chamado de um módulo fora da classe, mas faz parte do projeto no qual a classe é definida.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que você está chamando ou acessar o procedimento a partir de um módulo que faz parte do projeto no qual a classe é definida.  
  
## <a name="see-also"></a>Consulte também  
 [Friend](../../visual-basic/language-reference/modifiers/friend.md)
