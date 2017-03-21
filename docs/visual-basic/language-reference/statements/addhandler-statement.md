---
title: "Instrução AddHandler | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
dev_langs:
- VB
helpviewer_keywords:
- AddHandler statement
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 728d8393c44d777f9cc016d9cf66030036582ae4
ms.lasthandoff: 03/13/2017

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
 O `AddHandler` e `RemoveHandler` instruções permitem que você inicie e pare a manipulação de eventos a qualquer momento durante a execução do programa.  
  
 A assinatura de `eventhandler` procedimento deve corresponder à assinatura do evento `event`.  
  
 O `Handles` palavra-chave e o `AddHandler` instrução os dois permitem que você especifique que determinados procedimentos manipulem eventos específicos, mas há diferenças. O `AddHandler` instrução conecta os procedimentos a eventos em tempo de execução. Use o `Handles` palavra-chave ao definir um procedimento para especificar que ele manipula um evento específico. Para obter mais informações, consulte [manipula](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
>  Para eventos personalizados, o `AddHandler` instrução chama o evento `AddHandler` acessador. Para obter mais informações sobre eventos personalizados, consulte [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemplo  
 [!code-vb[17 VbVbalrEvents](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Identificadores](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
