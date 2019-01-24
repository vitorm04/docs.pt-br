---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39; deve implementar &#39; &lt;methodname&gt; &#39; para interface &#39; &lt;interfacename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: ff9ffd50f7f21814d5e4c23fd8df50b12bf746f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642432"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt;typename&gt; &#39; deve implementar &#39; &lt;methodname&gt; &#39; para interface &#39; &lt;interfacename&gt;&#39;
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
