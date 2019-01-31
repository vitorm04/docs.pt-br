---
title: <type1>'<typename>' deve implementar '<methodname>' para interface '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c5dd7c6889a3fb5344142ee9914f98e8922d748b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264422"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1 >'\<typename >' deve implementar '\<methodname >' para interface '\<interfacename >'
Uma classe ou estrutura para implementar uma interface de declarações, mas não implementa um procedimento definido pela interface. Todos os membros da interface devem ser implementado.  
  
 **ID do erro:** BC30149  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Declara um procedimento com o mesmo nome e assinatura, conforme definido na interface. Não se esqueça de incluir pelo menos o `End Function` ou `End Sub` instrução.  
  
2.  Adicionar um `Implements` cláusula no final dos `Function` ou `Sub` instrução. Por exemplo:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Consulte também
- [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
