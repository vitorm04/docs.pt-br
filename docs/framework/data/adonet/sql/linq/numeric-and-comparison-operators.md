---
title: Numérico e operadores de comparação
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 733c1e494c29f04aa06a4159c3b1dae219f01b44
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180330"
---
# <a name="numeric-and-comparison-operators"></a>Numérico e operadores de comparação
Aritmética e operadores de comparação funciona como esperado em Common Language Runtime (CLR) exceto como segue:  
  
-   O SQL não suporta o operador de módulo em números de ponto flutuante.  
  
-   O SQL não oferece suporte a aritmética não-verificada.  
  
-   Operadores de incremento e de redução causam efeitos colaterais quando você usa os em expressões que não podem ser replicadas no SQL e, portanto, não são suportados.  
  
## <a name="supported-operators"></a>Operadores suportados  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oferece suporte aos seguintes operadores.  
  
-   Operadores aritméticos básicos:  
  
    -   `+`  
  
    -   `-` (subtração)  
  
    -   `*`  
  
    -   `/`  
  
    -   Divisão de inteiros de Visual Basic (`\`)  
  
    -   `%` (Visual Basic) `Mod`  
  
    -   `<<`  
  
    -   `>>`  
  
    -   `-` (negação unária)  
  
-   Operadores de comparação básicos:  
  
    -   `=` Visual Basic e C# `==`  
  
    -   `<>` Visual Basic e C# `!=`  
  
    -   Visual Basic `Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a>Consulte também  
 [Funções e tipos de dados](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [Operadores do C#](../../../../../../docs/csharp/language-reference/operators/index.md)  
 [Operadores](../../../../../visual-basic/language-reference/operators/index.md)
