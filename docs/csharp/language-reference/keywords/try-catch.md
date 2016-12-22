---
title: "try-catch (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "try"
  - "try_CSharpKeyword"
  - "catch"
  - "catch_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave catch [C#]"
  - "instruções try-catch [C#]"
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
caps.latest.revision: 45
caps.handback.revision: 45
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# try-catch (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A instrução try\-catch consiste em uma `try` bloco seguido por uma ou mais `catch` cláusulas, que especificam os manipuladores para exceções diferentes.  
  
## Comentários  
 Quando uma exceção é lançada, o common language runtime \(CLR\) procura o `catch` instrução que manipula essa exceção. Se o método em execução no momento não há como um `catch` Bloquear, a CLR examina o método que chamou o método atual, e assim por diante até a pilha de chamada. Se nenhum `catch` bloco for encontrado, o CLR exibirá uma mensagem de exceção sem tratamento ao usuário e interrompe a execução do programa.  
  
 O `try` bloco contém o código protegido que pode causar a exceção. O bloco é executado até que uma exceção é lançada ou ele é concluído com êxito. Por exemplo, o seguinte tenta converter uma `null` objeto gera o <xref:System.NullReferenceException> exceção:  
  
```c#  
object o2 = null;  
try  
{  
    int i2 = (int)o2;   // Error  
}  
```  
  
 Embora o `catch` cláusula pode ser usada sem argumentos para capturar qualquer tipo de exceção, esse uso não é recomendado. Em geral, você só deve capturar essas exceções que você sabe como recuperar. Portanto, você sempre deve especificar um argumento de objeto derivado de <xref:System.Exception?displayProperty=fullName> por exemplo:  
  
```c#  
catch (InvalidCastException e)   
{  
}  
```  
  
 É possível usar mais de um específico `catch` cláusula na mesma instrução try\-catch. Nesse caso, a ordem do `catch` cláusulas é importante porque o `catch` cláusulas são examinadas em ordem. Capture as exceções mais específicas antes dos menos específicos. O compilador gerará um erro se você solicitar que o catch blocos para que um bloco posterior nunca pode ser alcançado.  
  
 Usando `catch` argumentos é uma maneira de filtrar as exceções que você deseja manipular.  Você também pode usar uma expressão de predicado que examina ainda mais a exceção para decidir se deve tratá\-la.  Se a expressão de predicado retornar false, a pesquisa para um manipulador continua.  
  
```c#  
catch (ArgumentException e) when (e.ParamName == “…”)  
{  
}  
```  
  
 Filtros de exceção são preferíveis capturando e relançamento porque filtros deixar a pilha de seguro de \(explicado abaixo\).  Se um manipulador posterior despejos de pilha, você pode ver onde a exceção originalmente veio, em vez de apenas o último lugar em que ele foi relançado.  Um uso comum de expressões de filtro de exceção está fazendo.  Você pode criar uma função de predicado que sempre retorna falso que também gera um log, você pode registrar exceções como se eles fossem sem a necessidade de tratá\-los e relançar.  
  
 Um [Lançar](../../../csharp/language-reference/keywords/throw.md) instrução pode ser usada em um `catch` bloco para relançar a exceção detectada pelo `catch` instrução. O exemplo a seguir extrai informações de origem de um <xref:System.IO.IOException> exceção e, em seguida, gera a exceção para o método pai.  
  
```c#  
catch (FileNotFoundException e)  
{  
    // FileNotFoundExceptions are handled here.  
}  
catch (IOException e)  
{  
    // Extract some information from this exception, and then   
    // throw it to the parent method.  
    whenDo not initialize (e.Source != null)  
        Console.WriteLine("IOException source: {0}", e.Source);  
    throw;  
}  
```  
  
 Você pode capturar uma exceção e lançar uma exceção diferente. Quando você fizer isso, especifique a exceção capturada como exceção interna, como mostrado no exemplo a seguir.  
  
```c#  
catch (InvalidCastException e)   
{  
    // Perform some action here, and then throw a new exception.  
    throw new YourCustomException("Put your error message here.", e);  
}  
```  
  
 Você pode também novamente lançar uma exceção quando uma determinada condição for verdadeira, conforme mostrado no exemplo a seguir.  
  
```c#  
  
catch (InvalidCastException e)  
{  
    if (e.Data == null)  
    {  
        throw;  
    }  
    else  
    {  
        // Take some action.  
    }  
 }  
```  
  
 De dentro de um `try` bloco, inicializar somente as variáveis são declaradas contidos nele. Caso contrário, uma exceção pode ocorrer antes da conclusão da execução do bloco. Por exemplo, no exemplo de código, a variável `n` é inicializada dentro de `try` bloco. Uma tentativa de usar essa variável fora o `try` bloco no `Write(n)` instrução irá gerar um erro do compilador.  
  
