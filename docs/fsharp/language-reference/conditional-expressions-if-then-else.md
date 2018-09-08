---
title: 'Expressões condicionais: if...then...else (F#)'
description: 'Saiba como escrever expressões condicionais em F # para executar diferentes ramificações do código.'
ms.date: 05/16/2016
ms.openlocfilehash: 10e4224bef772f00520cf5a0fff2f2920147c2fc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177595"
---
# <a name="conditional-expressions-ifthenelse"></a>Expressões condicionais: `if...then...else`

O `if...then...else` expressão executa diferentes ramificações do código e também é avaliada como um valor diferente, dependendo da expressão booliana fornecida.

## <a name="syntax"></a>Sintaxe

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, *expression1* é executado quando a expressão booleana for avaliada como `true`; caso contrário, *expression2* é executado.

Ao contrário em outros idiomas, o `if...then...else` construção é uma expressão, não uma instrução. Isso significa que ele produz um valor, que é o valor da última expressão na ramificação que é executado. Os tipos de valores produzidos em cada ramificação devem corresponder. Se não houver não explícita `else` ramificação, seu tipo é `unit`. Portanto, se o tipo dos `then` ramificação é qualquer tipo diferente de `unit`, deve haver um `else` branch com o mesmo tipo de retorno. Ao encadear `if...then...else` juntas, você pode usar a palavra-chave de expressões `elif` em vez de `else if`; eles são equivalentes.

## <a name="example"></a>Exemplo

O exemplo a seguir ilustra como usar o `if...then...else` expressão.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
