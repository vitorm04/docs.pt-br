---
title: Operadores boolianos (F#)
description: "Saiba mais sobre os operadores booleanos que estão disponíveis no F # linguagem de programação."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f79370b8-4bc2-4704-b514-d392c80942bd
ms.openlocfilehash: 63588f2e371bf2c0f15de0b8a26a46be82f832c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
