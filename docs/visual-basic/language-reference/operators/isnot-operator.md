---
title: Operador IsNot (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: babee364d350ca84a8379f675acc4b5c87f98303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603308"
---
# <a name="isnot-operator-visual-basic"></a>Operador IsNot (Visual Basic)
Compara duas variáveis de referência de objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Um valor `Boolean`.  
  
 `object1`  
 Necessário. Qualquer `Object` variável ou expressão.  
  
 `object2`  
 Necessário. Qualquer `Object` variável ou expressão.  
  
## <a name="remarks"></a>Comentários  
 O `IsNot` operador determina se duas referências de objeto se referir a objetos diferentes. No entanto, ele não realiza comparações de valor. Se `object1` e `object2` se referir à mesma instância de objeto, `result` é `False`; caso contrário, `result` é `True`.  
  
 `IsNot` é o oposto do `Is` operador. A vantagem de `IsNot` é que você pode evitar sintaxes estranhas com `Not` e `Is`, que pode ser difícil de ler.  
  
 Você pode usar o `Is` e `IsNot` operadores para testar objetos early bound e associação tardia.  
  
> [!NOTE]
>  O `IsNot` operador não pode ser usado para comparar expressões retornadas do `TypeOf` operador. Em vez disso, você deve usar o `Not` e `Is` operadores.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir usa o `Is` operador e o `IsNot` operador para realizar a mesma comparação.  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador Is](../../../visual-basic/language-reference/operators/is-operator.md)  
 [Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Como testar se dois objetos são iguais](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
