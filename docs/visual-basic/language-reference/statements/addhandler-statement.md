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
ms.openlocfilehash: 95277f532488b0cf56114e5ee94dc3528e3a2e02
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004535"
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
  
 A assinatura do procedimento `eventhandler` deve corresponder à assinatura do evento `event`.  
  
 A palavra-chave `Handles` e a instrução `AddHandler` permitem que você especifique que procedimentos específicos manipulam eventos específicos, mas há diferenças. A instrução `AddHandler` conecta procedimentos a eventos em tempo de execução. Use a palavra-chave `Handles` ao definir um procedimento para especificar que ele trata de um evento específico. Para obter mais informações, consulte [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
> Para eventos personalizados, a instrução `AddHandler` invoca o acessador do evento `AddHandler`. Para obter mais informações sobre eventos personalizados, consulte [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
