---
title: Operadores boolianos (F#)
description: 'Saiba mais sobre os operadores boolianos que estão disponíveis na linguagem de programação F #.'
ms.date: 05/16/2016
ms.openlocfilehash: faa181090efa7c4064a30b42d83afa4888e98b82
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516627"
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
