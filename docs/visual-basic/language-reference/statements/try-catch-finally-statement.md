---
title: "Try... Catch... Instrução Finally (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
dev_langs:
- VB
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement, Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement
- When keyword
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
caps.latest.revision: 69
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 379359e3a338746ccd440dbe1ad58c483e562dbe
ms.lasthandoff: 03/13/2017

---
# <a name="trycatchfinally-statement-visual-basic"></a>Instrução Try...Catch...Finally (Visual Basic)
Fornece uma maneira de lidar com alguns ou todos os erros possíveis que podem ocorrer em um determinado bloco de código, executando ainda o código.  
  
## <a name="syntax"></a>Sintaxe  
  
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
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`tryStatements`|Opcional. Instrução (ões) em que um erro pode ocorrer. Pode ser uma instrução composta.|  
|`Catch`|Opcional. Vários `Catch` blocos permitidos. Se ocorrer uma exceção ao processar a `Try` bloquear, cada `Catch` instrução é examinada na ordem textual para determinar se ele lida com a exceção com `exception` que representa a exceção foi lançada.|  
|`exception`|Opcional. Qualquer nome de variável. O valor inicial de `exception` é o valor do erro gerado. Usado com `Catch` especificar o erro capturado. Se omitido, o `Catch` instrução captura qualquer exceção.|  
|`type`|Opcional. Especifica o tipo de filtro de classe. Se o valor de `exception` é do tipo especificado por `type` ou de um tipo derivado, o identificador se torna associado ao objeto de exceção.|  
|`When`|Opcional. A `Catch` instrução com uma `When` cláusula captura exceções somente quando `expression` é avaliada como `True`. A `When` cláusula é aplicada somente depois de verificar o tipo de exceção, e `expression` podem se referir ao identificador que representa a exceção.|  
|`expression`|Opcional. Deve ser implicitamente conversível para `Boolean`. Qualquer expressão que descreve um filtro genérico. Normalmente usado para filtrar pelo número do erro. Usado com `When` palavra-chave para especificar as circunstâncias sob as quais o erro é capturado.|  
|`catchStatements`|Opcional. Instruções para manipular erros que ocorrem em associado `Try` bloco. Pode ser uma instrução composta.|  
|`Exit Try`|Opcional. Palavra-chave que quebras do `Try...Catch...Finally` estrutura. Execução continua com o código imediatamente após o `End Try` instrução. O `Finally` instrução ainda será executada. Não é permitido em `Finally` blocos.|  
|`Finally`|Opcional. A `Finally` bloco sempre será executado quando a execução deixa qualquer parte do `Try...Catch` instrução.|  
|`finallyStatements`|Opcional. Instruções que são executadas depois que todos os outros processamentos de erros.|  
|`End Try`|Encerra o `Try...Catch...Finally` estrutura.|  
  
## <a name="remarks"></a>Comentários  
 Se você espera que uma exceção em particular pode ocorrer durante uma determinada seção de código, coloque o código em um `Try` bloquear e usar um `Catch` bloco para manter o controle e tratar a exceção se ocorrer.  
  
 A `Try…Catch` consiste em uma `Try` bloco seguido por uma ou mais `Catch` cláusulas, que especificam os manipuladores para várias exceções. Quando uma exceção é lançada uma `Try` bloco, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] procura o `Catch` instrução que lida com a exceção. Se uma correspondência `Catch` instrução não for encontrada, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] examina o método que chamou o método atual, e assim por diante até a pilha de chamada. Se nenhum `Catch` bloco for encontrado, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] exibe uma mensagem de exceção sem tratamento para o usuário e interrompe a execução do programa.  
  
 Você pode usar mais de uma `Catch` instrução em um `Try…Catch` instrução. Se você fizer isso, a ordem do `Catch` cláusulas é significativo porque eles são examinados em ordem. Capture as exceções mais específicas antes dos menos específicos.  
  
 O seguinte `Catch` condições de instrução são menos específicas e irá capturar todas as exceções que derivam de <xref:System.Exception>classe.</xref:System.Exception> Você normalmente deve usar uma dessas variações na última `Catch` bloco no `Try...Catch...Finally` estrutura, após a captura todas as exceções específicas que você espera. Fluxo de controle nunca pode alcançar um `Catch` bloco que segue uma dessas variações.  
  
