---
title: Operador IsNot
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ea978f8874cee20fb3a005189fd846f7564da777
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811035"
---
# <a name="isnot-operator-visual-basic"></a>Operador IsNot (Visual Basic)

Compara duas variáveis de referência de objeto.

## <a name="syntax"></a>Sintaxe

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>Partes

- `result`

  Obrigatórios. Um valor `Boolean`.

- `object1`

  Obrigatórios. Qualquer `Object` variável ou expressão.

- `object2`

  Obrigatórios. Qualquer `Object` variável ou expressão.

## <a name="remarks"></a>Comentários

O `IsNot` operador determina se duas referências de objeto se referem a objetos diferentes. No entanto, ele não executa comparações de valor. Se `object1` e `object2` ambos se referirem exatamente à mesma instância de objeto, `result` será `False` ; se não forem, `result` é `True` .

`IsNot` é o oposto do `Is` operador. A vantagem do `IsNot` é que você pode evitar uma sintaxe estranha com `Not` e `Is` , que pode ser difícil de ler.

 Você pode usar os `Is` `IsNot` operadores e para testar os objetos de ligação antecipada e de associação tardia.

## <a name="example"></a>Exemplo

O exemplo de código a seguir usa o `Is` operador e o `IsNot` operador para realizar a mesma comparação.

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a>Use o operador TypeOf com o operador IsNot

A partir do Visual Basic 14, você pode usar o `TypeOf` operador com o `IsNot` operador para testar se um objeto *não* é compatível com um tipo de dados. Por exemplo:

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a>Confira também

- [Operador Is](is-operator.md)
- [Operador TypeOf](typeof-operator.md)
- [Precedência do operador no Visual Basic](operator-precedence.md)
- [Como testar se dois objetos são iguais](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
