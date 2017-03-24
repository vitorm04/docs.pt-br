---
title: "Como: fazer referência à instância atual de um objeto (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances, referring to current
- current instance
- object variables
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
caps.latest.revision: 14
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
ms.openlocfilehash: 83e29c8a57649525f1a2afda6898ddf3bb82787e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Como fazer referência à instância atual de um objeto (Visual Basic)
O *atual instância* de um objeto é a instância na qual o código está sendo executado.  
  
 Você usa o `Me` palavra-chave para se referir à instância atual.  
  
### <a name="to-refer-to-the-current-instance"></a>Para fazer referência à instância atual  
  
-   Use o `Me` palavra-chave onde você normalmente usa o nome de uma variável de objeto.  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Embora `Me` se comporta como um objeto variável, você não pode declará-la ou atribuir algo a ela. `Me`sempre refere-se à instância atual.  
  
## <a name="see-also"></a>Consulte também  
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Atribuição de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
