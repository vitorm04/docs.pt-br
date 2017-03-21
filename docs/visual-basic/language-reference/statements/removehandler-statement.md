---
title: "Instrução RemoveHandler | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
dev_langs:
- VB
helpviewer_keywords:
- RemoveHandler keyword
- RemoveHandler statement
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: 14
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
ms.openlocfilehash: d35de576bd9e267800acc2a9bfd5761dd977622f
ms.lasthandoff: 03/13/2017

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
|`event`|O nome do evento que está sendo manipulado.|  
|`eventhandler`|O nome do procedimento atualmente manipulando o evento.|  
  
## <a name="remarks"></a>Comentários  
 O `AddHandler` e `RemoveHandler` instruções permitem que você inicie e pare a manipulação de eventos para um evento específico a qualquer momento durante a execução do programa.  
  
> [!NOTE]
>  Para eventos personalizados, o `RemoveHandler` instrução chama o evento `RemoveHandler` acessador. Para obter mais informações sobre eventos personalizados, consulte [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemplo  
 [!code-vb[17 VbVbalrEvents](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [Identificadores](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
