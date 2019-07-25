---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: abfe1489cb7e0d06b03c308e0704ce6f69ee55da
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433809"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Especifica que um argumento é passado [por valor](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), de modo que o procedimento chamado ou a propriedade não possa alterar o valor de uma variável subjacente ao argumento no código de chamada. Se nenhum modificador for especificado, ByVal será o padrão.
  
## <a name="remarks"></a>Comentários  
 O `ByVal` modificador pode ser usado nesses contextos:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso do `ByVal` mecanismo de passagem de parâmetro com um argumento de tipo de referência. No exemplo, o argumento é `c1`uma instância da classe. `Class1` `ByVal`impede que o código nos procedimentos altere o valor subjacente do argumento de referência, `c1`, mas não protege os campos e as propriedades acessíveis do. `c1`  
  
 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]  
  
## <a name="see-also"></a>Consulte também

- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
- [Passando Argumentos por Valor e por Referência](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
