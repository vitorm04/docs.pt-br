---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68a58fd130c04f2ed0cb1f2e5b9250f6c85f120d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Especifica que uma ou mais variáveis de membro declaradas referem-se a uma instância de uma classe que pode gerar eventos.  
  
## <a name="remarks"></a>Comentários  
 Quando uma variável é definida usando `WithEvents`, você pode especificar declarativamente que um método trata os eventos da variável usando a `Handles` palavra-chave.  
  
 Você pode usar `WithEvents` apenas no nível de classe ou módulo. Isso significa que o contexto da declaração para um `WithEvents` variável deve ser uma classe ou um módulo e não pode ser um arquivo de origem, namespace, estrutura ou procedimento.  
  
 Não é possível usar `WithEvents` em um membro da estrutura.  
  
 Você pode declarar apenas variáveis individuais — não matrizes — com `WithEvents`.  
  
## <a name="rules"></a>Regras  
  
-   **Tipos de elemento.** Você deve declarar `WithEvents` variáveis como variáveis de objeto para que eles podem aceitar instâncias de classe. No entanto, você não pode declará-los como `Object`. Você deve declará-los como a classe específica que pode gerar eventos.  
  
 O `WithEvents` modificador pode ser usado neste contexto: [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)  
 [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
