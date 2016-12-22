---
title: "Como fazer uma vari&#225;vel de objeto n&#227;o se referir a nenhuma inst&#226;ncia (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Nothing, atribuição de variável"
  - "variáveis de objeto, referência nula"
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como fazer uma vari&#225;vel de objeto n&#227;o se referir a nenhuma inst&#226;ncia (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode desassociar uma variável de objeto de qualquer instância do objeto definindo\-a [nada](../../../../visual-basic/language-reference/nothing.md).  
  
### Para desassociar uma variável de objeto de qualquer instância do objeto  
  
-   Definir a variável `Nothing` em uma instrução de atribuição.  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## Programação robusta  
 Se seu código tentar acessar um membro de uma variável de objeto que foi definido como `Nothing`, um <xref:System.NullReferenceException> ocorre.  Se você definir uma variável de objeto para `Nothing` com freqüência, ou se for possível, a variável não é inicializada, ele é uma boa idéia para delimitar os acessos de membro em um `Try...Catch...Finally` bloco.  
  
## Segurança do .NET Framework  
 Se você usar uma variável de objeto para objetos que contêm dados confidenciais, você pode definir a variável `Nothing` quando você não está ativamente lidando com um desses objetos.  Isso reduz a chance de códigos mal\-intencionados obtenham acesso aos dados.  
  
## Consulte também  
 <xref:System.NullReferenceException>   
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [nada](../../../../visual-basic/language-reference/nothing.md)   
 [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Exceções de solução de problemas: System.NullReferenceException](../Topic/Troubleshooting%20Exceptions:%20System.NullReferenceException.md)