---
title: "Tipo de dados &#250;nico (Visual Basic) | Microsoft Docs"
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
  - "vb.Single"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "caractere de tipo identificador !"
  - "0 caracteres, à direita"
  - "tipos de dados [Visual Basic], atribuindo"
  - "caractere de tipo literal F"
  - "números de ponto flutuante, tipo de dados Single"
  - "caracteres de tipo identificador, !"
  - "caracteres de tipo literal, F"
  - "números, ponto flutuante"
  - "números, real"
  - "números reais"
  - "tipo de dados Single"
  - "números de precisão única"
  - "0 caracteres à direita"
  - "zeros à direita"
  - "zeros, à direita"
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de dados &#250;nico (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Armazena números ponto flutuante de precisão simples assinados com IEEE de 32 bits e variando do valor de \- 3.4028235E \+ 38 até \-1.401298E \- 45 para valores negativos e de 1, 401298E \- 45 a 3.4028235E \+ 38 para valores positivos.  Números de precisão simples armazenam uma aproximação de um número real.  
  
## Comentários  
 Use o tipo de dado `Single` para armazenar valores inteiros que não necessitam de todos os bits de um `Double`.  Em alguns casos a commom language runtime pode ser suficiente para armazenar suas variáveis `Single` próximas uma da outra e diminuir o uso de memória.  
  
 O valor padrão para `Single` é 0.  
  
## Dicas de Programação  
  
-   **Precisão.** Quando você trabalha com números de ponto flutuante, lembre que eles nem sempre têm uma representação precisa na memória.  Isso pode levar a resultados inesperados em certas operações, com comparação de valores e com o operador `Mod`.  Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Tipos de dados.** O `Single` tipo de dados amplia a `Double`.  Isso significa que você pode converter `Single` para `Double` sem encontrar um erro <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Zeros à direita.** Os tipos de dados de ponto flutuante não tem qualquer representação interna de trilha 0 caracteres.  Por exemplo, eles não fazem distinção entre 4,2000 e 4,2.  Consequentemente, caracteres de zeros à direita não aparecem quando você exibe ou imprime valores de ponto flutuante.  
  
-   **Caracteres de tipo.** Acrescentando o caractere de tipo literal `F` para um literal, força\-o para o `Single` tipo de dados.  Acrescentar o caractere de tipo identificador `!` a qualquer identificador o força ao tipo `Single`.  
  
-   **Tipos de Framework.** O tipo correspondente na.NET Framework é o <xref:System.Single?displayProperty=fullName> estrutura.  
  
## Consulte também  
 <xref:System.Single?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipo de dados decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)   
 [Tipo de dados double](../../../visual-basic/language-reference/data-types/double-data-type.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)