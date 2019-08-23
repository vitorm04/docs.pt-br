---
title: Operador Is (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: a5481a9bce01e84ce4f078335c8cd15a747a3c51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917211"
---
# <a name="is-operator-visual-basic"></a>Operador Is (Visual Basic)
Compara duas variáveis de referência de objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer `Boolean` valor.  
  
 `object1`  
 Necessário. Qualquer `Object` nome.  
  
 `object2`  
 Necessário. Qualquer `Object` nome.  
  
## <a name="remarks"></a>Comentários  
 O `Is` operador determina se duas referências de objeto se referem ao mesmo objeto. No entanto, ele não executa comparações de valor. Se `object1` e `True` `result` `result` `False`ambos se referirem exatamente à mesma instância de objeto, será; se não forem, será. `object2`  
  
 `Is`também pode ser usado com a `TypeOf` palavra-chave para `TypeOf`criar um... `Is` expressão, que testa se uma variável de objeto é compatível com um tipo de dados.  
  
> [!NOTE]
> A `Is` palavra-chave também é usada no [Select... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `Is` o operador para comparar pares de referências de objeto. Os resultados são atribuídos a um `Boolean` valor que representa se os dois objetos são idênticos.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Como demonstra o exemplo anterior, você pode usar o `Is` operador para testar os objetos ligados antecipadamente e associação tardia.  
  
## <a name="see-also"></a>Consulte também

- [Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operadores de comparação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
