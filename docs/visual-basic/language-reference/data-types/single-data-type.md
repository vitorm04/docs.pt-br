---
title: Tipo de dados único (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: 98433c0f1d1008664bb994f3b43fe48a753a432c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483639"
---
# <a name="single-data-type-visual-basic"></a>Tipo de dados único (Visual Basic)
Mantém conectado IEEE de 32 bits (4 bytes) de precisão simples números de ponto flutuante que variam em valor de - 3,4028235E + 38 a - 1,401298E-45 para valores negativos e de 1,401298E-45 3,4028235E + 38 para valores positivos. Números de precisão simples armazenam uma aproximação de um número real.  
  
## <a name="remarks"></a>Comentários  
 Use o `Single` tipo de dados para conter os valores de ponto flutuante que não exigem a largura de dados completo do `Double`. Em alguns casos, o common language runtime pode ser capaz de empacotar seu `Single` variáveis próximas uma da outra e economizar memória.  
  
 O valor padrão de `Single` é 0.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Precisão.** Quando você trabalha com números de ponto flutuante, lembre-se de que eles nem sempre têm uma representação precisa na memória. Isso pode levar a resultados inesperados em certas operações, como comparação de valor e o `Mod` operador. Para obter mais informações, consulte [solução de problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Ampliação.** O `Single` tipo de dados é ampliado para `Double`. Isso significa que você pode converter `Single` à `Double` sem encontrar uma <xref:System.OverflowException?displayProperty=nameWithType> erro.  
  
-   **Zeros à direita.** Os tipos de dados de ponto flutuante não possuem uma representação interna de 0 caracteres à direita. Por exemplo, eles não fazem distinção entre 4,2000 e 4.2. Consequentemente, 0 caracteres à direita não aparecem quando você exibe ou imprimir valores de ponto flutuante.  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `F` a um literal o força ao tipo de dados `Single`. Acrescentar o caractere de tipo identificador `!` a qualquer identificador o força ao tipo `Single`.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Single?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Single?displayProperty=nameWithType>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)  
 [Tipo de Dados Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Tipo de Dados Duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Solução de problemas de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
