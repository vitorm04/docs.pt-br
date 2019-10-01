---
title: <type1>'<typename>' deve implementar '<membername>' para interface '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: a824b66eaad964049ced5cae5eb2cc370d00ba7f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696889"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1 > ' \<typename > ' deve implementar ' \<membername > ' para a interface ' \<interfacename > '
' \<typename > ' deve implementar ' \<membername > ' para a interface ' \<interfacename > '. A implementação da propriedade deve ter especificadores ' ReadOnly '/' WriteOnly ' correspondentes.  
  
 Declarações de classe ou estrutura para implementar uma interface, mas não implementa um procedimento, propriedade ou evento definido pela interface. Todos os membros da interface devem ser implementados.  
  
 **ID do erro:** BC30154  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Declare um membro com o mesmo nome e assinatura, conforme definido na interface. Certifique-se de incluir pelo menos a instrução `End Function`, `End Sub` ou `End Property`.  
  
2. Adicione uma cláusula `Implements` ao final da instrução `Function`, `Sub`, `Property` ou `Event`. Por exemplo:  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. Ao implementar uma propriedade, certifique-se de que `ReadOnly` ou `WriteOnly` seja usado da mesma maneira como na definição da interface.  
  
4. Ao implementar uma propriedade, declare os procedimentos `Get` e `Set`, conforme apropriado.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
