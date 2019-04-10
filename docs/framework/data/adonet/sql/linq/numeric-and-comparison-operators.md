---
title: Numérico e operadores de comparação
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 9b31fd2d819afbb1e589ad74f23ec139830c68b8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212161"
---
# <a name="numeric-and-comparison-operators"></a>Numérico e operadores de comparação
Aritmética e operadores de comparação funciona como esperado em Common Language Runtime (CLR) exceto como segue:  
  
-   O SQL não suporta o operador de módulo em números de ponto flutuante.  
  
-   O SQL não oferece suporte a aritmética não-verificada.  
  
-   Operadores de incremento e de redução causam efeitos colaterais quando você usa os em expressões que não podem ser replicadas no SQL e, portanto, não são suportados.  
  
## <a name="supported-operators"></a>Operadores suportados  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oferece suporte a operadores a seguir.  
  
-   Operadores aritméticos básicos:  
  
    -   `+`  
  
    -   `-` (subtração)  
  
    -   `*`  
  
    -   `/`  
  
    -   Divisão de inteiros de Visual Basic (`\`)  
  
    -   `%` (Visual Basic `Mod`)  
  
    -   `<<`  
  
    -   `>>`  
  
    -   `-` (negação unária)  
  
-   Operadores de comparação básicos:  
  
    -   Visual Basic `=` e C#. `==`  
  
    -   Visual Basic `<>` e C#. `!=`  
  
    -   Visual Basic `Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a>Consulte também

- [Tipos de dados e funções](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [Operadores em C#](../../../../../../docs/csharp/language-reference/operators/index.md)
- [Operadores](../../../../../visual-basic/language-reference/operators/index.md)
