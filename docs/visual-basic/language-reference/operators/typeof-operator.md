---
title: Operador TypeOf (Visual Basic)
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
ms.openlocfilehash: fe287794423048e993d953c83fc8590a06b7a5e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604049"
---
# <a name="typeof-operator-visual-basic"></a>Operador TypeOf (Visual Basic)
Compara uma variável de referência de objeto para um tipo de dados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Retornado. Um valor `Boolean`.  
  
 `objectexpression`  
 Necessário. Qualquer expressão que é avaliada como um tipo de referência.  
  
 `typename`  
 Necessário. Qualquer tipo de dados nome.  
  
## <a name="remarks"></a>Comentários  
 O `TypeOf` operador determina se o tempo de execução do tipo de `objectexpression` é compatível com `typename`. A compatibilidade depende da categoria de tipo de `typename`. A tabela a seguir mostra como compatibilidade é determinada.  
  
|Categoria de tipo de `typename`|Critério de compatibilidade|  
|---------------------------------|-----------------------------|  
|Classe|`objectexpression` é do tipo `typename` ou herda de `typename`|  
|Estrutura|`objectexpression` é do tipo `typename`|  
|Interface|`objectexpression` implementa `typename` ou herda de uma classe que implementa `typename`|  
  
 Se o tipo de tempo de execução de `objectexpression` satisfaz o critério de compatibilidade, `result` é `True`. Caso contrário, `result` é `False`.  Se `objectexpression` for nulo, `TypeOf`... `Is` retorna `False`, e... `IsNot` retorna `True`.  
  
 `TypeOf` sempre é usado com o `Is` palavra-chave para construir um `TypeOf`... `Is` expressão, ou com o `IsNot` palavra-chave para construir um `TypeOf`... `IsNot` expressão.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `TypeOf`... `Is` para testar a compatibilidade das duas variáveis de referência com vários tipos de dados do objeto.  
  
 [!code-vb[VbVbalrOperators#39](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]  
  
 A variável `refInteger` tem um tipo de tempo de execução de `Integer`. Ele é compatível com `Integer` , mas não com `Double`. A variável `refForm` tem um tipo de tempo de execução de <xref:System.Windows.Forms.Form>. Ele é compatível com <xref:System.Windows.Forms.Form> porque esse é o seu tipo, com <xref:System.Windows.Forms.Control> porque <xref:System.Windows.Forms.Form> herda de <xref:System.Windows.Forms.Control>e com <xref:System.ComponentModel.IComponent> porque <xref:System.Windows.Forms.Form> herda de <xref:System.ComponentModel.Component>, que implementa <xref:System.ComponentModel.IComponent>. No entanto, `refForm` não é compatível com <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Consulte também  
 [Operador Is](../../../visual-basic/language-reference/operators/is-operator.md)  
 [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Operadores de comparação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
