---
title: "Um único tipo de dados (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Single
dev_langs:
- VB
helpviewer_keywords:
- Single data type
- F literal type character
- trailing zeros
- real numbers
- literal type characters, F
- trailing 0 characters
- identifier type characters, !
- single-precision numbers
- '! identifier type character'
- 0 characters, trailing
- data types [Visual Basic], assigning
- floating-point numbers, Single data type
- numbers, real
- zeros, trailing
- numbers, floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: f8153876ce3a957af8b6d3aa9206580a574a7fda
ms.lasthandoff: 03/13/2017

---
# <a name="single-data-type-visual-basic"></a>Tipo de dados único (Visual Basic)
Mantém assinado IEEE de 32 bits (4 bytes) de precisão simples números de ponto flutuante cujo valor varia de - 3, 4028235E + 38 até - 1.401298-45 para valores negativos e de 1, 401298E-45 a 3, 4028235E + 38 para valores positivos. Números de precisão simples armazenam uma aproximação de um número real.  
  
## <a name="remarks"></a>Comentários  
 Use o `Single` tipo de dados para armazenar valores inteiros que não requerem a largura total de dados de `Double`. Em alguns casos, o common language runtime pode ser possível empacotar sua `Single` variáveis próximas uma da outra e economizar memória.  
  
 O valor padrão de `Single` é 0.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Precisão.** Quando você trabalha com números de ponto flutuante, tenha em mente que eles nem sempre têm uma representação precisa na memória. Isso pode levar a resultados inesperados em certas operações, como comparação de valor e o `Mod` operador. Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Ampliação.** O `Single` tipo de dados amplia a `Double`. Isso significa que você pode converter `Single` para `Double` sem encontrar uma <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName>  
  
-   **Os Zeros à direita.** Os tipos de dados de ponto flutuante não possuem uma representação interna de 0 caracteres à direita. Por exemplo, eles não fazem distinção entre 4,2000 e 4,2. Consequentemente, 0 caracteres à direita não aparecem quando você exibe ou imprime valores de ponto flutuante.  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `F` a um literal o força ao tipo de dados `Single`. Acrescentar o caractere de tipo identificador `!` a qualquer identificador o força ao tipo `Single`.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é o <xref:System.Single?displayProperty=fullName>estrutura.</xref:System.Single?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Single?displayProperty=fullName></xref:System.Single?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipo de dados decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)   
 [Tipo de dados Double](../../../visual-basic/language-reference/data-types/double-data-type.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Solução de problemas de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
