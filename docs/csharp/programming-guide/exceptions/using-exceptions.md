---
title: "Usando exce&#231;&#245;es (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "exceções [C#], sobre exceções"
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Usando exce&#231;&#245;es (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Em C\#, erros no programa em tempo de execução são propagados por meio do programa, usando um mecanismo chamado de exceções.  Exceções são lançadas pelo código que encontra um erro e capturadas pelo código que pode corrigir o erro.  Exceções podem ser geradas pela.NET Framework common language runtime \(CLR\) ou pelo código em um programa.  Depois que uma exceção é lançada, ele se propaga para cima a pilha de chamadas até um `catch` se encontra a instrução para a exceção.  Exceções não capturadas são tratadas por um manipulador de exceção genérico fornecida pelo sistema que exibe uma caixa de diálogo.  
  
 Exceções são representadas por classes derivadas de <xref:System.Exception>.  Essa classe identifica o tipo de exceção e contém propriedades que possuem detalhes sobre a exceção.  Lançando uma exceção envolve a criação de uma instância de uma classe derivada da exceção, opcionalmente Configurando propriedades da exceção e, em seguida, lançando o objeto usando o `throw` palavra\-chave.  Por exemplo:  
  
 [!code-cs[csProgGuideExceptions#1](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_1.cs)]  
  
 Depois que uma exceção é lançada, o runtime verifica a instrução atual para ver se ele está dentro de um `try` bloco.  Se for, qualquer `catch` blocos associados a `try` bloco são verificados para ver se eles podem capturar a exceção.  `Catch`blocos geralmente especificam os tipos de exceção. Se o tipo da `catch` bloco é do mesmo tipo que a exceção ou uma classe base da exceção, o `catch` bloco pode lidar com o método.  Por exemplo:  
  
 [!code-cs[csProgGuideExceptions#2](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_2.cs)]  
  
 Se a instrução que lança uma exceção não está contido um `try` bloco ou se a `try` bloco que envolve a ele não tem correspondente `catch` bloco, o runtime verifica o método de chamada para um `try` instrução e `catch` blocos.  O tempo de execução continua na pilha de chamada, procurando por um compatível com o `catch` bloco.  Depois que o `catch` bloco é encontrado e executado, controle é passado para a próxima instrução após que `catch` bloco.  
  
 A `try` instrução pode conter mais de um `catch` bloco.  O primeiro `catch` instrução que pode manipular a exceção é executada; qualquer seguinte `catch` instruções, mesmo se eles são compatíveis, são ignoradas.  Portanto, catch blocos sempre devem ser ordenados do mais específico \(ou derivado de maioria\) à menos específica.  Por exemplo:  
  
 [!code-cs[csProgGuideExceptions#3](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_3.cs)]  
  
 Antes do `catch` bloco é executado, o runtime verifica se há `finally` blocos.  `Finally`blocos de habilitar o programador limpar qualquer estado ambíguo que poderia ser deixado de um anuladas `try` bloco, ou para liberar recursos externos \(como, por exemplo, as alças de elementos gráficos, conexões de banco de dados ou fluxos de arquivo\) sem precisar esperar que o coletor de lixo no runtime finalizar os objetos.  Por exemplo:  
  
 [!code-cs[csProgGuideExceptions#4](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_4.cs)]  
  
 Se `WriteByte()` emitiu uma exceção, o código na segunda `try` bloco que tenta reabrir o arquivo falhará se `file.Close()` não for chamado, e o arquivo permanecerá bloqueado.  Porque `finally` blocos são executados, mesmo se uma exceção é lançada, a `finally` bloco no exemplo anterior permite que o arquivo a ser fechado corretamente e ajuda a evitar um erro.  
  
 Se não compatível com o `catch` bloco for encontrada na pilha de chamadas após uma exceção é lançada, uma das três fatos ocorre:  
  
-   Se a pilha de chamadas contiver um construtor estático, ou um inicializador Campo estático, é acionada, com a exceção original atribuída à propriedade InnerException da Nova Exceção. um TypeInitializationException  
  
-   Se a pilha de chamadas contiver um construtor estático ou um inicializador de campo estático, um <xref:System.TypeInitializationException> é lançada, com a exceção original atribuída para o <xref:System.Exception.InnerException%2A> propriedade da nova exceção.  
  
-   Se o início do thread é alcançado, o segmento é encerrado.  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Exceções e manipulação de exceções](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)