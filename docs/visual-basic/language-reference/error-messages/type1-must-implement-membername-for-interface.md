---
title: <type1>'<typename>' deve implementar '<membername>' para interface '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: de7dd9026e08495941a89be0db11ad4c68d2a748
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264226"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1 >'\<typename >' deve implementar '\<membername >' para interface '\<interfacename >'
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
