---
title: Operador Is (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b1f3f0fa1fd782550c08c816f47b7541399198e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
 O `Is` operador determina se duas referências de objeto referem-se ao mesmo objeto. No entanto, ele não realiza comparações de valor. Se `object1` e `object2` se referir à mesma instância de objeto, `result` é `True`; caso contrário, `result` é `False`.  
  
 `Is`também pode ser usado com o `TypeOf` palavra-chave para fazer um `TypeOf`... `Is` expressão, que testa se uma variável de objeto é compatível com um tipo de dados.  
  
> [!NOTE]
>  O `Is` palavra-chave também é usada a [selecione... Caso a instrução](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Is` operador para comparar pares de referências de objeto. Os resultados são atribuídos a um `Boolean` valor representando se os dois objetos são idênticos.  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 Como demonstrado no exemplo anterior, você pode usar o `Is` operador para o teste associação inicial e objetos de associação tardia.  
  
## <a name="see-also"></a>Consulte também  
 [Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Operadores de comparação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
