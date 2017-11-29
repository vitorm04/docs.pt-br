---
title: '&lt;type1&gt;&#39;&lt; TypeName&gt;&#39; deve implementar &#39;&lt; MethodName&gt;&#39; para interface &#39;&lt; InterfaceName&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords: BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e803ec7d0054f2fa1b9ed2a731fd30c9c3060468
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt; TypeName&gt;&#39; deve implementar &#39;&lt; MethodName&gt;&#39; para interface &#39;&lt; InterfaceName&gt;&#39;
Uma classe ou estrutura alega implementar uma interface mas não implementa um procedimento definido pela interface. Cada membro da interface deve ser implementado.  
  
 **ID do erro:** BC30149  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Declara um procedimento com o mesmo nome e assinatura, conforme definido na interface. Certifique-se de incluir pelo menos o `End Function` ou `End Sub` instrução.  
  
2.  Adicionar uma `Implements` cláusula ao final do `Function` ou `Sub` instrução. Por exemplo:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
