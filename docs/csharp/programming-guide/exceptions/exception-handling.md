---
title: "Manipula&#231;&#227;o de exce&#231;&#245;es (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "tratamento de exceções [C#], sobre tratamento de exceção"
  - "exceções [C#], tratamento"
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Manipula&#231;&#227;o de exce&#231;&#245;es (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um bloco de [tentativa](../../../csharp/language-reference/keywords/try-catch.md) é usado por programadores C\# para dividir o código que pode ser afetado por uma exceção.  Blocos de [captura](../../../csharp/language-reference/keywords/try-catch.md) associados são usados para tratar todas as exceções resultantes.  Um bloco de [finalmente](../../../csharp/language-reference/keywords/try-finally.md) contém o código que é executado independentemente se uma exceção é lançada no bloco de `try` , como liberar os recursos que são atribuídos no bloco de `try` .  Um bloco de `try` requer um ou vários blocos associados de `catch` , ou um bloco de `finally` , ou ambos.  
  
 Os exemplos a seguir mostram uma instrução de `try-catch` , uma instrução de `try-finally` , e uma instrução de `try-catch-finally` .  
  
 [!code-cs[csProgGuideExceptions#6](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_1.cs)]  
  
 [!code-cs[csProgGuideExceptions#7](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_2.cs)]  
  
 [!code-cs[csProgGuideExceptions#8](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_3.cs)]  
  
 Um bloco de `try` sem um bloco de `catch` ou de `finally` causa um erro do compilador.  
  
## Blocos catch  
 Um bloco de `catch` pode especificar o tipo de exceção para capturar uma.  A especificação de tipo é chamado *um filtro de exceção*.  o tipo de exceção deve ser derivado de <xref:System.Exception>.  Em geral, não especifique <xref:System.Exception> como o filtro de exceção ou a menos que você saiba o manipule as exceções que podem ser lançadas pelo bloco de `try` , ou incluir uma declaração de [throw](../../../csharp/language-reference/keywords/throw.md) no final do bloco de `catch` .  
  
 Vários blocos de `catch` com os filtros diferentes de exceção podem ser encadeados juntos.  Blocos de `catch` são avaliados de cima para baixo em seu código, mas somente um bloco de `catch` é executado para cada exceção que é lançada.  O primeiro bloco de `catch` especificando o tipo exato ou uma classe base de exceção lançada é executado.  Se nenhum bloco de `catch` especificar um filtro correspondente de exceção, um bloco de `catch` que não tenha um filtro é selecionado, se um está presente na instrução.  É importante posicionar blocos de `catch` com \(ou seja, os tipos de exceção os mais específicos mais derivada\) primeiro.  
  
 Você deve capturar exceções quando as seguintes condições forem verdadeiras:  
  
-   Você tem uma boa conhecimento sobre como a exceção pode ser acionada, e você pode implementar uma recuperação específica, como solicitar ao usuário para inserir um novo nome de arquivo quando você capture um objeto de <xref:System.IO.FileNotFoundException> .  
  
-   Você pode criar e lançar uma exceção mais recente, específica.  
  
     [!code-cs[csProgGuideExceptions#9](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_4.cs)]  
  
-   Você deseja manipular parcialmente uma exceção antes de passá\-la para tratamento adicionais.  Em o exemplo a seguir, um bloco de `catch` é usado para adicionar uma entrada em um log de erros antes da lançar uma exceção.  
  
     [!code-cs[csProgGuideExceptions#10](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_5.cs)]  
  
## Blocos finally  
 Um bloco de `finally` permite que você para limpar as ações que são executadas em um bloco de `try` .  Se estiver presente, o bloco de `finally` executa o último, após o bloco de `try` e qualquer bloco correspondente de `catch` .  Um bloco de `finally` sempre executa, independentemente se uma exceção é lançada ou um bloco de `catch` que corresponde ao tipo de exceção será localizado.  
  
 O bloco de `finally` pode ser usado para liberar recursos como fluxos de arquivo, conexões de banco de dados, e alças de elementos gráficos sem esperar o coletor de lixo em tempo de execução para finalizar os objetos.  Consulte [Instrução using](../../../visual-basic/language-reference/statements/using-statement.md) para maiores informações.  
  
 Em o exemplo, o bloco de `finally` é usado para fechar um arquivo que é aberto no bloco de `try` .  Observe que o estado do identificador de arquivo é verificado antes que o arquivo está fechado.  Se o bloco de `try` não pode abrir o arquivo, o identificador de arquivo ainda tem o valor `null` e o bloco de `finally` não tenta feche\-o.  Como alternativa, se o arquivo está aberto com êxito no bloco de `try` , o bloco de `finally` fecha o arquivo aberto.  
  
 [!code-cs[csProgGuideExceptions#11](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_6.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Exceções e manipulação de exceções](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)   
 [Instrução using](../../../visual-basic/language-reference/statements/using-statement.md)