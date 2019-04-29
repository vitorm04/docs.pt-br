---
title: Instrução 'Class' deve finalizar com 'End Class' correspondente
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 0619db618abd562bda86836bdd41bbcd6caee0f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649888"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a>Instrução 'Class' deve finalizar com 'End Class' correspondente
`Class` é usado para iniciar um `Class` block; portanto, ele só pode aparecer no início do bloco, com uma correspondência `End Class` terminando o bloco de instrução. Ou você tem um redundantes `Class` instrução, ou você não ter terminado sua `Class` bloco com `End Class`.  
  
 **ID do erro:** BC30481  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Localize e remova o desnecessárias `Class` instrução.  
  
- Concluo a `Class` bloco com uma correspondência `End Class`.  
  
## <a name="see-also"></a>Consulte também

- [End \<palavra-chave > demonstrativo](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
- [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)
