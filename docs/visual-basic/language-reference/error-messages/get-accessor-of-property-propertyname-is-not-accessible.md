---
title: "Acessor &quot; get&quot; da propriedade &quot;&lt;propertyname&gt;&quot; não está acessível | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31103
- bc31103
dev_langs:
- VB
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c2312783f9fb2a7eaac37e8ed1c859a5a8112005
ms.lasthandoff: 03/13/2017

---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>Acessor ' get' da propriedade '&lt;propertyname&gt;' não está acessível
Uma declaração tenta recuperar o valor de uma propriedade quando ela não tem acesso à propriedade `Get` procedimento.  
  
 Se o [instrução Get](../../../visual-basic/language-reference/statements/get-statement.md) é marcado com um acesso mais restritivo do nível em que seu [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md), uma tentativa de ler o valor da propriedade pode falhar nos seguintes casos:  
  
-   O `Get` instrução é marcada [particular](../../../visual-basic/language-reference/modifiers/private.md) e o código de chamada está fora da classe ou estrutura na qual a propriedade está definida.  
  
-   O `Get` instrução é marcada [protegido](../../../visual-basic/language-reference/modifiers/protected.md) e o código de chamada é não na classe ou estrutura na qual a propriedade é definida, nem em uma classe derivada.  
  
-   O `Get` instrução é marcada [amigo](../../../visual-basic/language-reference/modifiers/friend.md) e o código de chamada não está no mesmo assembly no qual a propriedade está definida.  
  
 **ID do erro:** BC31103  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você tiver o controle do código-fonte definindo a propriedade, considere declarando o `Get` procedimento com o mesmo nível de acesso que a própria propriedade.  
  
-   Se você não tem controle do código-fonte definindo a propriedade, você deve restringir o `Get` procedimento nível de acesso mais que a própria propriedade, tente mover a declaração que lê o valor da propriedade para uma região de código que tem um melhor acesso à propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Como declarar uma propriedade com níveis de acesso mistos](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
