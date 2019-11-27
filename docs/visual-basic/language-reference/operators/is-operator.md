---
title: Operador Is
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 52fbb39ab0a36c8b947b78f464fad26be05ce204
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349540"
---
# <a name="is-operator-visual-basic"></a>Operador Is (Visual Basic)
Compara duas variáveis de referência de objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessária. Qualquer valor de `Boolean`.  
  
 `object1`  
 Necessária. Qualquer `Object` nome.  
  
 `object2`  
 Necessária. Qualquer `Object` nome.  
  
## <a name="remarks"></a>Comentários  
 O operador `Is` determina se duas referências de objeto se referem ao mesmo objeto. No entanto, ele não executa comparações de valor. Se `object1` e `object2` fizerem referência exatamente à mesma instância de objeto, `result` será `True`; Se não tiverem, `result` será `False`.  
  
 `Is` também pode ser usado com a palavra-chave `TypeOf` para criar uma expressão `TypeOf`...`Is`, que testa se uma variável de objeto é compatível com um tipo de dados.  
  
> [!NOTE]
> A palavra-chave `Is` também é usada no [Select... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `Is` para comparar pares de referências de objeto. Os resultados são atribuídos a um valor `Boolean` que representa se os dois objetos são idênticos.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Como demonstra o exemplo anterior, você pode usar o operador `Is` para testar os objetos ligados antecipadamente e associação tardia.  
  
## <a name="see-also"></a>Consulte também

- [Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operadores de comparação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
