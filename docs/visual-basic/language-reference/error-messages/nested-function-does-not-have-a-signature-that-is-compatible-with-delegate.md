---
title: A função aninhada não tem uma assinatura que seja compatível com o delegado '<delegatename>'
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: d65c8eab661675c955ff6562098248c04036d6e7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580647"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>A função aninhada não tem uma assinatura compatível com o delegado ' \<delegatename > '

Uma expressão lambda foi atribuída a um delegado que tem uma assinatura incompatível. Por exemplo, no código a seguir, o `Del` delegado tem dois parâmetros inteiros.

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

O erro será gerado se uma expressão lambda com um argumento for declarada como tipo `Del`:

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

**ID do erro:** BC36532

## <a name="to-correct-this-error"></a>Para corrigir este erro

Ajuste a definição de delegado ou a expressão lambda atribuída para que as assinaturas sejam compatíveis.

## <a name="see-also"></a>Consulte também

- [Conversão de Delegado Reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
