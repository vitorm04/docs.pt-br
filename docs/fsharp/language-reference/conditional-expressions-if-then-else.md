---
title: "Expressões condicionais: if...then...else (F#)"
description: "Saiba como escrever expressões condicionais em F # para executar diferentes ramos do código."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e1871c-4d4d-4691-9ab2-bd2c6f65589a
ms.openlocfilehash: 3531a112eb53657d5e9102d5e5f3be988360b76e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="conditional-expressions-ifthenelse"></a>Expressões condicionais:`if...then...else`

O `if...then...else` expressão executa ramificações diferentes do código e também é avaliada como um valor diferente dependendo da expressão booliana fornecido.


## <a name="syntax"></a>Sintaxe

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>Comentários
Na sintaxe anterior, *expression1* é executado quando a expressão booleana for avaliada como `true`; caso contrário, *expression2* é executado.

Ao contrário em outros idiomas, o `if...then...else` construção é uma expressão, não uma instrução. Isso significa que ele produz um valor, que é o valor da última expressão na ramificação que é executado. Os tipos de valores produzidos em cada ramificação devem corresponder. Se não houver explícita não `else` ramificação, seu tipo é `unit`. Portanto, se o tipo do `then` ramificação for qualquer tipo diferente de `unit`, deve haver um `else` branch com o mesmo tipo de retorno. Ao encadear `if...then...else` expressões juntas, você pode usar a palavra-chave `elif` em vez de `else if`; eles são equivalentes.

## <a name="example"></a>Exemplo
O exemplo a seguir ilustra como usar o `if...then...else` expressão.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
John
910 is less than 20
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

