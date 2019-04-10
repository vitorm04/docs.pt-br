---
title: 'Como: Determinar se dois objetos são idêntico (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: aae053ae0473ed6ced0f28da3d5e5afc0be629df
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295024"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>Como: Determinar se dois objetos são idêntico (Visual Basic)
No Visual Basic, duas referências de variável são consideradas idênticas se os ponteiros são os mesmos, ou seja, se as duas variáveis apontam para a mesma instância de classe na memória. Por exemplo, em um aplicativo de formulários do Windows, talvez você queira fazer uma comparação para determinar se a instância atual (`Me`) é o mesmo que uma determinada instância, como `Form2`.  
  
 Visual Basic fornece dois operadores para comparar ponteiros. O [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) retorna `True` se os objetos forem idênticos e o [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) retorna `True` se eles não forem.  
  
## <a name="determining-if-two-objects-are-identical"></a>Determinando se dois objetos são idênticos  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>Para determinar se dois objetos são idênticos  
  
1. Configurar um `Boolean` expressão para testar os dois objetos.  
  
2. Em sua expressão de teste, use o `Is` operador com os dois objetos como operandos.  
  
     `Is` Retorna `True` se os objetos apontam para a mesma instância de classe.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>Determinando se dois objetos não são idênticos  
 Às vezes você deseja executar uma ação se dois objetos não são idênticos, e pode ser complicado combinar `Not` e `Is`, por exemplo `If Not obj1 Is obj2`. Nesse caso, você pode usar o `IsNot` operador.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>Para determinar se dois objetos não são idênticos  
  
1. Configurar um `Boolean` expressão para testar os dois objetos.  
  
2. Em sua expressão de teste, use o `IsNot` operador com os dois objetos como operandos.  
  
     `IsNot` Retorna `True` se os objetos não apontam para a mesma instância de classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir testa pares de `Object` variáveis para ver se eles apontam para a mesma instância de classe.  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 O exemplo anterior exibe a saída a seguir.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>Consulte também

- [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Valores de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Operador Is](../../../../visual-basic/language-reference/operators/is-operator.md)
- [Operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Como: determinar se dois objetos estão relacionados](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
