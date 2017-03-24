---
title: "Cláusula Handles (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Handles
- vb.Handles
dev_langs:
- VB
helpviewer_keywords:
- Handles keyword
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
caps.latest.revision: 19
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
ms.openlocfilehash: 7c79935e7f15f31abca7efddbc443239d5db2f58
ms.lasthandoff: 03/13/2017

---
# <a name="handles-clause-visual-basic"></a>Cláusula Handles (Visual Basic)
Declara se um procedimento manipula um evento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Partes  
 `proceduredeclaration`  
 O `Sub` declaração de procedimento para o procedimento que manipulará o evento.  
  
 `eventlist`  
 Lista de eventos para `proceduredeclaration` para tratar, separados por vírgulas. Os eventos devem ser gerados pela classe base para a classe atual, ou por um objeto declarado usando a `WithEvents` palavra-chave.  
  
## <a name="remarks"></a>Comentários  
 Use o `Handles` palavra-chave no final de uma declaração de procedimento faz com que ele manipule eventos causados por uma variável de objeto declarado usando a `WithEvents` palavra-chave. O `Handles` palavra-chave também pode ser usado em uma classe derivada para manipular eventos de uma classe base.  
  
 O `Handles` palavra-chave e o `AddHandler` instrução os dois permitem que você especifique que determinados procedimentos manipulem eventos específicos, mas há diferenças. Use o `Handles` palavra-chave ao definir um procedimento para especificar que ele manipula um evento específico. O `AddHandler` instrução conecta os procedimentos a eventos em tempo de execução. Para obter mais informações, consulte [instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md).  
  
 Para eventos personalizados, o aplicativo chama o evento `AddHandler` acessador quando ele adiciona o procedimento como um manipulador de eventos. Para obter mais informações sobre eventos personalizados, consulte [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrEvents n º&2;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]  
  
 O exemplo a seguir demonstra como uma classe derivada pode usar o `Handles` declaração para tratar um evento de uma classe base.  
  
 [!code-vb[VbVbalrEvents n º&3;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir contém dois manipuladores de eventos do botão para um **aplicativo WPF** projeto.  
  
 [!code-vb[41 VbVbalrEvents](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é equivalente ao exemplo anterior. O `eventlist` no `Handles` cláusula contém os eventos para os dois botões.  
  
 [!code-vb[VbVbalrEvents&42;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)   
 [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)   
 [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
