---
title: Tipo de dados Double (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Double
dev_langs:
- VB
helpviewer_keywords:
- 'identifier type characters, #'
- trailing zeros
- real numbers
- trailing 0 characters
- 0 characters, trailing
- literal type characters, R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers, Double data type
- R literal type character
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1f831acf62cad973171a16bde09cde4a56b8d6a0
ms.lasthandoff: 03/13/2017

---
# <a name="double-data-type-visual-basic"></a>Tipo de dados double (Visual Basic)
Mantém assinado IEEE de 64 bits (8 bytes) de precisão dupla números de ponto flutuante que variam em valor entre - 1, 79769313486231570E + 308 até - 4.94065645841246544 e-324 para valores negativos e de 4.94065645841246544 e-324 1.79769313486231570 e + 308 para valores positivos. Números de precisão dupla armazenam uma aproximação de um número real.  
  
## <a name="remarks"></a>Comentários  
 O `Double` tipo de dados fornece a maior e menor magnitude possível para um número.  
  
 O valor padrão de `Double` é 0.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Precisão.** Quando você trabalha com números de ponto flutuante, lembre-se de que eles nem sempre têm uma representação precisa na memória. Isso pode levar a resultados inesperados em certas operações, como comparação de valor e o `Mod` operador. Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Os Zeros à direita.** Os tipos de dados de ponto flutuante não possuem uma representação interna de zero caracteres à direita. Por exemplo, eles não fazem distinção entre 4,2000 e 4,2. Consequentemente, zero caracteres à direita não aparecem quando você exibe ou valores de ponto flutuante de impressão.  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `R` a um literal o força ao tipo de dados `Double`. Por exemplo, se um valor inteiro é seguido por `R`, o valor é alterado para um `Double`.  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     Acrescentar o caractere de tipo identificador `#` a qualquer identificador o força ao tipo `Double`. No exemplo a seguir, a variável `num` é digitado como um `Double`:  
  
    ```  
    Dim num# = 3  
    ```  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é o <xref:System.Double?displayProperty=fullName>estrutura.</xref:System.Double?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Double?displayProperty=fullName></xref:System.Double?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipo de dados decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)   
 [Tipo de dados Single](../../../visual-basic/language-reference/data-types/single-data-type.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Caracteres de Tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
