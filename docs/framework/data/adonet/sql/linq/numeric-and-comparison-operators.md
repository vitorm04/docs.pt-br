---
title: Numérico e operadores de comparação
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 7e7af725864aa191f092055fa32b403093321aa5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781285"
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

  - Divisão de inteiro Visual Basic`\`()

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

- [Funções e tipos de dados](data-types-and-functions.md)
- [Operadores do C#](../../../../../csharp/language-reference/operators/index.md)
- [Operadores](../../../../../visual-basic/language-reference/operators/index.md)
