---
title: Manipulação de exceções (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: bbe9db48ab5cc1313c18fce66312f4334b40b9c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="exception-handling-c-programming-guide"></a>Manipulação de exceções (Guia de Programação em C#)
Um bloco [try](../../../csharp/language-reference/keywords/try-catch.md) é usado por programadores de C# para particionar o código que pode ser afetado por uma exceção. Os blocos [catch](../../../csharp/language-reference/keywords/try-catch.md) associados são usados para tratar qualquer exceção resultante. Um bloco [finally](../../../csharp/language-reference/keywords/try-finally.md) contém código que será executado independentemente de uma exceção ser ou não ser lançada no bloco `try`, como a liberação de recursos que estão alocados no bloco `try`. Um bloco `try` exige um ou mais blocos `catch` associados ou um bloco `finally` ou ambos.  
  
 Os exemplos a seguir mostram uma instrução `try-catch`, uma instrução `try-finally` e um instrução `try-catch-finally`.  
  
 [!code-csharp[csProgGuideExceptions#6](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_1.cs)]  
  
 [!code-csharp[csProgGuideExceptions#7](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_2.cs)]  
  
 [!code-csharp[csProgGuideExceptions#8](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_3.cs)]  
  
 Um bloco `try` sem um bloco `catch` ou `finally` causa um erro do compilador.  
  
## <a name="catch-blocks"></a>Blocos catch  
 Um bloco `catch` pode especificar o tipo de exceção a ser capturado. A especificação de tipo é chamada de *filtro de exceção*. O tipo de exceção deve ser derivado de <xref:System.Exception>. Em geral, não especifique <xref:System.Exception> como o filtro de exceção, a menos que você saiba como tratar todas as exceções que podem ser lançadas no bloco `try` ou incluiu uma instrução [throw](../../../csharp/language-reference/keywords/throw.md) no final do seu bloco `catch`.  
  
 Vários blocos `catch` com filtros de exceção diferentes podem ser encadeados. Os blocos `catch` são avaliados de cima para baixo no seu código, mas somente um bloco `catch` será executado para cada exceção que é lançada. O primeiro bloco `catch` que especifica o tipo exato ou uma classe base da exceção lançada será executado. Se nenhum bloco `catch` especificar um filtro de exceção correspondente, um bloco `catch` que não tem um filtro será selecionado, caso haja algum na instrução. É importante posicionar os blocos `catch` com os tipos de exceção mais específicos (ou seja, os mais derivados) em primeiro.  
  
 Você deve capturar exceções quando as seguintes condições forem verdadeiras:  
  
-   Você tem uma boa compreensão de porque a exceção seria lançada e pode implementar uma recuperação específica, como solicitar que o usuário insira um novo nome de arquivo, quando você capturar um objeto <xref:System.IO.FileNotFoundException>.  
  
-   Você pode criar e lançar uma exceção nova e mais específica.  
  
     [!code-csharp[csProgGuideExceptions#9](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_4.cs)]  
  
-   Você deseja tratar parcialmente uma exceção antes de passá-la para tratamento adicional. No exemplo a seguir, um bloco `catch` é usado para adicionar uma entrada a um log de erros antes de lançar novamente a exceção.  
  
     [!code-csharp[csProgGuideExceptions#10](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_5.cs)]  
  
## <a name="finally-blocks"></a>Blocos Finally  
 Um bloco `finally` permite que você limpe as ações que são realizadas em um bloco `try`. Se estiver presente, o bloco `finally` será executado por último, depois do bloco `try` e de qualquer bloco `catch` de correspondência. Um bloco `finally` é sempre executado, independentemente de uma exceção ser lançada ou de um bloco `catch` correspondente ao tipo de exceção ser encontrado.  
  
 O bloco `finally` pode ser usado para liberar recursos, como fluxos de arquivos, conexões de banco de dados e identificadores de gráficos, sem esperar que o coletor de lixo no tempo de execução finalize os objetos. Consulte a [Instrução using](../../../csharp/language-reference/keywords/using-statement.md) para obter mais informações.  
  
 No exemplo a seguir, o bloco `finally` é usado para fechar um arquivo está aberto no bloco `try`. Observe que o estado do identificador de arquivo é selecionado antes do arquivo ser fechado. Se o bloco `try` não puder abrir o arquivo, o identificador de arquivo ainda terá o valor `null` e o bloco `finally` não tentará fechá-lo. De outra forma, se o arquivo for aberto com êxito no bloco `try`, o bloco `finally` fechará o arquivo aberto.  
  
 [!code-csharp[csProgGuideExceptions#11](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_6.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Exceções e manipulação de exceções](../../../csharp/programming-guide/exceptions/index.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)  
 [Instrução using](../../../csharp/language-reference/keywords/using-statement.md)
