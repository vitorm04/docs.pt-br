---
title: Tipo de dados único
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
ms.openlocfilehash: 60a688c510f6e36dca5809566b37a388429e18c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343925"
---
# <a name="single-data-type-visual-basic"></a>Tipo de dados único (Visual Basic)

Contém números de ponto flutuante de precisão simples IEEE 32 bits (4 bytes) que variam em valor de-3.4028235 E + 38 a-1.401298 E-45 para valores negativos e de 1.401298 E-45 a 3.4028235 E + 38 para valores positivos. Números de precisão única armazenam uma aproximação de um número real.  
  
## <a name="remarks"></a>Comentários  

 Use o tipo de dados `Single` para conter valores de ponto flutuante que não exigem a largura total dos dados de `Double`. Em alguns casos, a Common Language Runtime pode ser capaz de empacotar suas variáveis de `Single` em conjunto e economizar o consumo de memória.  
  
 O valor padrão de `Single` é 0.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
- **Preciso.** Quando você trabalha com números de ponto flutuante, tenha em mente que eles nem sempre têm uma representação precisa na memória. Isso pode levar a resultados inesperados de determinadas operações, como comparação de valor e o operador de `Mod`. Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
- **Ampliação.** O tipo de dados `Single` amplia a `Double`. Isso significa que você pode converter `Single` em `Double` sem encontrar um erro <xref:System.OverflowException?displayProperty=nameWithType>.  
  
- **Zeros à direita.** Os tipos de dados de ponto flutuante não têm nenhuma representação interna de zero caracteres à direita. Por exemplo, eles não fazem distinção entre 4,2000 e 4,2. Consequentemente, 0 caracteres à direita não aparecem quando você exibe ou imprime valores de ponto flutuante.  
  
- **Digite os caracteres.** Acrescentar o caractere de tipo literal `F` a um literal o força ao tipo de dados `Single`. Acrescentar o caractere de tipo identificador `!` a qualquer identificador o força ao tipo `Single`.  
  
- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Single?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Single?displayProperty=nameWithType>
- [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)
- [Tipo de Dados Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Tipo de Dados Duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Solução de problemas de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
