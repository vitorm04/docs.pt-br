---
title: "Instru&#231;&#227;o Try...Catch...Finally (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Try...Catch...Finally"
  - "vb.when"
  - "vb.Finally"
  - "vb.Catch"
  - "vb.Try"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "instrução Catch"
  - "tratamento de erros, durante a execução do código"
  - "palavra-chave Finally [Visual Basic], Try...Catch...Finally"
  - "tratamento estruturado de exceções, instruções Try...Catch...Finally"
  - "instrução Try"
  - "instrução Try, Try...Catch...Finally"
  - "instruções Try...Catch...Finally"
  - "tratamento de exceções de try-catch, instruções Try...Catch...Finally"
  - "código do Visual Basic, tratando erros durante a execução"
  - "palavra-chave When"
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
caps.latest.revision: 69
caps.handback.revision: 69
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Try...Catch...Finally (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Fornece uma maneira para manipular alguns ou todos os possíveis erros que podem ocorrer em um determinado bloco de código, quando código imóvel de execução.  
  
## Sintaxe  
  
```  
Try  
    [ tryStatements ]  
    [ Exit Try ]  
[ Catch [ exception [ As type ] ] [ When expression ]  
    [ catchStatements ]  
    [ Exit Try ] ]  
[ Catch ... ]  
[ Finally  
    [ finallyStatements ] ]  
End Try  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`tryStatements`|Opcional.  Instruções onde um erro pode ocorrer.  Pode ser uma instrução composta.|  
|`Catch`|Opcional.  Vários blocos de `Catch` permitidos.  Se uma exceção ocorrer ao processar o bloco de `Try` , cada declaração de `Catch` é examinada na ordem textual determinar se lida com a exceção, com `exception` que representa a exceção que foi lançada.|  
|`exception`|Opcional.  Qualquer nome de variável.  O valor inicial de `exception` é o valor de erro gerado.  Usado com `Catch` para especificar o erro capturado.  Se omitido, a instrução de `Catch` captura qualquer exceção.|  
|`type`|Opcional.  Especifica o tipo de filtro da classe.  Se o valor de `exception` é do tipo especificado por `type` ou um tipo derivado, o identificador transformações limite para o objeto de exceção.|  
|`When`|Opcional.  Uma declaração de `Catch` com uma cláusula de `When` captura exceções somente quando `expression` avalia a `True`.  Uma cláusula de `When` é aplicada somente após verifique o tipo de exceção, e `expression` pode se referir ao identificador que representa a exceção.|  
|`expression`|Opcional.  Deve ser conversível implicitamente na `Boolean`.  Qualquer expressão que descrever um filtro genérico.  Normalmente usado para filtrar por engano o número.  Usado com a palavra\-chave de `When` para especificar as condições sob as quais o erro é capturado.|  
|`catchStatements`|Opcional.  Instruções para manipular erros que ocorrem no bloco associado de `Try` .  Pode ser uma instrução composta.|  
|`Exit Try`|Opcional.  Palavras\-chave que estoira estrutura de `Try...Catch...Finally` .  A execução continua com o código imediatamente após a declaração de `End Try` .  A declaração de `Finally` ainda será executada.  Não permitido em blocos de `Finally` .|  
|`Finally`|Opcional.  Um bloco de `Finally` é executado sempre quando a execução permite que qualquer parte da declaração de `Try...Catch` .|  
|`finallyStatements`|Opcional.  A instrução que é executado após o outro processamento de erro ocorreu.|  
|`End Try`|Finaliza a estrutura de `Try...Catch...Finally` .|  
  
## Comentários  
 Se você pretende que uma exceção específica pode ocorrer durante uma determinada seção de código, coloque o código em um bloco de `Try` e usam um bloco de `Catch` para manter controle e tratar a exceção ocorre se.  
  
 Uma declaração de `Try…Catch` consiste em um bloco de `Try` seguido por um ou mais cláusulas de `Catch` , que especificam manipuladores para várias exceções.  Quando uma exceção é lançada em um bloco de `Try` , [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] procura pela instrução de `Catch` que lida com a exceção.  Se uma instrução de `Catch` de correspondência não for encontrada, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] examina o método que chamou o método atual, e assim por diante até que a pilha de chamadas.  Se nenhum bloco de `Catch` for encontrado, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] exibe uma mensagem de exceção sem tratamento para o usuário e para a execução do programa.  
  
 Você pode usar mais de uma declaração de `Catch` em uma instrução de `Try…Catch` .  Se você fizer isso, a ordem das cláusulas de `Catch` é útil porque eles são examinados em ordem.  Capturar exceções mais específicas antes de menos específicas.  
  
 As seguintes condições de instrução de `Catch` é ao menos específicas, e capturarão todas as exceções que derivam da classe de <xref:System.Exception> .  Você normalmente deve usar uma de essas variações como o último bloco de `Catch` na estrutura de `Try...Catch...Finally` , após capturado todas as exceções específicas que você espera.  O fluxo de controle nunca pode alcançar um bloco de `Catch` que segue qualquer uma de essas variações.  
  
-   `type` é `Exception`, por exemplo: `Catch ex As Exception`  
  
-   A declaração não tem nenhum variável de `exception` , por exemplo: `Catch`  
  
 Quando uma declaração de `Try…Catch…Finally` está aninhado em outro bloco de `Try` , [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] primeiro examina cada instrução de `Catch` no bloco interno de `Try` .  Se nenhuma instrução de `Catch` de correspondência for encontrada, a pesquisa continua às instruções de `Catch` do bloco externo de `Try…Catch…Finally` .  
  
 Variáveis locais de um bloco de `Try` não estão disponíveis em um bloco de `Catch` blocos porque eles são separados.  Se você desejar usar uma variável em mais de um bloco, declare a variável fora da estrutura de `Try...Catch...Finally` .  
  
> [!TIP]
>  A declaração de `Try…Catch…Finally` está disponível como um trecho de código IntelliSense.  Em o gerenciador de trechos de código, expanda **Padrões de código \- se para, cada um, a captura try, a propriedade, etc.**, e então **Tratamento de erros \(exceções\)**.  Para mais informações, consulte [Trechos de código](/visual-studio/ide/code-snippets).  
  
## Bloco finally  
 Se você tiver uma ou mais instruções que devem executar antes de sair da estrutura `Try` use um bloco `Finally`.  O controle passa para o bloco `Finally` logo antes de sair da estrutura `Try…Catch`.  Isso é verdadeiro mesmo se uma exceção ocorre em qualquer lugar dentro da estrutura `Try`.  
  
 Um bloco de `Finally` é útil para executar qualquer código que é executando mesmo se houver uma exceção.  O controle é passado para o bloco de `Finally` independentemente de como `Try...Catch` sai do bloco.  
  
 O código em um bloco de `Finally` executa mesmo se o seu código encontra uma instrução de `Return` em um bloco de `Try` ou de `Catch` .  O controle não passa de um bloco `Try` ou `Catch` para o bloco `Finally` correpondente nos seguintes casos:  
  
-   [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md) está localizado no bloco de `Try` ou de `Catch` .  
  
-   <xref:System.StackOverflowException> é lançada no bloco de `Try` ou de `Catch` .  
  
 é inválido transferir explicitamente a execução em um bloco de `Finally` .  Transferir a execução fora de um bloco de `Finally` é inválido, exceto com uma exceção.  
  
 Se uma instrução de `Try` não contém pelo menos um bloco de `Catch` , deve conter um bloco de `Finally` .  
  
> [!TIP]
>  Se você não precisa capturar exceções específicas, a instrução de `Using` se comporta como um bloco de `Try…Finally` , e garante a liberação de recursos, independentemente de como você sai do bloco.  Isso é verdadeiro mesmo com uma exceção não tratada.  Para mais informações, consulte [Instrução Using](../../../visual-basic/language-reference/statements/using-statement.md).  
  
## Argumento de exceção  
 O argumento de `exception` do bloco de `Catch` é uma instância da classe de <xref:System.Exception> ou de uma classe que deriva da classe de `Exception` .  A instância de classe de `Exception` corresponde ao erro que ocorreu no bloco de `Try` .  
  
 As propriedades do objeto de `Exception` ajudam a identificar a causa e o local de uma exceção.  Por exemplo, a propriedade lista de <xref:System.Exception.StackTrace%2A> os métodos que chamados que conduziu à exceção, ajudando você encontrar onde ocorreu o erro no código.  <xref:System.Exception.Message%2A> retorna uma mensagem que descreve a exceção.  <xref:System.Exception.HelpLink%2A> retorna um link para um arquivo de ajuda associado.  <xref:System.Exception.InnerException%2A> retorna o objeto de `Exception` que causou a exceção atual, ou retorna `Nothing` se não houver nenhum `Exception`original.  
  
## Considerações ao usar uma captura a instrução try…  
 Use uma instrução de `Try…Catch` para sinalizar somente a ocorrência de eventos ou incomuns não\-antecipados do programa.  As razões para essa incluem o seguinte:  
  
-   Capturar exceções em tempo de execução cria a sobrecarga adicional, e é provável de ser mais lento do que significa verificando para evitar exceções.  
  
-   Se um bloco de `Catch` não é tratado corretamente, a exceção não pode ser relatadas corretamente aos usuários.  
  
-   Manipulação de exceção torna um programa mais complexo.  
  
 Você não precisa sempre uma instrução de `Try…Catch` de verificar se houver uma condição que é provável de ocorrer.  O exemplo a seguir verifica se um arquivo existe antes de tentar abrir a.  Isso reduz a necessidade para capturar uma exceção acionada pelo método de <xref:System.IO.File.OpenText%2A> .  
  
 [!code-vb[VbVbalrStatements#94](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/try-catch-finally-statement_1.vb)]  
  
 Certifique\-se de que o código nos blocos de `Catch` pode relatar exceções corretamente para usuários, se através de log thread\-safe ou apropriado para mensagens.  Caso contrário, as exceções desconhecidas podem continuar.  
  
## Métodos de Async  
 Se você marcar um método com o modificador de [Async](../../../visual-basic/language-reference/modifiers/async.md) , você pode usar o operador de [espere](../../../visual-basic/language-reference/operators/await-operator.md) no método.  Uma instrução com o operador de `Await` suspende a execução do método até que a tarefa deve terminar.  A tarefa representa trabalho contínuo.  Quando a tarefa que está associada com o operador de `Await` concluir, a execução continua no mesmo método.  Para mais informações, consulte [Fluxo de controle em programas assíncronos](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Uma tarefa retornada por um método de Async pode finalizar em um estado criticado, indicando que tiver terminado por causa de uma exceção sem tratamento.  Uma tarefa também pode finalizar em um estado cancelado, que resulta em `OperationCanceledException` que está sendo gerada fora da expressão de espera.  Para capturar um ou outro tipo de exceção, coloque a expressão de `Await` que está associada com a tarefa em um bloco de `Try` , e capturar a exceção no bloco de `Catch` .  Um exemplo é apresentado posteriormente em este tópico.  
  
 Uma tarefa pode estar em um estado criticado porque as várias exceções eram responsáveis por sua crítica.  Por exemplo, a tarefa pode ser o resultado de uma chamada a <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.  Quando você espera uma tarefa, a exceção capturada é apenas uma das exceções, e você não pode prever que será exceção capturada.  Um exemplo é apresentado posteriormente em este tópico.  
  
 Uma expressão de `Await` não pode ser dentro de um bloco de `Catch` ou bloco de `Finally` .  
  
## Iteradores  
 Uma função de iterador ou um acessador de `Get` executam uma iteração personalizado em uma coleção.  Um iterador usa uma instrução de [Produzir](../../../visual-basic/language-reference/statements/yield-statement.md) para retornar um de cada vez a cada elemento da coleção.  Você chama uma função de iterador usando [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 Uma declaração de `Yield` pode estar dentro de um bloco de `Try` .  Um bloco de `Try` que contém uma declaração de `Yield` pode ter blocos de `Catch` , e pode ter um bloco de `Finally` .  Consulte “blocos try a seção no Visual Basic” de [Iteradores](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md) para um exemplo.  
  
 Uma declaração de `Yield` não pode ser dentro de um bloco de `Catch` ou um bloco de `Finally` .  
  
 Se o corpo de `For Each` \(fora da função de iterador\) gera uma exceção, um bloco de `Catch` na função de iterador não é executado, mas um bloco de `Finally` na função de iterador é executado.  Um bloco de `Catch` dentro de uma função de iterador somente captura exceções que ocorrem dentro da função de iterador.  
  
## Situações de Confiança parcial  
 Em situações de confiança parcial, como um aplicativo hospedado em um compartilhamento de rede, `Try...Catch...Finally` não captura exceções de segurança que ocorre antes que o método que contém a chamada seja chamado.  O seguinte exemplo, quando você colocar o em um compartilhamento de servidor e executá\-lo de aí, gera erro “System.Security.SecurityException: Solicitação falha.” Para obter mais informações sobre as exceções de segurança, consulte a classe de <xref:System.Security.SecurityException> .  
  
 [!code-vb[VbVbalrStatements#85](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/try-catch-finally-statement_2.vb)]  
  
 Em uma situação de confiança parcial, você precisa colocar a instrução de `Process.Start` em `Sub`separado.  A chamada inicial a `Sub` falhará.  Isso permite que `Try...Catch` para capturar\-lo antes que `Sub` que contém `Process.Start` é iniciado e a exceção de segurança gerada.  
  
## Exemplo  
 O exemplo a seguir ilustra a estrutura de instrução de `Try...Catch...Finally` .  
  
 [!code-vb[VbVbalrStatements#86](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/try-catch-finally-statement_3.vb)]  
  
## Exemplo  
 Em o exemplo, o método de `CreateException` gera `NullReferenceException`.  O código que gera a exceção não estiver em um bloco de `Try` .  Portanto, o método de `CreateException` não lida com a exceção.  O método de `RunSample` lida com a exceção como a chamada para o método de `CreateException` está em um bloco de `Try` .  
  
 O exemplo inclui instruções de `Catch` para vários tipos de exceções, ordenados da mais específica para mais geral.  
  
 [!code-vb[VbVbalrStatements#91](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/try-catch-finally-statement_4.vb)]  
  
## Exemplo  
 O exemplo a seguir mostra como usar uma instrução de `Catch When` para filtrar utilizando uma expressão condicional.  Se a expressão condicional for avaliada como `True`, o código no bloco de `Catch` executa.  
  
 [!code-vb[VbVbalrStatements#92](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/try-catch-finally-statement_5.vb)]  
  
## Exemplo  
 O exemplo tem uma instrução de `Try…Catch` que está contida em um bloco de `Try` .  O bloco interno de `Catch` gera uma exceção que tem sua propriedade definida `InnerException` da exceção original.  O bloco externo de `Catch` relata sua própria exceção e a exceção interna.  
  
 [!code-vb[VbVbalrStatements#93](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/try-catch-finally-statement_6.vb)]  
  
## Exemplo  
 O exemplo a seguir ilustra a manipulação de exceção para métodos de async.  Para capturar uma exceção que se aplica a uma tarefa de async, a expressão de `Await` está em um bloco de `Try` do chamador, e a exceção é detectada no bloco de `Catch` .  
  
 Tire comentários da linha de `Throw New Exception` no exemplo para demonstrar manipulação de exceção.  A exceção é detectada no bloco de `Catch` , a propriedade de `IsFaulted` de tarefa é definida como `True`, e a propriedade de `Exception.InnerException` de tarefa é definida para a exceção.  
  
 Tire comentários da linha de `Throw New OperationCancelledException` para demonstrar o que acontece quando você cancelar um processo assíncrono.  A exceção é detectada no bloco de `Catch` , e a propriedade de `IsCanceled` de tarefa é definida como `True`.  Em o entanto, em algumas circunstâncias que não se aplicam a esse exemplo, `IsFaulted` é definido como `True` e `IsCanceled` é definido como `False`.  
  
 [!code-vb[csAsyncExceptions#1](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_7.vb)]  
  
## Exemplo  
 O exemplo a seguir ilustra a manipulação de exceção onde várias tarefas podem resultar em várias exceções.  O bloco de `Try` tem a expressão de `Await` para a tarefa que o <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> retornado.  A tarefa é concluída quando as três tarefas que é aplicado a <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> está concluída.  
  
 Cada uma das três tarefas causa de uma exceção.  O bloco de `Catch` itera com exceções, que são encontrados na propriedade de `Exception.InnerExceptions` de tarefa que o `Task.WhenAll` retornado.  
  
 [!code-vb[csAsyncExceptions#3](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_8.vb)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:System.Exception>   
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)   
 [Práticas recomendadas para usar trechos de código](/visual-studio/ide/best-practices-for-using-code-snippets)   
 [Tratamento de Exceção](../Topic/Exception%20Handling%20\(Task%20Parallel%20Library\).md)   
 [Instrução Throw](../../../visual-basic/language-reference/statements/throw-statement.md)