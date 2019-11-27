---
title: Cláusula Handles
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 2fecad919722f3da25c48f133a9c92b5e683d5e4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345904"
---
# <a name="handles-clause-visual-basic"></a>Cláusula Handles (Visual Basic)
Declara que um procedimento manipula um evento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Partes  
 `proceduredeclaration`  
 A declaração de procedimento `Sub` para o procedimento que manipulará o evento.  
  
 `eventlist`  
 Lista de eventos para `proceduredeclaration` manipular, separados por vírgulas. Os eventos devem ser gerados pela classe base para a classe atual ou por um objeto declarado usando a palavra-chave `WithEvents`.  
  
## <a name="remarks"></a>Comentários  
 Use a palavra-chave `Handles` no final de uma declaração de procedimento para fazer com que ele manipule eventos gerados por uma variável de objeto declarada usando a palavra-chave `WithEvents`. A palavra-chave `Handles` também pode ser usada em uma classe derivada para manipular eventos de uma classe base.  
  
 A palavra-chave `Handles` e a instrução `AddHandler` permitem que você especifique que procedimentos específicos manipulam eventos específicos, mas há diferenças. Use a palavra-chave `Handles` ao definir um procedimento para especificar que ele trata de um evento específico. A instrução `AddHandler` conecta procedimentos a eventos em tempo de execução. Para obter mais informações, consulte [instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md).  
  
 Para eventos personalizados, o aplicativo invoca o acessador de `AddHandler` do evento ao adicionar o procedimento como um manipulador de eventos. Para obter mais informações sobre eventos personalizados, consulte [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 O exemplo a seguir demonstra como uma classe derivada pode usar a instrução `Handles` para manipular um evento de uma classe base.  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir contém dois manipuladores de eventos de botão para um projeto de **aplicativo WPF** .  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é equivalente ao exemplo anterior. O `eventlist` na cláusula `Handles` contém os eventos para ambos os botões.  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a>Consulte também

- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
