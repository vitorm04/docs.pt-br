---
title: "Tipo de dados inteiro (Visual Basic) | Microsoft Docs"
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
  - "vb.Integer"
  - "Integer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "caractere de tipo identificador %"
  - "tipos de dados [Visual Basic], atribuindo"
  - "tipos de dados [Visual Basic], integral"
  - "valores enumerados"
  - "caractere de tipo literal I"
  - "caracteres de tipo identificador, %"
  - "tipo de dados Integer"
  - "números inteiros"
  - "números inteiros, tipos de dados"
  - "números inteiros, tipos"
  - "tipos de dados integrais"
  - "caracteres de tipo literal, I"
  - "números, inteiro"
  - "números, inteiro"
  - "números inteiros"
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de dados inteiro (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Armazena inteiros de 32 bits \(4 bytes\) com sinal que variam em valor de \-2.147.483.648 a 2.147.483.647.  
  
## Comentários  
 O tipo de dados `Integer` proporciona um desempenho ideal em um processador de 32 bits.  Os outros tipos integrais são mais lentos para carregar e armazenar na memória.  
  
 O valor padrão de `Integer` é 0.  
  
## Dicas de programação  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, lembre\-se de que `Integer` possui uma largura de dados diferente \(16 bits\) em outros ambientes.  Se você estiver passando um argumento de 16 bits para esse componente, declare\-o como `Short` em vez de `Integer` no seu novo código do Visual Basic.  
  
-   **Ampliação.** O tipo de dados `Integer` é ampliado para `Long`, `Decimal`, `Single` ou `Double`.  Isso significa que você pode converter `Integer` em qualquer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `I` a um literal o força ao tipo de dados `Integer`.  Acrescentar o caractere de tipo identificador `%` a qualquer identificador o força ao tipo `Integer`.  
  
-   **Tipos de framework.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Int32?displayProperty=fullName>.  
  
## Intervalo  
 Se você tentar definir uma variável de um tipo integral para um número fora do intervalo para esse tipo, ocorrerá um erro.  Se você tentar defini\-lo como uma fração, o número será arredondado para cima ou para baixo para o valor inteiro mais próximo.  Se o número for igualmente próximo de dois valores inteiros, o valor será arredondado para o inteiro par mais próximo.  Esse comportamento minimiza erros de arredondamento gerados ao arredondar consistentemente um valor de ponto médio em uma única direção.  O código a seguir mostra exemplos de arredondamento.  
  
```  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```  
  
## Consulte também  
 <xref:System.Int32?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipo de dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md)   
 [Tipo de dados curto](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)