---
title: "Como executar c&#243;digo de limpeza usando finally (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "tratamento de exceções [C#], bloco try/finally"
  - "exceções [C#], bloco try/finally"
  - "blocos try/finally [C#]"
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como executar c&#243;digo de limpeza usando finally (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A finalidade de um `finally` instrução é para garantir que a limpeza necessária de objetos, normalmente os objetos que estão mantendo a recursos externos, ocorre imediatamente, mesmo se uma exceção é lançada.  Um exemplo de tal limpeza está chamando <xref:System.IO.Stream.Close%2A> em um <xref:System.IO.FileStream> imediatamente após o uso em vez de esperar para o objeto a ser lixo coletado pelo common language runtime, da seguinte maneira:  
  
 [!code-cs[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]  
  
## Exemplo  
 Para ativar o código anterior em um `try-catch-finally` a instrução, o código de limpeza é separada do código de trabalho, da seguinte maneira.  
  
 [!code-cs[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]  
  
 Porque uma exceção pode ocorrer a qualquer momento dentro do `try` bloquear antes do `OpenWrite()` chamar, ou o `OpenWrite()` própria chamada pode falhar, nós não são garantidas que o arquivo está aberto quando tentamos para fechá\-la.  O `finally` bloco adiciona uma verificação para certificar\-se de que o <xref:System.IO.FileStream> o objeto não é `null` antes de chamar o <xref:System.IO.Stream.Close%2A> método.  Sem o `null` verificar, o `finally` bloco poderia lançar sua própria <xref:System.NullReferenceException>, mas gerar exceções `finally` blocos devem ser evitados se possível.  
  
 Uma conexão de banco de dados é outro bom candidato sendo fechado um `finally` bloco.  Como o número de conexões permitidas para um servidor de banco de dados, às vezes, é limitado, você deve fechar conexões de banco de dados o mais rápido possível.  Se uma exceção é lançada antes de fechar a conexão, este é outro caso onde usar o `finally` bloco é melhor do que esperar para coleta de lixo.  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Exceções e manipulação de exceções](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [Manipulação de exceções](../../../csharp/programming-guide/exceptions/exception-handling.md)   
 [Instrução using](../../../visual-basic/language-reference/statements/using-statement.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)