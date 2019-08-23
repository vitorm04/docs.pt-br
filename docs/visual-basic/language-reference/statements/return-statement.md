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
ms.openlocfilehash: af49ea95d7f9d01072190ac3ccf6ba2f1041347e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957670"
---
# <a name="return-statement-visual-basic"></a>Instrução Return (Visual Basic)
Retorna o controle para o código que chamou `Function`um `Sub`procedimento `Get`, `Set`,, `Operator` ou.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>Parte  
 `expression`  
 Necessário em um `Function`procedimento `Get`, ou `Operator` . Expressão que representa o valor a ser retornado para o código de chamada.  
  
## <a name="remarks"></a>Comentários  
 Em um `Sub` procedimento `Set` ou, a `Return` instrução é equivalente a uma `Exit Sub` instrução `Exit Property` or e `expression` não deve ser fornecida.  
  
 Em um `Function`procedimento `Get`,, `Operator` ou, a `Return` instrução deve incluir `expression`e `expression` deve ser avaliada como um tipo de dados que é conversível para o tipo de retorno do procedimento. Em um `Function` procedimento `Get` ou, você também tem a alternativa de atribuir uma expressão ao nome do procedimento para servir como o valor de retorno e, em seguida, executar `Exit Function` uma `Exit Property` instrução or. Em um `Operator` procedimento, você deve usar `Return expression`.  
  
 Você pode incluir `Return` quantas instruções forem apropriadas no mesmo procedimento.  
  
> [!NOTE]
> O código em um `Finally` bloco é executado depois `Return` que uma instrução `Try` em `Catch` um bloco ou é encontrada, mas `Return` antes que essa instrução seja executada. Uma `Return` instrução não pode ser incluída em `Finally` um bloco.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Return` a instrução várias vezes para retornar ao código de chamada quando o procedimento não precisa fazer mais nada.  
  
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
