---
title: "Tipo de dados SByte (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.sbyte"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipos de dados [Visual Basic], integral"
  - "números inteiros"
  - "números inteiros, tipos de dados"
  - "números inteiros, tipos"
  - "tipos de dados integrais"
  - "números, inteiro"
  - "números, inteiro"
  - "tipo de dados SByte"
  - "números inteiros"
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de dados SByte (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Armazena inteiros de 8 bits com sinal que variam em valor entre \-128 e 127.  
  
## Comentários  
 Use o tipo de dado `SByte` para armazenar valores inteiros que não necessitam de todos os bits de um `Integer` ou até a metade dos bits de um `Short`.  Em alguns casos a commom language runtime pode ser suficiente para armazenar suas variáveis `SByte` próximas uma da outra e diminuir o uso de memória.  
  
 O valor padrão para `SByte` é 0.  
  
## Dicas de Programação  
  
-   **Compatibilidade com CLS.** O tipo de dado `SByte` não é parte de [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)\(CLS\), então um código compatível com CLS não pode consumir um componente que o utilize.  
  
-   **Tipos de dados.** The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.  Isto significa que você pode converter um `SByte` para qualqer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Digitar caracteres.** `SByte` não tem nenhum caractere de tipo literal ou um caractere de tipo de identificador.  
  
-   **Tipos de Framework.** O tipo correspondente na.NET Framework é o <xref:System.SByte?displayProperty=fullName> estrutura.  
  
## Consulte também  
 <xref:System.SByte?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Tipo de dados curto](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Tipo de dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)