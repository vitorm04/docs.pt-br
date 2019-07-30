---
title: 'Expressões condicionais: If... Então... restante'
description: Saiba como escrever expressões condicionais no F# para executar diferentes ramificações de código.
ms.date: 05/16/2016
ms.openlocfilehash: 825149bf296eded3cc2b4d8847ba4d82bea40cdc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630395"
---
# <a name="conditional-expressions-ifthenelse"></a>Expressões condicionais:`if...then...else`

A `if...then...else` expressão executa diferentes ramificações de código e também é avaliada como um valor diferente, dependendo da expressão booliana fornecida.

## <a name="syntax"></a>Sintaxe

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, *expressão1* é executado quando a expressão booliana é avaliada como `true`; caso contrário, a *expression2* é executada.

Ao contrário de outras linguagens `if...then...else` , a construção é uma expressão, não uma instrução. Isso significa que ele produz um valor, que é o valor da última expressão na ramificação que é executada. Os tipos dos valores produzidos em cada ramificação devem corresponder. Se não houver nenhuma ramificação explícita `else` , seu tipo será. `unit` Portanto, se o tipo da `then` ramificação for qualquer tipo diferente de `unit`, deve haver uma `else` ramificação com o mesmo tipo de retorno. Ao encadear `if...then...else` expressões juntas, você pode usar a palavra `elif` -chave `else if`em vez de; elas são equivalentes.

## <a name="example"></a>Exemplo

O exemplo a seguir ilustra como usar a `if...then...else` expressão.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
