---
title: Operadores boolianos
description: Saiba mais sobre os operadores boolianos que estão disponíveis no F# linguagem de programação.
ms.date: 05/16/2016
ms.openlocfilehash: ad4bdd1121389f7e280647dbe0c4d0098ffb17df
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641886"
---
# <a name="boolean-operators"></a>Operadores boolianos

Este tópico descreve o suporte para operadores boolianos no F# idioma.

## <a name="summary-of-boolean-operators"></a>Resumo de operadores boolianos

A tabela a seguir resume os operadores boolianos que estão disponíveis no F# idioma. O único tipo com suporte desses operadores é o `bool` tipo.

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
