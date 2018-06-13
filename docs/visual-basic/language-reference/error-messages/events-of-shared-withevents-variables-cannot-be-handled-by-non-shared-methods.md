---
title: Eventos de variáveis WithEvents compartilhadas não podem ser identificados por métodos não compartilhados
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: f61f4cd17b1bb3088117e0a0d91b186fd40db3b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585165"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Eventos de variáveis WithEvents compartilhadas não podem ser identificados por métodos não compartilhados
Uma variável declarada com o `Shared` modificador é uma variável compartilhada. Uma variável compartilhada identifica exatamente um local de armazenamento. Uma variável declarada com o `WithEvents` modificador declara que o tipo ao qual pertence a variável trata o conjunto de eventos que a variável gera. Quando um valor é atribuído à variável, a propriedade criada pelo `WithEvents` declaração desengancha qualquer manipulador de eventos existente e conecta o novo manipulador de eventos por meio de `Add` método.  
  
 **ID do erro:** BC30594  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Declarar o manipulador de eventos `Shared`.  
  
## <a name="see-also"></a>Consulte também  
 [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
