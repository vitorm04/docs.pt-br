---
title: '&lt;type1&gt;&quot;&lt;typename&gt;&quot;deve implementar&quot;&lt;methodname&gt;&quot;para interface&quot;&lt;interfacename&gt;&quot; | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30149
- bc30149
dev_langs:
- VB
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
caps.latest.revision: 10
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
ms.openlocfilehash: 1c600b979b62dae635f11d8d242bb5083d5925db
ms.lasthandoff: 03/13/2017

---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;'&lt;typename&gt;'deve implementar'&lt;methodname&gt;'para interface'&lt;interfacename&gt;'
Uma classe ou estrutura alega implementar uma interface mas não implementa um procedimento definido pela interface. Cada membro da interface deve ser implementado.  
  
 **ID do erro:** BC30149  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Declare um procedimento com o mesmo nome e assinatura, conforme definido na interface. Não se esqueça de incluir pelo menos o `End Function` ou `End Sub` instrução.  
  
2.  Adicionar uma `Implements` cláusula no final do `Function` ou `Sub` instrução. Por exemplo:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
