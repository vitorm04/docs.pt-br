---
title: '&#39;Definir&#39; acessador de propriedade &#39; &lt;propertyname&gt; &#39; não está acessível'
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: d047d03755de89d4740482db4845d5db72003ac0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595846"
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39;Definir&#39; acessador de propriedade &#39; &lt;propertyname&gt; &#39; não está acessível
Uma declaração tenta recuperar o valor de uma propriedade quando ela não tem acesso para a propriedade `Set` procedimento.  
  
 Se o [instrução Set](../../../visual-basic/language-reference/statements/set-statement.md) está marcado com um acesso mais restritivo do nível em que seu [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md), uma tentativa de definir o valor da propriedade pode falhar nos seguintes casos:  
  
-   O `Set` instrução está marcado como [privada](../../../visual-basic/language-reference/modifiers/private.md) e o código de chamada está fora da classe ou estrutura na qual a propriedade está definida.  
  
-   O `Set` instrução está marcado como [protegidos](../../../visual-basic/language-reference/modifiers/protected.md) e o código de chamada é não na classe ou estrutura na qual a propriedade é definida, nem em uma classe derivada.  
  
-   O `Set` instrução está marcado como [Friend](../../../visual-basic/language-reference/modifiers/friend.md) e o código de chamada não está no mesmo assembly no qual a propriedade está definida.  
  
 **ID do erro:** BC31102  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você tiver o controle do código-fonte definindo a propriedade, considere declarando o `Set` procedimento com o mesmo nível de acesso da propriedade.  
  
-   Se você não tem controle do código-fonte definindo a propriedade, você deve restringir o `Set` procedimento nível de acesso mais que a própria propriedade, tente mover a declaração que define o valor da propriedade a uma região de código que tem um acesso melhor para o propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de Propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Como declarar uma propriedade com níveis de acesso mistos](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
