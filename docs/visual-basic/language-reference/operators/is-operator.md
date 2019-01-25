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
ms.openlocfilehash: a78189a6b82100665ac07b9d7c89590613ec1e1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745617"
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
 O `Is` operador determina se duas referências de objeto se referem ao mesmo objeto. No entanto, ele não realiza comparações de valor. Se `object1` e `object2` fazem referência à mesma instância de objeto, `result` é `True`; caso contrário, `result` é `False`.  
  
 `Is` também pode ser usado com o `TypeOf` palavra-chave para tornar um `TypeOf`... `Is` expressão, que testa se uma variável de objeto é compatível com um tipo de dados.  
  
> [!NOTE]
>  O `Is` palavra-chave também é usado no [selecione... Instrução de caso](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Is` operador para comparar pares de referências de objeto. Os resultados são atribuídos a um `Boolean` valor representando se os dois objetos são idênticos.  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 Conforme demonstrado no exemplo anterior, você pode usar o `Is` operador para o teste de associação antecipada e tardia em objetos.  
  
## <a name="see-also"></a>Consulte também
- [Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operadores de comparação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
