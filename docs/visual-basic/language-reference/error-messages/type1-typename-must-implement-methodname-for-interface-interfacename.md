---
title: <type1>'<typename>'deve implementar'<methodname>'para interface'<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 432f089bc77928308820d7456d930fba8dc513f7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304903"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1 >'\<typename >' deve implementar '\<methodname >' para interface '\<interfacename >'
Uma classe ou estrutura para implementar uma interface de declarações, mas não implementa um procedimento definido pela interface. Todos os membros da interface devem ser implementado.  
  
 **ID do erro:** BC30149  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Declara um procedimento com o mesmo nome e assinatura, conforme definido na interface. Não se esqueça de incluir pelo menos o `End Function` ou `End Sub` instrução.  
  
2. Adicionar um `Implements` cláusula no final dos `Function` ou `Sub` instrução. Por exemplo:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
