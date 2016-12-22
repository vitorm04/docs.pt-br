---
title: "Tipo de dados ULong (Visual Basic) | Microsoft Docs"
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
  - "vb.ulong"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipos de dados [Visual Basic], integral"
  - "números inteiros"
  - "números inteiros, tipos de dados"
  - "números inteiros, tipos"
  - "tipos de dados integrais"
  - "caracteres de tipo literal, UL"
  - "números, inteiro"
  - "números, inteiro"
  - "caracteres de tipo literal UL"
  - "tipo de dados ULong"
  - "números inteiros"
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de dados ULong (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Pode conter inteiros de 64 bits \(8 bytes\), sem\-sinal, com valor variando de 0 a 18.446.744.073.709.551.615 \(mais do que 1,84 vezes 10 ^ 19\).  
  
## Comentários  
 Use o tipo de dados `ULong` para armazenar dados binários muito grandes para `UInteger`, ou os maiores valores inteiros sem\-sinal possíveis.  
  
 O valor padrão para `ULong` é 0.  
  
## Dicas de Programação  
  
-   **Números negativos.** Porque `ULong` é um tipo não assinado, ele não pode representar um número negativo.  Se você usar o operador unário menos \(`-`\) ou uma expressão avaliada como tipo `ULong`, o Visual Basic converte a expressão para  `Decimal` primeiramente.  
  
-   **Compatibilidade com CLS.** O tipo de dado `ULong` não é parte de [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)\(CLS\), então um código compatível com CLS não pode consumir um componente que o utilize.  
  
-   **Considerações de interoperabilidade.** Se você está em uma interface com componentes não escritos para o.NET Framework, para objetos de automação ou COM exemplo, tenha em mente que os tipos, como `ulong` pode ter uma largura de dados diferentes \(32 bits\) em outros ambientes.  Se você estiver passando um argumento de 32 bits para tal componente, declare\-o como `UInteger` em vez de `ULong` no seu código Visual Basic gerenciado.  
  
     Além disso, automação não oferece suporte a inteiros de 64 bits no Windows 95, Windows 98, Windows ME ou Windows 2000.  Você não pode passar um Visual Basic `ULong` argumento para um componente de automação nessas plataformas.  
  
-   **Tipos de dados.** The `ULong` data type widens to `Decimal`, `Single`, and `Double`.  Isto significa que você pode converter um `ULong` para qualqer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Caracteres de tipo.** Acrescentando os caracteres do tipo literal `UL` para um literal, força\-o para o `ULong` tipo de dados.  `ULong`não tem nenhum caractere de tipo de identificador.  
  
-   **Tipos de Framework.** O tipo correspondente na.NET Framework é o <xref:System.UInt64?displayProperty=fullName> estrutura.  
  
## Consulte também  
 <xref:System.UInt64>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Como chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)