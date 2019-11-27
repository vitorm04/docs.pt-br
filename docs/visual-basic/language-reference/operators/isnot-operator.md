---
title: Operador IsNot
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 616506f64d20e1f150b443433f1b69040136a5ba
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336069"
---
# <a name="isnot-operator-visual-basic"></a>Operador IsNot (Visual Basic)

Compara duas variáveis de referência de objeto.

## <a name="syntax"></a>Sintaxe

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>Partes
 `result` Necessário. Um valor `Boolean`.

 `object1` Necessário. Qualquer `Object` variável ou expressão.

 `object2` Necessário. Qualquer `Object` variável ou expressão.

## <a name="remarks"></a>Comentários
 O operador `IsNot` determina se duas referências de objeto se referem a objetos diferentes. No entanto, ele não executa comparações de valor. Se `object1` e `object2` fizerem referência exatamente à mesma instância de objeto, `result` será `False`; Se não tiverem, `result` será `True`.

 `IsNot` é o oposto do operador de `Is`. A vantagem do `IsNot` é que você pode evitar uma sintaxe estranha com `Not` e `Is`, o que pode ser difícil de ler.

 Você pode usar os operadores de `Is` e `IsNot` para testar os objetos de ligação antecipada e de associação tardia.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir usa tanto o operador de `Is` quanto o operador de `IsNot` para realizar a mesma comparação.

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a>Consulte também

- [Operador Is](is-operator.md)
- [Operador TypeOf](typeof-operator.md)
- [Precedência do operador no Visual Basic](operator-precedence.md)
- [Como testar se dois objetos são iguais](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
