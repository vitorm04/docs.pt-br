---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39; deve implementar &#39; &lt;membername&gt; &#39; para interface &#39; &lt;interfacename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 14e7bd199215764676a4b563eafc68bd6dabadc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574736"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt;typename&gt; &#39; deve implementar &#39; &lt;membername&gt; &#39; para interface &#39; &lt;interfacename&gt;&#39;
'\<typename >' deve implementar '\<membername >' para interface '\<interfacename >'. Implementação de propriedade deve ter 'ReadOnly' / 'WriteOnly' especificadores.  
  
 Uma classe ou estrutura para implementar uma interface de declarações, mas não implementa um procedimento, propriedade ou evento definido pela interface. Todos os membros da interface devem ser implementado.  
  
 **ID do erro:** BC30154  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Declare um membro com o mesmo nome e assinatura, conforme definido na interface. Não se esqueça de incluir pelo menos o `End Function`, `End Sub`, ou `End Property` instrução.  
  
2.  Adicionar um `Implements` cláusula no final dos `Function`, `Sub`, `Property`, ou `Event` instrução. Por exemplo:  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  Ao implementar uma propriedade, certifique-se de que `ReadOnly` ou `WriteOnly` é usado da mesma forma como a definição de interface.  
  
4.  Quando estiver implementando uma propriedade, declare `Get` e `Set` procedimentos, conforme apropriado.  
  
## <a name="see-also"></a>Consulte também
- [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
