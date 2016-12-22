---
title: "Tipo de dados UShort (Visual Basic) | Microsoft Docs"
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
  - "vb.ushort"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipos de dados [Visual Basic], integral"
  - "números inteiros"
  - "números inteiros, tipos de dados"
  - "números inteiros, tipos"
  - "tipos de dados integrais"
  - "caracteres de tipo literal, US"
  - "números, inteiro"
  - "números, inteiro"
  - "caracteres de tipo literal US"
  - "tipo de dados UShort"
  - "números inteiros"
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de dados UShort (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Contém números inteiros sem\-sinal de 16 bits \(2 bytes\) variando de 0 a 65.535.  
  
## Comentários  
 Use o tipo de dados `UShort` para conter dados binários grandes demais para `Byte`.  
  
 O valor padrão para `UShort` é 0.  
  
## Dicas de Programação  
  
-   **Números negativos.** Porque `UShort` é um tipo não assinado, ele não pode representar um número negativo.  Se você usar o operador unário menos \(`-`\) ou uma expressão avaliada como tipo `UShort`, o Visual Basic converte a expressão para  `Integer` primeiramente.  
  
-   **Compatibilidade com CLS.** O tipo de dado `UShort` não é parte de [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)\(CLS\), então um código compatível com CLS não pode consumir um componente que o utilize.  
  
-   **Tipos de dados.** The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.  Isto significa que você pode converter um `UShort` para qualqer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Caracteres de tipo.** Acrescentando os caracteres do tipo literal `US` para um literal, força\-o para o `UShort` tipo de dados.  `UShort`não tem nenhum caractere de tipo de identificador.  
  
-   **Tipos de Framework.** O tipo correspondente na.NET Framework é o <xref:System.UInt16?displayProperty=fullName> estrutura.  
  
## Consulte também  
 <xref:System.UInt16>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Como chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)