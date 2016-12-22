---
title: "Tipo de dados double (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Double"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "caractere de tipo identificador #"
  - "0 caracteres, à direita"
  - "tipos de dados [Visual Basic], atribuindo"
  - "tipo de dados Double"
  - "tipo de dados Double [Visual Basic]"
  - "números de precisão dupla"
  - "números de ponto flutuante, tipo de dados Double"
  - "caracteres de tipo identificador, #"
  - "caracteres de tipo literal, R"
  - "caractere de tipo literal R"
  - "números reais"
  - "0 caracteres à direita"
  - "zeros à direita"
  - "zeros, à direita"
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de dados double (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Suporta números de ponto flutuante com precisão dupla sinalizados IEEE de 64\-bits \(8\-bytes\) com intervalo de \-1.79769313486231570E\+308 até \-4.94065645841246544E\-324 para valores negativos e de 4.94065645841246544E\-324 para 1.79769313486231570E\+308 para valores positivos.  Números de precisão dupla armazenam uma aproximação de um número real.  
  
## Comentários  
 O tipo de dado `Double` provê a maior e a menor magnitude possível para um número.  
  
 O valor padrão para `Double` é 0.  
  
## Dicas de Programação  
  
-   **Precisão.** Quando você trabalha com números de ponto flutuante, lembre que eles nem sempre têm uma representação precisa na memória.  Isso pode levar a resultados inesperados em certas operações, com comparação de valores e com o operador `Mod`.  Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Zeros à direita.** Os tipos de dado de ponto flutuante não possuem uma representação interna para os caracteres de zeros à direita.  Por exemplo, eles não fazem distinção entre 4,2000 e 4,2.  Consequentemente, caracteres de zeros à direita não aparecem quando você exibe ou imprime valores de ponto flutuante.  
  
-   **Caracteres de tipo.** Acrescentando o caractere de tipo literal `R` para um literal, força\-o para o `Double` tipo de dados.  Por exemplo, se um valor inteiro é seguido por `R`, o valor é alterado para um `Double`.  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     Acrescentar o caractere de tipo identificador `#` a qualquer identificador o força ao tipo `Double`.  No exemplo a seguir, a variável `num` é digitada como uma `Double`:  
  
    ```  
    Dim num# = 3  
    ```  
  
-   **Tipos de Framework.** O tipo correspondente na.NET Framework é o <xref:System.Double?displayProperty=fullName> estrutura.  
  
## Consulte também  
 <xref:System.Double?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipo de dados decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)   
 [Tipo de dados único](../../../visual-basic/language-reference/data-types/single-data-type.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Caracteres de tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)