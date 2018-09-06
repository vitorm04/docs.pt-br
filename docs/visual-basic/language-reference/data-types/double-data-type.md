---
title: Tipo de dados double (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: 5d2d84f298b9cf6138e84ef287f6ea9212da2960
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43806118"
---
# <a name="double-data-type-visual-basic"></a>Tipo de dados double (Visual Basic)
Mantém conectado IEEE de 64 bits (8 bytes) de precisão dupla números de ponto flutuante que variam em valor de - 1, 79769313486231570E + 308 a - 4.94065645841246544-324 para valores negativos e de 4.94065645841246544-324 1.79769313486231570 + 308 para valores positivos. Números de precisão dupla armazenam uma aproximação de um número real.  
  
## <a name="remarks"></a>Comentários  
 O `Double` tipo de dados fornece o maior e menor magnitude possível para um número.  
  
 O valor padrão de `Double` é 0.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Precisão.** Quando você trabalha com números de ponto flutuante, lembre-se de que eles nem sempre têm uma representação precisa na memória. Isso pode levar a resultados inesperados em certas operações, como comparação de valor e o `Mod` operador. Para obter mais informações, consulte [solução de problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Zeros à direita.** Os tipos de dados de ponto flutuante não possuem uma representação interna de zero caracteres à direita. Por exemplo, eles não fazem distinção entre 4,2000 e 4.2. Consequentemente, zero caracteres à direita não aparecem quando você exibe ou valores de ponto flutuante de impressão.  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `R` a um literal o força ao tipo de dados `Double`. Por exemplo, se um valor inteiro é seguido por `R`, o valor é alterado para um `Double`.  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     Acrescentar o caractere de tipo identificador `#` a qualquer identificador o força ao tipo `Double`. No exemplo a seguir, a variável `num` é digitada como um `Double`:  
  
    ```  
    Dim num# = 3  
    ```  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Double?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Double?displayProperty=nameWithType>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)  
 [Tipo de Dados Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Tipo de Dados Simples](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Solução de problemas de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Caracteres de Tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