-   O `type` é `Exception`, por exemplo:`Catch ex As Exception`  
  
-   A instrução não tiver nenhuma `exception` variável, por exemplo:`Catch`  
  
 Quando um `Try…Catch…Finally` instrução está aninhada em outra `Try` bloco, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] primeiro examina cada `Catch` instrução no último campo interno `Try` bloco. Se nenhuma correspondência `Catch` declaração for encontrada, a pesquisa passa para o `Catch` instruções de externo `Try…Catch…Finally` bloco.  
  
 Variáveis locais de um `Try` bloco não estão disponíveis em um `Catch` bloquear porque eles são blocos separados. Se você quiser usar uma variável em mais de um bloco, declarar a variável de fora a `Try...Catch...Finally` estrutura.  
  
> [!TIP]
>  O `Try…Catch…Finally` instrução está disponível como um trecho de código IntelliSense. No Gerenciador de trechos de código, expanda **os padrões de código - se, para cada um, tente capturar, propriedade, etc**e então **tratamento de erros (exceções)**. Para obter mais informações, consulte [Trechos de Código](https://docs.microsoft.com/visualstudio/ide/code-snippets).  
  
## <a name="finally-block"></a>Bloco Finally  
 Se você tiver uma ou mais instruções que devem executar antes de sair do `Try` estrutura, use um `Finally` bloco. O controle passa para o `Finally` bloquear logo antes do `Try…Catch` estrutura. Isso é verdadeiro mesmo se uma exceção ocorre em qualquer lugar dentro do `Try` estrutura.  
  
 Um `Finally` bloco é útil para executar qualquer código que deve executar mesmo se houver uma exceção. O controle é passado para o `Finally` bloco, independentemente de como o `Try...Catch` bloquear sai.  
  
 O código em um `Finally` bloco é executado mesmo se seu código encontra uma `Return` instrução em uma `Try` ou `Catch` bloco. Controle não passa de um `Try` ou `Catch` bloco correspondente `Finally` bloquear nos seguintes casos:  
  
-   Um [instrução End](../../../visual-basic/language-reference/statements/end-statement.md) é encontrada no `Try` ou `Catch` bloco.  
  
-   A <xref:System.StackOverflowException>é lançada `Try` ou `Catch` bloco.</xref:System.StackOverflowException>  
  
 Não é válido para transferir explicitamente a execução em um `Finally` bloco. Transferir a execução de um `Finally` bloco não for válido, exceto por meio de uma exceção.  
  
 Se um `Try` instrução não contém pelo menos um `Catch` bloco, ele deve conter um `Finally` bloco.  
  
> [!TIP]
>  Se você não precisa capturar exceções específicas, a `Using` instrução se comporta como um `Try…Finally` bloco e garante o descarte dos recursos, independentemente de como você sai do bloco. Isso é verdadeiro mesmo com uma exceção não tratada. Para obter mais informações, consulte [usando instrução](../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="exception-argument"></a>Argumento de exceção  
 O `Catch` bloco `exception` argumento é uma instância do <xref:System.Exception>classe ou uma classe que deriva de `Exception` classe</xref:System.Exception> O `Exception` instância da classe corresponde ao erro que ocorreu no `Try` bloco.  
  
 As propriedades do `Exception` ajuda a identificar a causa e o local de uma exceção do objeto. Por exemplo, o <xref:System.Exception.StackTrace%2A>propriedade lista os métodos chamados que levam à exceção, ajudando você encontrar onde o erro ocorreu no código.</xref:System.Exception.StackTrace%2A> <xref:System.Exception.Message%2A>Retorna uma mensagem que descreve a exceção.</xref:System.Exception.Message%2A> <xref:System.Exception.HelpLink%2A>Retorna um link para um arquivo de ajuda associado.</xref:System.Exception.HelpLink%2A> <xref:System.Exception.InnerException%2A>Retorna o `Exception` retorna o objeto que causou a exceção atual, ou `Nothing` se não houver nenhum original `Exception`.</xref:System.Exception.InnerException%2A>  
  
## <a name="considerations-when-using-a-trycatch-statement"></a>Considerações ao usar um bloco Try... Instrução catch  
 Use um `Try…Catch` instrução somente para sinalizar a ocorrência de eventos de programa incomuns ou inesperados. Motivos para isso incluem o seguinte:  
  
-   Capturando exceções em tempo de execução cria uma sobrecarga adicional e provavelmente será mais lenta que a pré-verificação de para evitar exceções.  
  
-   Se um `Catch` bloco não seja tratado corretamente, a exceção não pode ser relatada corretamente para os usuários.  
  
-   Tratamento de exceção faz com que um programa mais complexas.  
  
 Não é necessário sempre um `Try…Catch` instrução para verificar uma condição que é provável de ocorrer. O exemplo a seguir verifica se um arquivo existe antes de tentar abri-lo. Isso reduz a necessidade para capturar uma exceção lançada pelo <xref:System.IO.File.OpenText%2A>método.</xref:System.IO.File.OpenText%2A>  
  
 [!code-vb[VbVbalrStatements&#94;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_1.vb)]  
  
 Garantir que o código em `Catch` blocos podem relatar corretamente exceções aos usuários, seja por meio de log de thread-safe ou mensagens apropriadas. Caso contrário, exceções podem permanecer desconhecidas.  
  
## <a name="async-methods"></a>Métodos assíncronos  
 Se você marcar um método com o [Async](../../../visual-basic/language-reference/modifiers/async.md) modificador, você pode usar o [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador no método. Uma instrução com o `Await` operador suspende a execução do método até que a tarefa aguardada seja concluída. A tarefa representa um trabalho em andamento. Quando a tarefa que está associada com o `Await` operador termina, retoma a execução no mesmo método. Para obter mais informações, consulte [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
 Uma tarefa retornada por um método assíncrono pode terminar em um estado de falha, indicando que ela foi concluída devido a uma exceção sem tratamento. Uma tarefa também pode terminar em um estado cancelado, o que resulta em um `OperationCanceledException` sendo lançadas fora a expressão await. Para capturar qualquer tipo de exceção, coloque o `Await` expressão associado com a tarefa em uma `Try` bloquear e capturar a exceção no `Catch` bloco. Um exemplo é fornecido neste tópico.  
  
 Uma tarefa pode ser em um estado de falha porque várias exceções foram responsáveis por sua falha. Por exemplo, a tarefa pode ser o resultado de uma chamada para <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> Quando você espera uma tarefa, a exceção capturada é apenas uma das exceções, e você não pode prever qual exceção será capturada. Um exemplo é fornecido neste tópico.  
  
 Um `Await` expressão não pode estar dentro de uma `Catch` bloco ou `Finally` bloco.  
  
## <a name="iterators"></a>Iteradores  
 Uma função de iterador ou `Get` acessador realiza uma iteração personalizada em uma coleção. Um iterador usa um [gerar](../../../visual-basic/language-reference/statements/yield-statement.md) instrução para retornar cada elemento da coleção um por vez. Chamar uma função de iterador usando um [para cada uma... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 A `Yield` instrução pode ser dentro de uma `Try` bloco. A `Try` bloco que contém um `Yield` instrução pode ter `Catch` blocos e pode ter um `Finally` bloco. Consulte a seção "Tente blocos no Visual Basic" [iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7) para obter um exemplo.  
  
 A `Yield` instrução não pode estar dentro de uma `Catch` bloco ou uma `Finally` bloco.  
  
 Se o `For Each` corpo (fora da função de iterador) gera uma exceção, uma `Catch` bloco na função iterador não é executado, mas um `Finally` bloco na função iterador é executado. Um `Catch` bloco dentro de uma função de iterador captura somente exceções que ocorrem dentro da função de iterador.  
  
## <a name="partial-trust-situations"></a>Situações de confiança parcial  
 Em situações de confiança parcial, como um aplicativo hospedado em um compartilhamento de rede, `Try...Catch...Finally` não capturar exceções de segurança que ocorrem antes que o método que contém a chamada é invocado. O exemplo a seguir, quando você coloca em um compartilhamento de servidor e executar a partir daí, gera o erro "System.Security.SecurityException: falha de solicitação." Para obter mais informações sobre exceções de segurança, consulte a <xref:System.Security.SecurityException>classe.</xref:System.Security.SecurityException>  
  
 [!code-vb[VbVbalrStatements&#85;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_2.vb)]  
  
 Em tal situação confiança parcial, você precisa colocar o `Process.Start` instrução em um separado `Sub`. A chamada inicial para o `Sub` falhará. Isso permite que `Try...Catch` para capturá-la antes do `Sub` que contém `Process.Start` é iniciado e produziu a exceção de segurança.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra a estrutura do `Try...Catch...Finally` instrução.  
  
 [!code-vb[VbVbalrStatements&#86;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_3.vb)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o `CreateException` método lança um `NullReferenceException`. O código que gera a exceção não está em um `Try` bloco. Portanto, o `CreateException` método não trata a exceção. O `RunSample` método tratar a exceção porque a chamada para o `CreateException` método está em um `Try` bloco.  
  
 O exemplo inclui `Catch` instruções para vários tipos de exceções, ordenados da mais específica para a mais geral.  
  
 [!code-vb[VbVbalrStatements&#91;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_4.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar um `Catch When` instrução para filtrar em uma expressão condicional. Se a expressão condicional for avaliada como `True`, o código de `Catch` bloco é executado.  
  
 [!code-vb[VbVbalrStatements&#92;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_5.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir tem uma `Try…Catch` instrução que está contida em um `Try` bloco. Interno `Catch` bloco lançar uma exceção que tem seu `InnerException` propriedade definida para a exceção original. Externo `Catch` bloco relata sua própria exceção e a exceção interna.  
  
 [!code-vb[VbVbalrStatements&#93;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_6.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o tratamento de exceção para métodos assíncronos. Para capturar uma exceção se aplica a uma tarefa assíncrona, o `Await` expressão está em uma `Try` bloco do chamador e a exceção é detectado no `Catch` bloco.  
  
 Remova o `Throw New Exception` linha no exemplo para demonstrar o tratamento de exceção. A exceção é detectada no `Catch` bloquear a tarefa `IsFaulted` está definida como `True`e a tarefa `Exception.InnerException` propriedade é definida para a exceção.  
  
 Remova o `Throw New OperationCancelledException` linha para demonstrar o que acontece quando você cancela um processo assíncrono. A exceção é detectada no `Catch` bloco e a tarefa `IsCanceled` está definida como `True`. No entanto, em algumas condições que não se aplicam a este exemplo `IsFaulted` é definido como `True` e `IsCanceled` é definido como `False`.  
  
 [!code-vb[csAsyncExceptions n º&1;](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_7.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra a manipulação de exceção onde várias tarefas podem resultar em várias exceções. O `Try` bloco tem o `Await` expressão para a tarefa que <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>retornado.</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> A tarefa é concluída quando as três tarefas ao qual <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>é aplicado forem concluídas.</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>  
  
 Cada uma das três tarefas causa uma exceção. O `Catch` bloco itera por meio de exceções, que são encontradas no `Exception.InnerExceptions` propriedade da tarefa que `Task.WhenAll` retornado.  
  
 [!code-vb[csAsyncExceptions n º&3;](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_8.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Information.Err%2A></xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:System.Exception></xref:System.Exception>   
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)   
 [Melhores práticas para usar trechos de código](https://docs.microsoft.com/visualstudio/ide/best-practices-for-using-code-snippets)   
 [Tratamento de exceção](https://msdn.microsoft.com/library/dd997415)   
 [Instrução Throw](../../../visual-basic/language-reference/statements/throw-statement.md)
