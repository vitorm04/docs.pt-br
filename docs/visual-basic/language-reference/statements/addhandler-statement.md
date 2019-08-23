---
title: Instrução AddHandler (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: a9913cd682e52562422ba140e27187d37c592684
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928948"
---
# <a name="addhandler-statement"></a>Instrução AddHandler
Associa um evento a um manipulador de eventos em tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Partes  
|||
|---|---|
|evento|O nome do evento a ser manipulado.|  
|`eventhandler`|O nome de um procedimento que manipula o evento.|
|||
  
## <a name="remarks"></a>Comentários  
 As `AddHandler` instruções `RemoveHandler` e permitem iniciar e parar a manipulação de eventos a qualquer momento durante a execução do programa.  
  
 A assinatura do `eventhandler` procedimento deve corresponder à assinatura do evento `event`.  
  
 A `Handles` palavra-chave `AddHandler` e a instrução permitem que você especifique que procedimentos específicos manipulam eventos específicos, mas há diferenças. A `AddHandler` instrução conecta procedimentos a eventos em tempo de execução. Use a `Handles` palavra-chave ao definir um procedimento para especificar que ele trata de um evento específico. Para obter mais informações, consulte [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
> Para eventos personalizados, a `AddHandler` instrução invoca o acessador `AddHandler` do evento. Para obter mais informações sobre eventos personalizados, consulte [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
