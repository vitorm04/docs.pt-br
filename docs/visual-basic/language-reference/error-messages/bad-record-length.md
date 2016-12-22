---
title: "Comprimento de registro inv&#225;lido | Microsoft Docs"
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
  - "vbrID59"
dev_langs: 
  - "VB"
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Comprimento de registro inv&#225;lido
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Dentre as causas possíveis desse erro, estão:  
  
-   O comprimento de uma variável do registro especificada em uma instrução `FileGet`,`FileGetObject`,`FilePut` ou `FilePutObject` difere do comprimento especificado na instrução `FileOpen` correspondente.  
  
-   A variável em uma instrução `FilePut` ou `FilePutObject` é ou inclui uma a sequência de caracteres de comprimento variável.  
  
-   The variable in a `FilePut` or `FilePutObject` is or includes a `Variant`type**.**  
  
### Para corrigir este erro  
  
1.  Verificar se a soma dos tamanhos das variáveis de comprimento fixo no tipo definido pelo usuário definindo o tipo de registro da variável é o mesmo que o valor indicado na instrução `FileOpen` da cláusula `Len`.  
  
2.  Se a variável em uma instrução `FilePut` ou `FilePutObject` é ou inclui uma a sequência de caracteres de comprimento variável, certifique\-se de que a sequência de comprimento variável é ao menos 2 caracteres menor do que o comprimento do registro especificado na cláusula `Len` da instrução `FileOpen`.  
  
3.  Se a variável em uma instrução `FilePut` ou `FilePutObject` é ou inclui uma `Variant`, certifique\-se de que a sequência de comprimento variável é ao menos 4 bytes menor do que o comprimento do registro especificado na cláusula `Len` da instrução `FileOpen`.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>