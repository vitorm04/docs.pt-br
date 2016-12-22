---
title: "A vari&#225;vel &#39;&lt;variablename&gt;&#39; oculta uma vari&#225;vel em bloco delimitador | Microsoft Docs"
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
  - "vbc30616"
  - "bc30616"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30616"
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A vari&#225;vel &#39;&lt;variablename&gt;&#39; oculta uma vari&#225;vel em bloco delimitador
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma variável que entre em um bloco tem o mesmo nome que outra variável local.  
  
 **Identificação do erro:**  BC30616  
  
### Para corrigir este erro  
  
-   Renomear a variável no bloco de anexo para que não seja o mesmo que qualquer variável local.  Por exemplo:  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   Uma causa comum deste erro é o uso de `Catch e As Exception` dentro de um manipulador de eventos.  Se for esse o caso, o nome do `Catch` a variável de bloco `ex` em vez de `e`.  
  
-   Outra origem comum desse erro é uma tentativa de acessar uma variável local declarada dentro de um `Try` bloquear em um separado `Catch` bloco.  Para corrigir isso, declarar a variável fora do `Try...Catch...Finally` estrutura.  
  
## Consulte também  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Declaração de variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)