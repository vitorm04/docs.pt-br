---
title: O tipo de '<variablename>' não pode ser inferido porque os limites de loop e a variável step não são ampliados com o mesmo tipo
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: c3086f79fb71693810bc8f14e8c0f493aa1e6515
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512714"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>O tipo de\<' VariableName > ' não pode ser inferido porque os limites do loop e a variável Step não se ampliam ao mesmo tipo

Você escreveu um `For...Next` loop no qual o compilador não pode inferir um tipo de dados para a variável de controle de loop porque as seguintes condições são verdadeiras:

- O tipo de dados da variável de controle de loop não é especificado `As` com uma cláusula.

- Os limites do loop e a variável Step contêm pelo menos dois tipos de dados.

- Não existem conversões padrão entre os tipos de dados.

 Portanto, o compilador não pode inferir o tipo de dados da variável de controle de um loop.

 No exemplo a seguir, a variável Step é um caractere e os limites do loop são inteiros. Como não há conversão padrão entre caracteres e inteiros, esse erro é relatado.

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

**ID do erro:** BC30982

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Altere os tipos dos limites do loop e da variável Step conforme necessário para que pelo menos um deles seja um tipo que os outros ampliam. No exemplo anterior, altere o tipo de `stepVar` para. `Integer`

  ```vb
  Dim stepVar = 1
  ```

  - ou -

  ```vb
  Dim stepVar As Integer = 1
  ```

- Use funções de conversão explícitas para converter os limites do loop e a variável Step para os tipos apropriados. No exemplo anterior, aplique a `Val` função a. `stepVar`

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
