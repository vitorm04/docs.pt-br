---
title: "Instrução AddHandler"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords: AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07fbfe04ccd01b7d0f99338ef2682238830099dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="addhandler-statement"></a>Instrução AddHandler
Associa um evento com um manipulador de eventos em tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Partes  
 `event`  
 O nome do evento para manipular.  
  
 `eventhandler`  
 O nome de um procedimento que manipula o evento.  
  
## <a name="remarks"></a>Comentários  
 O `AddHandler` e `RemoveHandler` instruções permitem iniciar e interromper a manipulação de eventos a qualquer momento durante a execução do programa.  
  
 A assinatura do `eventhandler` procedimento deve corresponder à assinatura do evento `event`.  
  
 O `Handles` palavra-chave e o `AddHandler` instrução ambos permitem que você especifique que determinados procedimentos manipulem eventos específicos, mas há diferenças. O `AddHandler` instrução conecta os procedimentos a eventos em tempo de execução. Use o `Handles` palavra-chave ao definir um procedimento para especificar que ele manipula um evento específico. Para obter mais informações, consulte [manipula](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
>  Para eventos personalizados, o `AddHandler` instrução invoca o evento `AddHandler` acessador. Para obter mais informações sobre eventos personalizados, consulte [instrução Event](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
