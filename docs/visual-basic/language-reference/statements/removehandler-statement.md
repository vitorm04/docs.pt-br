---
title: Instrução RemoveHandler
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 0d982768707948bd6c616445509e16a462b86f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597982"
---
# <a name="removehandler-statement"></a>Instrução RemoveHandler
Remove a associação entre um evento e um manipulador de eventos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`event`|O nome do evento que está sendo tratado.|  
|`eventhandler`|O nome do procedimento atualmente manipular o evento.|  
  
## <a name="remarks"></a>Comentários  
 O `AddHandler` e `RemoveHandler` instruções permitem iniciar e interromper a manipulação de eventos para um evento específico a qualquer momento durante a execução do programa.  
  
> [!NOTE]
>  Para eventos personalizados, o `RemoveHandler` instrução invoca o evento `RemoveHandler` acessador. Para obter mais informações sobre eventos personalizados, consulte [instrução Event](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
