---
title: Instrução AddHandler
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: c110116af75d4fb39c016b8d6afcdb707fa6599b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350186"
---
# <a name="addhandler-statement"></a>Instrução AddHandler
Associa um evento a um manipulador de eventos em tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Partes  
|||
|---|---|
|evento|O nome do evento a ser manipulado.|  
|`eventhandler`|O nome de um procedimento que manipula o evento.|
|||
  
## <a name="remarks"></a>Comentários  
 As instruções `AddHandler` e `RemoveHandler` permitem iniciar e parar a manipulação de eventos a qualquer momento durante a execução do programa.  
  
 A assinatura do procedimento de `eventhandler` deve corresponder à assinatura do `event`de evento.  
  
 A palavra-chave `Handles` e a instrução `AddHandler` permitem que você especifique que procedimentos específicos manipulam eventos específicos, mas há diferenças. A instrução `AddHandler` conecta procedimentos a eventos em tempo de execução. Use a palavra-chave `Handles` ao definir um procedimento para especificar que ele trata de um evento específico. Para obter mais informações, consulte [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
> Para eventos personalizados, a instrução `AddHandler` invoca o acessador de `AddHandler` do evento. Para obter mais informações sobre eventos personalizados, consulte [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
