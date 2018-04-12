---
title: Eventos de variáveis WithEvents compartilhadas não podem ser identificados por métodos não compartilhados
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53372927b88df3946583564492df42170f302739
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Eventos de variáveis WithEvents compartilhadas não podem ser identificados por métodos não compartilhados
Uma variável declarada com o `Shared` modificador é uma variável compartilhada. Uma variável compartilhada identifica exatamente um local de armazenamento. Uma variável declarada com o `WithEvents` modificador declara que o tipo ao qual pertence a variável trata o conjunto de eventos que a variável gera. Quando um valor é atribuído à variável, a propriedade criada pelo `WithEvents` declaração desengancha qualquer manipulador de eventos existente e conecta o novo manipulador de eventos por meio de `Add` método.  
  
 **ID do erro:** BC30594  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Declarar o manipulador de eventos `Shared`.  
  
## <a name="see-also"></a>Consulte também  
 [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
