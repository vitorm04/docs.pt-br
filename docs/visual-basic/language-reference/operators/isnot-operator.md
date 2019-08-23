---
title: Operador IsNot (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 0a83b48e5e415bd6ca0c777cef6d34f7127691b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966933"
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
 O `IsNot` operador determina se duas referências de objeto se referem a objetos diferentes. No entanto, ele não executa comparações de valor. Se `object1` e `False` `result` `result` `True`ambos se referirem exatamente à mesma instância de objeto, será; se não forem, será. `object2`  
  
 `IsNot`é o oposto do `Is` operador. A vantagem do `IsNot` é que você pode evitar uma sintaxe estranha `Not` com `Is`e, que pode ser difícil de ler.  
  
 Você pode usar os `Is` operadores `IsNot` e para testar os objetos de ligação antecipada e de associação tardia.  
  
> [!NOTE]
> O `IsNot` operador não pode ser usado para comparar as `TypeOf` expressões retornadas do operador. Em vez disso, você deve `Not` usar `Is` os operadores e.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir usa `Is` o operador e `IsNot` o operador para realizar a mesma comparação.  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a>Consulte também

- [Operador Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Como: Testar se dois objetos são iguais](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
