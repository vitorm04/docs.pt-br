---
title: Como determinar se dois objetos são idênticos
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 5deebd4ffc5b277c94f5ae36c00fd6e5010a1551
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348607"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>Como determinar se dois objetos são idênticos (Visual Basic)
Em Visual Basic, duas referências de variáveis são consideradas idênticas se seus ponteiros forem iguais, ou seja, se ambas as variáveis apontarem para a mesma instância de classe na memória. Por exemplo, em um aplicativo Windows Forms, talvez você queira fazer uma comparação para determinar se a instância atual (`Me`) é igual a uma instância específica, como `Form2`.  
  
 Visual Basic fornece dois operadores para comparar ponteiros. O [operador is](../../../../visual-basic/language-reference/operators/is-operator.md) retornará `True` se os objetos forem idênticos e o [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) retornar `True` se não forem.  
  
## <a name="determining-if-two-objects-are-identical"></a>Determinando se dois objetos são idênticos  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>Para determinar se dois objetos são idênticos  
  
1. Configure uma expressão de `Boolean` para testar os dois objetos.  
  
2. Em sua expressão de teste, use o operador `Is` com os dois objetos como operandos.  
  
     `Is` retornará `True` se os objetos apontarem para a mesma instância de classe.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>Determinando se dois objetos não são idênticos  
 Às vezes, você deseja executar uma ação se os dois objetos não forem idênticos, e pode ser estranho combinar `Not` e `Is`, por exemplo `If Not obj1 Is obj2`. Nesse caso, você pode usar o operador de `IsNot`.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>Para determinar se dois objetos não são idênticos  
  
1. Configure uma expressão de `Boolean` para testar os dois objetos.  
  
2. Em sua expressão de teste, use o operador `IsNot` com os dois objetos como operandos.  
  
     `IsNot` retornará `True` se os objetos não apontarem para a mesma instância de classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir testa pares de `Object` variáveis para ver se eles apontam para a mesma instância de classe.  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 O exemplo anterior exibe a saída a seguir.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>Consulte também

- [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Operador Is](../../../../visual-basic/language-reference/operators/is-operator.md)
- [Operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Como determinar se dois objetos estão relacionados](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
