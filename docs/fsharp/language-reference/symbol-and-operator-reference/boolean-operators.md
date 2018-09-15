---
title: Operadores boolianos (F#)
description: 'Saiba mais sobre os operadores boolianos que estão disponíveis na linguagem de programação F #.'
ms.date: 05/16/2016
ms.openlocfilehash: faa181090efa7c4064a30b42d83afa4888e98b82
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638474"
---
# <a name="boolean-operators"></a>Operadores boolianos

Este tópico descreve o suporte para operadores boolianos na linguagem F #.

## <a name="summary-of-boolean-operators"></a>Resumo de operadores boolianos

A tabela a seguir resume os operadores boolianos que estão disponíveis na linguagem F #. O único tipo com suporte desses operadores é o `bool` tipo.

|Operador|Descrição|
|--------|-----------|
|`not`|Boleana|
|<code>&#124;&#124;</code>|Booliano OR|
|`&&`|Booliano AND|

Executam o booliano e e/ou operadores *avaliação curto-circuito*, ou seja, eles avaliar a expressão à direita do operador somente quando for necessário determinar o resultado geral da expressão. A segunda expressão do `&&` operador é avaliado somente se a primeira expressão é avaliada como `true`; a segunda expressão do `||` operador é avaliado somente se a primeira expressão é avaliada como `false`.

## <a name="see-also"></a>Consulte também

- [Operadores Bit a Bit](bitwise-operators.md)
- [Operadores Aritméticos](arithmetic-operators.md)
- [Referência de Símbolos e Operadores](index.md)