```c#  
static void Main()   
{  
    int n;  
    try   
    {  
        // Do not initialize this variable here.  
        n = 123;  
    }  
    catch  
    {  
    }  
    // Error: Use of unassigned local variable 'n'.  
    Console.Write(n);  
}  
```  
  
 Para obter mais informações sobre o problema, consulte [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
## Exceções em métodos assíncronos  
 Um método assíncrono é marcado por um  [async](../../../visual-basic/language-reference/modifiers/async.md) modificador e geralmente contém um ou mais await expressões ou instruções. Uma expressão await se aplica a [await](../../../csharp/language-reference/keywords/await.md) operador para um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.  
  
 Quando o controle atinge um `await` no método assíncrono, o progresso no método está suspenso até que a tarefa aguardada seja concluída. Quando a tarefa for concluída, a execução pode retomar o método. Para obter mais informações, consulte [Programação assíncrona com Async e Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md) e [Fluxo de controle em programas assíncronos](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Tarefa concluída para o qual `await` é aplicado pode estar em um estado de falha devido a uma exceção sem tratamento no método que retorna a tarefa. Aguardando a tarefa gera uma exceção. Uma tarefa também pode terminar em um estado cancelado se o processo assíncrono que ela retorna é cancelado. Aguardando uma tarefa cancelada lança um `OperationCanceledException`. Para obter mais informações sobre como cancelar um processo assíncrono, consulte [Ajustando seu aplicativo Async](../Topic/Fine-Tuning%20Your%20Async%20Application%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Para capturar a exceção, aguardar a tarefa em um `try` Bloquear e capturar a exceção a ele associada `catch` bloco. Para obter um exemplo, consulte a seção "Exemplo".  
  
 Uma tarefa pode ser em um estado de falha porque várias exceções ocorreram no método assíncrono aguardada. Por exemplo, a tarefa pode ser o resultado de uma chamada para <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>. Quando você espera uma tarefa, somente uma das exceções é capturada e você não pode prever qual exceção será capturada. Para obter um exemplo, consulte a seção "Exemplo".  
  
## Exemplo  
 No exemplo a seguir, o `try` bloco contém uma chamada para o `ProcessString` método que pode causar uma exceção. O `catch` cláusula contém o manipulador de exceção que apenas exibirá uma mensagem na tela. Quando o `throw` é chamada de dentro de `MyMethod`, o sistema procurará o `catch` instrução e exibe a mensagem `Exception caught`.  
  
 [!code-cs[csrefKeywordsExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_1.cs)]  
  
## Exemplo  
 No exemplo a seguir, dois blocos catch são usados e a exceção mais específica, o que vem em primeiro lugar, é capturada.  
  
 Para capturar a exceção menos específica, você pode substituir a instrução throw em `ProcessString` com a seguinte instrução: `throw new Exception()`.  
  
 Se você colocar o bloco catch menos específica primeiro no exemplo, a seguinte mensagem de erro aparece: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.  
  
 [!code-cs[csrefKeywordsExceptions#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_2.cs)]  
  
## Exemplo  
 O exemplo a seguir ilustra o tratamento de exceção para métodos assíncronos. Para capturar uma exceção que lança uma tarefa assíncrona, coloque o `await` expressão em um `try` Bloquear e capturar a exceção em um `catch` bloco.  
  
 Remova o `throw new Exception` linha no exemplo para demonstrar o tratamento de exceção. A tarefa `IsFaulted` está definida como `True`, a tarefa `Exception.InnerException` propriedade é definida para a exceção e a exceção é detectada no `catch` bloco.  
  
 Remova o `throw new OperationCancelledException` linha para demonstrar o que acontece quando você cancelan processo assíncrono. A tarefa `IsCanceled` está definida como `true`, e a exceção é detectada no `catch` bloco. Em algumas condições que não se aplicam a este exemplo, a tarefa `IsFaulted` está definida como `true` e `IsCanceled` é definido como `false`.  
  
 [!code-cs[csAsyncExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_3.cs)]  
  
## Exemplo  
 O exemplo a seguir ilustra a manipulação de exceção onde várias tarefas podem resultar em várias exceções. O `try` bloco aguarda a tarefa que é retornada por uma chamada para <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>. A tarefa é concluída quando as três tarefas ao qual é aplicado WhenAll forem concluídas.  
  
 Cada uma das três tarefas causa uma exceção. O `catch` bloco itera por meio de exceções, que são encontradas no `Exception.InnerExceptions` propriedade da tarefa que foi retornada por <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.  
  
 [!code-cs[csAsyncExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_4.cs)]  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Instruções try, throw e catch \(C\+\+\)](/visual-cpp/cpp/try-throw-and-catch-statements-cpp)   
 [Instruções para manipulação de exceções](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [Como lançar exceções explicitamente](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)