---
title: Instrução 'Class' deve finalizar com 'End Class' correspondente
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: d67f0e71dbdbf97420ec5b5ba4b6f06acfba1bd9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874612"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a>Instrução 'Class' deve finalizar com 'End Class' correspondente

`Class` é usado para iniciar um `Class` bloco; portanto, ele só pode aparecer no início do bloco, com uma instrução correspondente que `End Class` termina o bloco. Você tem uma instrução redundante `Class` ou não terminou seu `Class` bloco com `End Class` .  
  
 **ID do erro:** BC30481  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Localize e remova a instrução desnecessária `Class` .  
  
- Conclua o `Class` bloco com uma correspondência `End Class` .  
  
## <a name="see-also"></a>Confira também

- [\<keyword>Instrução End](../statements/end-keyword-statement.md)
- [Instrução Class](../statements/class-statement.md)
