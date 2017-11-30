---
title: Operadores bit a bit (F#)
description: "Saiba mais sobre os operadores bit a bit que estão disponíveis no F # linguagem de programação."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8a2c87f5-b4c7-47fe-8580-82c956f605e5
ms.openlocfilehash: 61a8e6bafe97a229480c967a4afb5d2a256474c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="bitwise-operators"></a>Operadores Bit a Bit

Este tópico descreve os operadores bit a bit que estão disponíveis na linguagem F #.

## <a name="summary-of-bitwise-operators"></a>Resumo de operadores bit a bit
A tabela a seguir descreve os operadores bit a bit com suporte para tipos integrais não demarcados em linguagem F #.

|Operador|Observações|
|--------|-----|
|`&&&`|Operador AND bit a bit. Bits no resultado tem o valor 1 se e somente se os bits correspondentes em ambos os operandos de origem são de 1.|
|<code>&#124;&#124;&#124;</code>|Operador OR bit a bit. Bits no resultado tem o valor 1 se os bits correspondentes na fonte de operandos são 1.|
|`^^^`|Bit a bit operador OR exclusivo. Bits no resultado tem o valor 1 se e somente se bits nos operandos de origem têm valores diferentes.|
|`~~~`|Operador de negação bit a bit. Este é um operador unário e produz um resultado em que todos os bits 0 do operando de origem são convertidos em bits 1 e todos os bits 1 são convertidos em bits 0.|
|`<<<`|Bit a bit operador left shift. O resultado é que o primeiro operando com os bits deslocados esquerda pelo número de bits no segundo operando. Bits deslocadas a posição mais significativa não são girados na posição menos significativa. Os bits menos significativos são preenchidos com zeros. O tipo do segundo argumento é `int32`.|
|`>>>`|Bit a bit operador right shift. O resultado é o primeiro operando com bits deslocados direita pelo número de bits no segundo operando. Bits deslocadas a posição menos significativa não são girados para a posição mais significativa. Para tipos não assinados, os bits mais significativos são preenchidos com zeros. Para tipos assinados, os bits mais significativos são preenchidos com aquelas. O tipo do segundo argumento é `int32`.|

Os tipos a seguir podem ser usados com operadores bit a bit: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, e `unativeint`.

## <a name="see-also"></a>Consulte também
[Referência de Símbolos e Operadores](index.md)

[Operadores Aritméticos](arithmetic-operators.md)

[Operadores Boolianos](boolean-operators.md)

