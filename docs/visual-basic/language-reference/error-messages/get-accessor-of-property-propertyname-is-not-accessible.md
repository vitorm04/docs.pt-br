---
title: '&#39;Obter&#39; acessador de propriedade &#39; &lt;propertyname&gt; &#39; não está acessível'
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 10b7168ac40ca7c7d696cd63cd823454f404bb94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582208"
---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39;Obter&#39; acessador de propriedade &#39; &lt;propertyname&gt; &#39; não está acessível
Uma declaração tenta recuperar o valor de uma propriedade quando ela não tem acesso para a propriedade `Get` procedimento.  
  
 Se o [instrução Get](../../../visual-basic/language-reference/statements/get-statement.md) está marcada com um acesso mais restritivo nível que seus [instrução Property](../../../visual-basic/language-reference/statements/property-statement.md), uma tentativa de ler o valor da propriedade pode falhar nos seguintes casos:  
  
-   O `Get` declaração está marcada [privada](../../../visual-basic/language-reference/modifiers/private.md) e o código de chamada está fora da classe ou estrutura na qual a propriedade é definida.  
  
-   O `Get` declaração está marcada [protegido](../../../visual-basic/language-reference/modifiers/protected.md) e o código de chamada é não na classe ou estrutura na qual a propriedade é definida, nem em uma classe derivada.  
  
-   O `Get` declaração está marcada [amigo](../../../visual-basic/language-reference/modifiers/friend.md) e o código de chamada não está no mesmo assembly no qual a propriedade é definida.  
  
 **ID do erro:** BC31103  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você tiver o controle do código-fonte definindo a propriedade, considere a possibilidade de declarar o `Get` procedimento com o mesmo nível de acesso que a própria propriedade.  
  
-   Se você não tem controle do código-fonte definindo a propriedade, você deve restringir o `Get` procedimento de nível de acesso mais que a própria propriedade, tente mover a declaração que lê o valor da propriedade para uma região de código que tem um melhor acesso para o propriedade.  
  
## <a name="see-also"></a>Consulte também
- [Procedimentos de Propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Como: Declarar uma propriedade com níveis de acesso mistos](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
