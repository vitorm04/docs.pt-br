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
ms.openlocfilehash: 00d9f09bed513199d579c9e1c3f831b729e68839
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977130"
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
 Necessário em uma `Function`, `Get`, ou `Operator` procedimento. Expressão que representa o valor a ser retornado para o código de chamada.  
  
## <a name="remarks"></a>Comentários  
 Em um `Sub` ou `Set` procedimento, o `Return` instrução é equivalente a um `Exit Sub` ou `Exit Property` instrução, e `expression` não deve ser fornecido.  
  
 Em um `Function`, `Get`, ou `Operator` procedimento, o `Return` instrução deve incluir `expression`, e `expression` deve ser avaliada como um tipo de dados que seja conversível para o tipo de retorno do procedimento. Em um `Function` ou `Get` procedimento, você também tem a alternativa de atribuir uma expressão para o nome do procedimento para servir como o valor de retorno e, em seguida, executar uma `Exit Function` ou `Exit Property` instrução. Em um `Operator` procedimento, você deve usar `Return expression`.  
  
 Você pode incluir tantos `Return` instruções conforme apropriado no mesmo procedimento.  
  
> [!NOTE]
>  O código em um `Finally` bloco é executado depois de uma `Return` instrução em um `Try` ou `Catch` bloco é encontrada, mas antes que `Return` instrução é executada. Um `Return` instrução não pode ser incluída em um `Finally` bloco.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Return` instrução várias vezes para retornar para o código de chamada quando o procedimento não precisa fazer mais nada.  
  
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
