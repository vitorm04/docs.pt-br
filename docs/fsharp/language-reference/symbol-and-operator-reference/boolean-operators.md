---
title: Operadores boolianos (F#)
description: 'Saiba mais sobre os operadores booleanos que estão disponíveis no F # linguagem de programação.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0b11b5133b02b6f507c7886b2fbaebf30abf46cb
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="boolean-operators"></a>Operadores boolianos

Este tópico descreve o suporte para operadores boolianos na linguagem F #.


## <a name="summary-of-boolean-operators"></a>Resumo de operadores boolianos
A tabela a seguir resume os operadores booleanos que estão disponíveis na linguagem F #. O único tipo com suporte desses operadores é o `bool` tipo.

|Operador|Descrição|
|--------|-----------|
|`not`|Boleana|
|<code>&#124;&#124;</code>|Booliano OR|
|`&&`|Boolean e|

Executam o Boolean e e/ou operadores *avaliação de curto-circuito*, ou seja, elas avaliam a expressão à direita do operador somente quando é necessário determinar o resultado geral da expressão. A segunda expressão do `&&` operador é avaliado apenas se a primeira expressão for avaliada como `true`; a segunda expressão do `||` operador é avaliado apenas se a primeira expressão for avaliada como `false`.

## <a name="see-also"></a>Consulte também
[Operadores Bit a Bit](bitwise-operators.md)

[Operadores Aritméticos](arithmetic-operators.md)

[Referência de Símbolos e Operadores](index.md)
