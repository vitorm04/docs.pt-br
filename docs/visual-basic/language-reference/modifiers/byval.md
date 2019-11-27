---
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: a96f871c6ce119f65ebbec54fdb1471ae105d504
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351593"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Especifica que um argumento é passado [por valor](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), de modo que o procedimento chamado ou a propriedade não possa alterar o valor de uma variável subjacente ao argumento no código de chamada. Se nenhum modificador for especificado, ByVal será o padrão.

> [!NOTE]
> Como é o padrão, você não precisa especificar explicitamente a palavra-chave `ByVal` em assinaturas de método. Ele tende a produzir código barulhento e, muitas vezes, leva à palavra-chave não padrão `ByRef` sendo ignorada.

## <a name="remarks"></a>Comentários
 O modificador de `ByVal` pode ser usado nesses contextos:

 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)

 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a>Exemplo
 O exemplo a seguir demonstra o uso do mecanismo de passagem de parâmetro `ByVal` com um argumento de tipo de referência. No exemplo, o argumento é `c1`, uma instância da classe `Class1`. `ByVal` impede que o código nos procedimentos altere o valor subjacente do argumento de referência, `c1`, mas não protege os campos e as propriedades acessíveis de `c1`.

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>Consulte também

- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
- [Passando Argumentos por Valor e por Referência](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
