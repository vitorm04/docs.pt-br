---
title: Instrução Return (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: 2f614045be1b91b9c747d961cdefd526ba1bab98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
 Necessário em um `Function`, `Get`, ou `Operator` procedimento. Expressão que representa o valor a ser retornado ao código de chamada.  
  
## <a name="remarks"></a>Comentários  
 Em um `Sub` ou `Set` procedimento, o `Return` instrução é equivalente a uma `Exit Sub` ou `Exit Property` instrução, e `expression` não deve ser fornecido.  
  
 Em um `Function`, `Get`, ou `Operator` procedimento, o `Return` deve incluir a instrução `expression`, e `expression` devem ser avaliados como um tipo de dados que é conversível para o tipo de retorno do procedimento. Em um `Function` ou `Get` procedimento, você também tem a alternativa de atribuir uma expressão para o nome do procedimento para servir como o valor de retorno e, em seguida, executar uma `Exit Function` ou `Exit Property` instrução. Em um `Operator` procedimento, você deve usar `Return``expression`.  
  
 Você pode incluir tantos `Return` instruções conforme apropriado no mesmo procedimento.  
  
> [!NOTE]
>  O código em um `Finally` bloco é executado um `Return` instrução em um `Try` ou `Catch` bloco for encontrada, mas antes que `Return` instrução é executada. Um `Return` instrução não pode ser incluída em um `Finally` bloco.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Return` instrução várias vezes para retornar ao código de chamada quando o procedimento não precisa fazer mais nada.  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
