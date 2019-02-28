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
ms.openlocfilehash: dd57f63b5741822de7b11c1fafe90452a767aa34
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965638"
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
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Consulte também
- [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
