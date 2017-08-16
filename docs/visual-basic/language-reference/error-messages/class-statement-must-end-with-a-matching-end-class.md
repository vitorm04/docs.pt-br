---
title: "Instrução &quot;Class&quot; deve finalizar com &quot;End Class&quot; correspondente | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30481
- bc30481
dev_langs:
- VB
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 04ee9fc64a7f8896023ca18fa986a0911a828a2a
ms.lasthandoff: 03/13/2017

---
# <a name="39class39-statement-must-end-with-a-matching-39end-class39"></a>Instrução 'Class' deve finalizar com 'End Class' correspondente
`Class`é usado para iniciar um `Class` bloco; portanto, ele só pode aparecer no início do bloco, com uma correspondência `End Class` terminando o bloco de instrução. Ou você tem um redundantes `Class` instrução, ou você não encerrou o `Class` bloco com `End Class`.  
  
 **ID do erro:** BC30481  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Localize e remova os desnecessários `Class` instrução.  
  
-   Conclua o `Class` bloco com uma correspondência `End Class`.  
  
## <a name="see-also"></a>Consulte também  
 [End \<palavra-chave > instrução](../../../visual-basic/language-reference/statements/end-keyword-statement.md)   
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)
