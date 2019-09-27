---
title: Operador IsNot (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 7e1ac1004e671f592c03bd44ee7ec2e8cc572933
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71331625"
---
# <a name="isnot-operator-visual-basic"></a>Operador IsNot (Visual Basic)
Compara duas variáveis de referência de objeto.

## <a name="syntax"></a>Sintaxe

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>Partes
 `result` Necessário. Um valor `Boolean`.

 `object1` Necessário. Qualquer variável ou expressão `Object`.

 `object2` Necessário. Qualquer variável ou expressão `Object`.

## <a name="remarks"></a>Comentários
 O operador `IsNot` determina se duas referências de objeto se referem a objetos diferentes. No entanto, ele não executa comparações de valor. Se `object1` e `object2` fizerem referência exatamente à mesma instância de objeto, `result` será `False`; Se não tiverem, `result` será `True`.

 `IsNot` é o oposto do operador `Is`. A vantagem do `IsNot` é que você pode evitar uma sintaxe estranha com `Not` e `Is`, o que pode ser difícil de ler.

 Você pode usar os operadores `Is` e `IsNot` para testar os objetos de ligação antecipada e de associação tardia.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir usa o operador `Is` e o operador `IsNot` para realizar a mesma comparação.

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a>Consulte também

- [Operador Is](is-operator.md)
- [Operador TypeOf](typeof-operator.md)
- [Precedência do operador no Visual Basic](operator-precedence.md)
- [Como: Testar se dois objetos são do mesmo @ no__t-0
