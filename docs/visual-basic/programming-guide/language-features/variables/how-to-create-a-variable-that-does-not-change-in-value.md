---
title: "Como criar uma vari&#225;vel que n&#227;o se altera no valor (Visual Basic) | Microsoft Docs"
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
  - "variáveis [Visual Basic], valor constante"
  - "variáveis [Visual Basic], somente leitura"
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar uma vari&#225;vel que n&#227;o se altera no valor (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

A noção de uma variável que não altera seu valor pode parecer ser contraditória.  Mas há situações quando uma constante não é viável e é útil ter uma variável com um valor fixo.  Neste caso você pode definir um variável de membro com a palavra\-chave [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Você não pode usar o [Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md) para declarar e atribua um valor constante nas seguintes circunstâncias:  
  
-   A declaração `Const` não aceita o tipo de dados que deseja usar  
  
-   Você não sabe o valor no tempo de compilação  
  
-   Você não está apto calcular o valor da constante em tempo de compilação  
  
### Como: criar uma variável que não se altera em valor  
  
1.  A nível de módulo, declare um variável de membro com o [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) e inclua a palavra\-chave [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md).  
  
    ```  
  
    Dim ReadOnly timeStarted  
    ```  
  
     Você pode especificar `ReadOnly` apenas em um variável de membro.  Isso significa que você deve definir a variável no nível de módulo, fora de qualquer procedimento.  
  
2.  Se você pode calcular o valor em uma única instrução em tempo de compilação, use uma cláusula de inicialização na declaração `Dim`.  Execute a cláusula [As](../../../../visual-basic/language-reference/statements/as-clause.md) com um sinal de igualdade \(`=`\), seguida de uma expressão.  Certifique\-se de que o compilador pode avaliar esta expressão para um valor constante.  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     Você pode atribuir um valor a uma variável `ReadOnly` apenas uma vez.  Uma vez feito isso, nenhum código pode alterar seu valor.  
  
     Se você não sabe o valor em tempo de compilação, ou não podel calculá\-lo em tempo de compilação em uma única declaração, você ainda pode atribuí\-lo em tempo de execução em um construtor.  Para fazer isso, você deve declarar a variável `ReadOnly` em nível de classe ou estrutura.  No Construtor para essa classe ou estrutura, calcular a variável do valor fixo e atribua a ela para a variável antes de retornar do construtor.  
  
## Consulte também  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)