---
title: "Tipo de dados UInteger | Microsoft Docs"
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
  - "vb.uinteger"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipos de dados [Visual Basic], integral"
  - "números inteiros"
  - "números inteiros, tipos de dados"
  - "números inteiros, tipos"
  - "tipos de dados integrais"
  - "caracteres de tipo literal, IU"
  - "números, inteiro"
  - "números, inteiro"
  - "caracteres de tipo literal de interface do usuário"
  - "tipo de dados UInteger"
  - "números inteiros"
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de dados UInteger
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Contém números inteiros sem sinal de 32 bits \(4 bytes\) variando de 0 a 4.294.967.295.  
  
## Comentários  
 O `UInteger` tipo de dados fornece o maior valor não assinado à largura de dados mais eficiente.  
  
 O valor padrão para `UInteger` é 0.  
  
## Dicas de Programação  
 O `UInteger` e `Integer` tipos de dados fornecem um desempenho ideal em um processador de 32 bits, porque os tipos de inteiro menores \(`UShort`, `Short`, `Byte`, e `SByte`\), mesmo que eles usam menos bits, levar mais tempo para carregar, armazenar e buscar.  
  
-   **Números negativos.** Porque `UInteger` é um tipo não assinado, ele não pode representar um número negativo.  Se você usar o operador unário menos \(`-`\) ou uma expressão avaliada como tipo `UInteger`, Visual Basic converte a expressão para  `Long`, primeiramente.  
  
-   **Compatibilidade com CLS.** O tipo de dado `UInteger` não é parte de [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)\(CLS\), então um código compatível com CLS não pode consumir um componente que o utilize.  
  
-   **Considerações de Interoperabilidade.** Se você está em uma interface com componentes não escritos para o.NET Framework, para objetos de automação ou COM exemplo, tenha em mente que os tipos, como `uint` pode ter uma largura de dados diferentes \(16 bits\) em outros ambientes.  Se você estiver passando um argumento de 16 bits para tal componente, declare\-o como `UShort` em vez de `UInteger` no seu código Visual Basic gerenciado.  
  
-   **Tipos de dados.** The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.  Isto significa que você pode converter um `UInteger` para qualquer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Caracteres de Tipo.** Acrescentando os caracteres do tipo literal `UI` para um literal, força\-o para o `UInteger` tipo de dados.  `UInteger`não tem nenhum caractere de tipo de identificador.  
  
-   **Tipo de Framework.** O tipo correspondente na.NET Framework é o <xref:System.UInt32?displayProperty=fullName> estrutura.  
  
## Consulte também  
 <xref:System.UInt32>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Como chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)