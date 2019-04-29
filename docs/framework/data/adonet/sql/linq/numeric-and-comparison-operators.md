---
title: Numérico e operadores de comparação
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: b29f78a13d6d0313e0ad29754f6d13ac08be1092
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783130"
---
# <a name="numeric-and-comparison-operators"></a>Numérico e operadores de comparação

Aritmética e operadores de comparação funciona como esperado em Common Language Runtime (CLR) exceto como segue:

- O SQL não suporta o operador de módulo em números de ponto flutuante.

- O SQL não oferece suporte a aritmética não-verificada.

- Operadores de incremento e de redução causam efeitos colaterais quando você usa os em expressões que não podem ser replicadas no SQL e, portanto, não são suportados.

## <a name="supported-operators"></a>Operadores suportados

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oferece suporte aos seguintes operadores.

- Operadores aritméticos básicos:

  - `+`

  - `-` (subtração)

  - `*`

  - `/`

  - Divisão de inteiros de Visual Basic (`\`)

  - `%` (Visual Basic) `Mod`

  - `<<`

  - `>>`

  - `-` (negação unária)

- Operadores de comparação básicos:

  - `=` Visual Basic e C# `==`

  - `<>` Visual Basic e C# `!=`

  - Visual Basic `Is/IsNot`

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a>Consulte também

- [Funções e tipos de dados](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [Operadores do C#](../../../../../../docs/csharp/language-reference/operators/index.md)
- [Operadores](../../../../../visual-basic/language-reference/operators/index.md)
