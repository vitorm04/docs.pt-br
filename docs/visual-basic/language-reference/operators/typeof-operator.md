---
title: Operador TypeOf
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 22af5b8f8488ca44e388596530decd52e33525dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350885"
---
# <a name="typeof-operator-visual-basic"></a>Operador TypeOf (Visual Basic)
Verifica se o tipo de tempo de execução do resultado de uma expressão é compatível com tipo com o tipo especificado.
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Exibido. Um valor `Boolean`.  
  
 `objectexpression`  
 Necessária. Qualquer expressão que seja avaliada como um tipo de referência.  
  
 `typename`  
 Necessária. Qualquer nome de tipo de dados.  
  
## <a name="remarks"></a>Comentários  
 O operador `TypeOf` determina se o tipo de tempo de execução de `objectexpression` é compatível com `typename`. A compatibilidade depende da categoria de tipo de `typename`. A tabela a seguir mostra como a compatibilidade é determinada.  
  
|Categoria de tipo de `typename`|Critério de compatibilidade|  
|---------------------------------|-----------------------------|  
|Classe|`objectexpression` é do tipo `typename` ou herda de `typename`|  
|Estrutura|`objectexpression` é do tipo `typename`|  
|Interface|`objectexpression` implementa `typename` ou herda de uma classe que implementa `typename`|  
  
 Se o tipo de tempo de execução de `objectexpression` satisfizer o critério de compatibilidade, `result` será `True`. Caso contrário, `result` é `False`.  Se `objectexpression` for NULL, `TypeOf`...`Is` retorna `False`e...`IsNot` retorna `True`.  
  
 `TypeOf` é sempre usado com a palavra-chave `Is` para construir uma expressão `TypeOf`...`Is` ou com a palavra-chave `IsNot` para construir uma expressão `TypeOf`...`IsNot`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `TypeOf`...`Is` expressões para testar a compatibilidade de tipos de duas variáveis de referência de objeto com vários tipos de dados.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 A variável `refInteger` tem um tipo de tempo de execução de `Integer`. Ele é compatível com `Integer`, mas não com `Double`. A variável `refForm` tem um tipo de tempo de execução de <xref:System.Windows.Forms.Form>. Ele é compatível com <xref:System.Windows.Forms.Form> porque esse é o tipo, com <xref:System.Windows.Forms.Control> porque <xref:System.Windows.Forms.Form> herda de <xref:System.Windows.Forms.Control>e com <xref:System.ComponentModel.IComponent> porque <xref:System.Windows.Forms.Form> herda de <xref:System.ComponentModel.Component>, que implementa <xref:System.ComponentModel.IComponent>. No entanto, `refForm` não é compatível com <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Consulte também

- [Operador Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operadores de comparação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
