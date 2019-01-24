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
ms.openlocfilehash: 6ed6f3d4fd77d714ab554d641c0c0fc4f403bbf8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715095"
---
# <a name="addhandler-statement"></a>Instrução AddHandler
Associa um evento com um manipulador de eventos em tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Partes  
|||
|---|---|
|evento|O nome do evento para manipular.|  
|`eventhandler`|O nome de um procedimento que manipula o evento.|
|||
  
## <a name="remarks"></a>Comentários  
 O `AddHandler` e `RemoveHandler` instruções permitem que você inicie e pare a manipulação de eventos a qualquer momento durante a execução do programa.  
  
 A assinatura do `eventhandler` procedimento deve corresponder à assinatura do evento `event`.  
  
 O `Handles` palavra-chave e o `AddHandler` instrução os dois permitem que você especifique que determinados procedimentos manipulem eventos específicos, mas há diferenças. O `AddHandler` instrução conecta os procedimentos a eventos em tempo de execução. Use o `Handles` palavra-chave ao definir um procedimento para especificar que ele manipula um evento específico. Para obter mais informações, consulte [manipula](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
>  Para eventos personalizados, o `AddHandler` instrução invoca o evento `AddHandler` acessador. Para obter mais informações sobre eventos personalizados, consulte [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
