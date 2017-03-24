---
title: "Instrução Return (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Return
dev_langs:
- VB
helpviewer_keywords:
- Return statement, syntax
- control flow, returning control to expressions
- Return statement
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
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
ms.openlocfilehash: faa0b7ddc33abb6b2abde849a71e4032eeff65fb
ms.lasthandoff: 03/13/2017

---
# <a name="return-statement-visual-basic"></a>Instrução Return (Visual Basic)
Retorna o controle para o código que chamou um `Function`, `Sub`, `Get`, `Set`, ou `Operator` procedimento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>Parte  
 `expression`  
 Necessário em um `Function`, `Get`, ou `Operator` procedimento. Expressão que representa o valor a ser retornado para o código de chamada.  
  
## <a name="remarks"></a>Comentários  
 Em um `Sub` ou `Set` procedimento, o `Return` instrução é equivalente a uma `Exit Sub` ou `Exit Property` instrução, e `expression` não deve ser fornecido.  
  
 Em um `Function`, `Get`, ou `Operator` procedimento, o `Return` deve incluir a instrução `expression`, e `expression` deve ser avaliada como um tipo de dados que seja conversível para o tipo de retorno do procedimento. Em um `Function` ou `Get` procedimento, você também tem a alternativa de atribuir uma expressão para o nome do procedimento para servir como o valor de retorno e, em seguida, executar uma `Exit Function` ou `Exit Property` instrução. Em um `Operator` procedimento, você deve usar `Return``expression`.  
  
 Você pode incluir tantos `Return` instruções conforme apropriado no mesmo procedimento.  
  
> [!NOTE]
>  O código em um `Finally` bloco é executado após um `Return` instrução em uma `Try` ou `Catch` bloco for encontrada, mas antes que `Return` instrução é executada. A `Return` instrução não pode ser incluída em um `Finally` bloco.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Return` instrução várias vezes para retornar para o código de chamada quando o procedimento não precisa fazer mais nada.  
  
 [!code-vb[VbVbalrStatements&#53;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md)   
 [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)   
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
