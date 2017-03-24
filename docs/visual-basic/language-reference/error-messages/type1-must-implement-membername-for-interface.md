---
title: '&lt;type1&gt;&quot;&lt;typename&gt;&quot;deve implementar&quot;&lt;membername&gt;&quot;para interface&quot;&lt;interfacename&gt;&quot; | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30154
- bc30154
dev_langs:
- VB
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
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
ms.openlocfilehash: 4cf8e075a55586cfc0d28539e6022609ba5a11e3
ms.lasthandoff: 03/13/2017

---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;'&lt;typename&gt;'deve implementar'&lt;membername&gt;'para interface'&lt;interfacename&gt;'
'\<typename >' deve implementar '\<membername >' para interface '\<interfacename >'. Implementação de propriedade deve ter 'ReadOnly' / 'WriteOnly' especificadores.  
  
 Uma classe ou estrutura alega implementar uma interface mas não implementa um procedimento, propriedade ou evento definido pela interface. Cada membro da interface deve ser implementado.  
  
 **ID do erro:** BC30154  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Declare um membro com o mesmo nome e assinatura, conforme definido na interface. Não se esqueça de incluir pelo menos o `End Function`, `End Sub`, ou `End Property` instrução.  
  
2.  Adicionar uma `Implements` cláusula no final do `Function`, `Sub`, `Property`, ou `Event` instrução. Por exemplo:  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  Quando estiver implementando uma propriedade, verifique se `ReadOnly` ou `WriteOnly` é usado da mesma forma como na definição de interface.  
  
4.  Quando estiver implementando uma propriedade, declare `Get` e `Set` procedimentos, conforme apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
