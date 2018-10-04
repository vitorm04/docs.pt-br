---
title: Operadores bit a bit (F#)
description: 'Saiba mais sobre os operadores bit a bit que estão disponíveis na linguagem de programação F #.'
ms.date: 07/20/2018
ms.openlocfilehash: ed76fcf5f9c569a2f288cf260e99dc29fd65ef3b
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48581502"
---
# <a name="bitwise-operators"></a>Operadores Bit a Bit

Este tópico descreve os operadores bit a bit que estão disponíveis na linguagem F #.

## <a name="summary-of-bitwise-operators"></a>Resumo de operadores bit a bit

A tabela a seguir descreve os operadores bit a bit com suporte para tipos integrais não demarcados na linguagem F #.

|Operador|Observações|
|--------|-----|
|`&&&`|Operador AND bit a bit. Bits no resultado tem o valor 1 se e somente se os bits correspondentes em ambos os operandos de origem são 1.|
|<code>&#124;&#124;&#124;</code>|Operador OR de bit a bit. Bits no resultado tem o valor 1 se ambos os bits correspondentes na fonte de operandos são 1.|
|`^^^`|Bit a bit operador OR exclusivo. Bits no resultado tem o valor 1 se e somente se bits nos operandos de origem tiverem valores diferentes.|
|`~~~`|Operador de negação bit a bit. Esse é um operador unário e produz um resultado em que todos os bits 0 no operando de origem são convertidos em bits 1 e todos os bits 1 são convertidos em bits 0.|
|`<<<`|Bit a bit operador de deslocamento à esquerda. O resultado é o primeiro operando com os bits deslocados para a esquerda pelo número de bits no segundo operando. Os bits deslocados a posição mais significativa não são girados na posição de menos significativa. Os bits menos significativos são preenchidos com zeros. O tipo do segundo argumento é `int32`.|
|`>>>`|Bit a bit operador de deslocamento à direita. O resultado é o primeiro operando com os bits deslocados para a direita pelo número de bits no segundo operando. Os bits deslocados a menos significativa posição não são girados para a posição mais significativa. Para tipos sem sinal, os bits mais significativos são preenchidos com zeros. Para tipos com sinal com valores negativos, os bits mais significativos são preenchidos com aquelas. O tipo do segundo argumento é `int32`.|

Os seguintes tipos podem ser usados com operadores bit a bit: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, e `unativeint`.

## <a name="see-also"></a>Consulte também

- [Referência de Símbolos e Operadores](index.md)
- [Operadores Aritméticos](arithmetic-operators.md)
- [Operadores Boolianos](boolean-operators.md)
