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
ms.openlocfilehash: edaaf09f5a984344f7e89c9da988c529774934e9
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583264"
---
# <a name="return-statement-visual-basic"></a>Instrução Return (Visual Basic)
Retorna o controle para o código que chamou um procedimento `Function`, `Sub`, `Get`, `Set` ou `Operator`.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a>Parte  
 `expression`  
 Necessário em um procedimento `Function`, `Get` ou `Operator`. Expressão que representa o valor a ser retornado para o código de chamada.  
  
## <a name="remarks"></a>Comentários  
 Em um procedimento `Sub` ou `Set`, a instrução `Return` é equivalente a uma instrução `Exit Sub` ou `Exit Property` e a `expression` não deve ser fornecida.  
  
 Em um procedimento `Function`, `Get` ou `Operator`, a instrução `Return` deve incluir `expression` e `expression` deve ser avaliada como um tipo de dados que é conversível para o tipo de retorno do procedimento. Em um procedimento `Function` ou `Get`, você também tem a alternativa de atribuir uma expressão ao nome do procedimento para servir como o valor de retorno e, em seguida, executar uma instrução `Exit Function` ou `Exit Property`. Em um procedimento `Operator`, você deve usar `Return expression`.  
  
 Você pode incluir tantas `Return` instruções, conforme apropriado no mesmo procedimento.  
  
> [!NOTE]
> O código em um bloco de `Finally` é executado depois que uma instrução `Return` em um `Try` ou bloco de `Catch` é encontrada, mas antes que a instrução `Return` seja executada. Uma instrução `Return` não pode ser incluída em um bloco de `Finally`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a instrução `Return` várias vezes para retornar ao código de chamada quando o procedimento não precisa fazer mais nada.  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md)
- [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)
- [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
