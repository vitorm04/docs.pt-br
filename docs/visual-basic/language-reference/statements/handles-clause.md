---
title: Cláusula Handles (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 3be28ee718675b1f6bebfaff03baaf561a6fff43
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974062"
---
# <a name="handles-clause-visual-basic"></a>Cláusula Handles (Visual Basic)
Declara um procedimento manipula um evento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Partes  
 `proceduredeclaration`  
 O `Sub` declaração de procedimento para o procedimento que manipulará o evento.  
  
 `eventlist`  
 Lista os eventos para `proceduredeclaration` para manipular, separados por vírgulas. Os eventos devem ser gerados pela classe base para a classe atual, ou por um objeto declarado usando a `WithEvents` palavra-chave.  
  
## <a name="remarks"></a>Comentários  
 Use o `Handles` palavra-chave no final de uma declaração de procedimento para fazer com que ele manipule eventos gerados por uma variável de objeto declaradas usando o `WithEvents` palavra-chave. O `Handles` palavra-chave também pode ser usado em uma classe derivada para manipular eventos de uma classe base.  
  
 O `Handles` palavra-chave e o `AddHandler` instrução os dois permitem que você especifique que determinados procedimentos manipulem eventos específicos, mas há diferenças. Use o `Handles` palavra-chave ao definir um procedimento para especificar que ele manipula um evento específico. O `AddHandler` instrução conecta os procedimentos a eventos em tempo de execução. Para obter mais informações, consulte [instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md).  
  
 Para eventos personalizados, o aplicativo chama o evento `AddHandler` acessador quando ele adiciona o procedimento como um manipulador de eventos. Para obter mais informações sobre eventos personalizados, consulte [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 O exemplo a seguir demonstra como uma classe derivada pode usar o `Handles` instrução para manipular um evento de uma classe base.  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir contém dois manipuladores de eventos do botão para um **aplicativo WPF** projeto.  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é equivalente ao exemplo anterior. O `eventlist` no `Handles` cláusula contém os eventos para os dois botões.  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a>Consulte também
- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
