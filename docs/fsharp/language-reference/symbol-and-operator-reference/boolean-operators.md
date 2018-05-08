---
title: Operadores boolianos (F#)
description: 'Saiba mais sobre os operadores booleanos que estão disponíveis no F # linguagem de programação.'
ms.date: 05/16/2016
ms.openlocfilehash: f8516ceb531907400f98dc4226d2985d3119e9e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
