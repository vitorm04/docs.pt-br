---
title: Tentar... Capturar... Instrução Finally
description: Aprenda a usar a manipulação de exceção com instruções Visual Basic try/catch/finally.
ms.date: 12/07/2018
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement [Visual Basic]
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement [Visual Basic], Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement [Visual Basic]
- When keyword [Visual Basic]
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
ms.custom: seodec18
ms.openlocfilehash: eb04b6cff0847009407e38a3696e9be7c700356c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337326"
---
# <a name="trycatchfinally-statement-visual-basic"></a>Instrução Try...Catch...Finally (Visual Basic)

Fornece uma maneira de lidar com alguns ou todos os erros possíveis que podem ocorrer em um determinado bloco de código, enquanto ainda executa o código.

## <a name="syntax"></a>Sintaxe

```vb
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
|`Catch`|Opcional. Blocos múltiplos de `Catch` permitidos. Se ocorrer uma exceção durante o processamento do bloco de `Try`, cada instrução `Catch` será examinada em ordem textual para determinar se ele trata a exceção, com `exception` que representa a exceção que foi lançada.|
|`exception`|Opcional. Qualquer nome de variável. O valor inicial de `exception` é o valor do erro gerado. Usado com `Catch` para especificar o erro detectado. Se for omitido, a instrução `Catch` capturará qualquer exceção.|
|`type`|Opcional. Especifica o tipo de filtro de classe. Se o valor de `exception` for do tipo especificado por `type` ou de um tipo derivado, o identificador se tornará associado ao objeto de exceção.|
|`When`|Opcional. Uma instrução `Catch` com uma cláusula `When` captura exceções somente quando `expression` é avaliada como `True`. Uma cláusula `When` é aplicada somente após a verificação do tipo da exceção e `expression` pode se referir ao identificador que representa a exceção.|
|`expression`|Opcional. Deve ser implicitamente conversível em `Boolean`. Qualquer expressão que descreva um filtro genérico. Normalmente usado para filtrar por número de erro. Usado com a palavra-chave `When` para especificar circunstâncias sob as quais o erro é capturado.|
|`catchStatements`|Opcional. Instruções para tratar erros que ocorrem no bloco de `Try` associado. Pode ser uma instrução composta.|
|`Exit Try`|Opcional. Palavra-chave que se divide da estrutura de `Try...Catch...Finally`. A execução é retomada com o código imediatamente após a instrução `End Try`. A instrução `Finally` ainda será executada. Não permitido em blocos de `Finally`.|
|`Finally`|Opcional. Um bloco de `Finally` é sempre executado quando a execução sai de qualquer parte da instrução `Try...Catch`.|
|`finallyStatements`|Opcional. As instruções que são executadas após o processamento de todo o outro erro ocorreram.|
|`End Try`|Encerra a estrutura de `Try...Catch...Finally`.|

## <a name="remarks"></a>Comentários

Se você espera que uma determinada exceção ocorra durante uma determinada seção de código, coloque o código em um bloco de `Try` e use um bloco de `Catch` para manter o controle e manipular a exceção, se ocorrer.

Uma instrução `Try…Catch` consiste em um bloco de `Try` seguido por uma ou mais cláusulas `Catch`, que especificam manipuladores para várias exceções. Quando uma exceção é gerada em um bloco de `Try`, Visual Basic procura a instrução `Catch` que manipula a exceção. Se uma instrução `Catch` correspondente não for encontrada, Visual Basic examinará o método que chamou o método atual e assim por diante na pilha de chamadas. Se nenhum bloco de `Catch` for encontrado, Visual Basic exibirá uma mensagem de exceção sem tratamento para o usuário e interromperá a execução do programa.

Você pode usar mais de uma instrução `Catch` em uma instrução `Try…Catch`. Se você fizer isso, a ordem das cláusulas de `Catch` será significativa, pois elas são examinadas em ordem. Capture as exceções mais específicas antes das menos específicas.

As seguintes condições de instrução de `Catch` são as menos específicas e capturarão todas as exceções que derivam da classe <xref:System.Exception>. Você normalmente deve usar uma dessas variações como o último bloco de `Catch` na estrutura de `Try...Catch...Finally`, depois de capturar todas as exceções específicas que você espera. O fluxo de controle nunca pode alcançar um bloco de `Catch` que segue qualquer uma dessas variações.

- O `type` é `Exception`, por exemplo: `Catch ex As Exception`

- A instrução não tem `exception` variável, por exemplo: `Catch`

Quando uma instrução `Try…Catch…Finally` é aninhada em outro bloco de `Try`, Visual Basic primeiro examina cada instrução `Catch` no bloco de `Try` mais interno. Se nenhuma instrução de `Catch` correspondente for encontrada, a pesquisa prosseguirá para as instruções de `Catch` do bloco de `Try…Catch…Finally` externo.

Variáveis locais de um bloco de `Try` não estão disponíveis em um bloco de `Catch` porque são blocos separados. Se você quiser usar uma variável em mais de um bloco, declare a variável fora da estrutura de `Try...Catch...Finally`.

> [!TIP]
> A instrução `Try…Catch…Finally` está disponível como um trecho de código IntelliSense. No Gerenciador de trechos de código, expanda **padrões de código-se, para cada um, Tente catch, propriedade, etc**. e, em seguida, **tratamento de erro (exceções)** . Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).

## <a name="finally-block"></a>Bloco finally

Se você tiver uma ou mais instruções que devem ser executadas antes de sair da estrutura de `Try`, use um bloco de `Finally`. O controle passa para o bloco de `Finally` antes de passar da estrutura de `Try…Catch`. Isso é verdadeiro mesmo se ocorrer uma exceção em qualquer lugar dentro da estrutura de `Try`.

Um bloco de `Finally` é útil para executar qualquer código que deve ser executado mesmo se houver uma exceção. O controle é passado para o bloco de `Finally`, independentemente de como o bloco de `Try...Catch` é encerrado.

O código em um bloco de `Finally` é executado mesmo que seu código encontre uma instrução `Return` em um bloco `Try` ou `Catch`. O controle não passa de um bloco de `Try` ou de `Catch` para o bloco de `Finally` correspondente nos seguintes casos:

- Uma [instrução End](end-statement.md) é encontrada no bloco `Try` ou `Catch`.

- Uma <xref:System.StackOverflowException> é lançada no bloco `Try` ou `Catch`.

Não é válido transferir explicitamente a execução para um bloco de `Finally`. A transferência da execução para fora de um bloco de `Finally` não é válida, exceto por uma exceção.

Se uma instrução `Try` não contiver pelo menos um bloco de `Catch`, ela deverá conter um bloco de `Finally`.

> [!TIP]
> Se você não precisa capturar exceções específicas, a instrução `Using` se comporta como um bloco de `Try…Finally` e garante a alienação dos recursos, independentemente de como você sai do bloco. Isso é verdadeiro mesmo com uma exceção sem tratamento. Para obter mais informações, consulte [Instrução using](using-statement.md).

## <a name="exception-argument"></a>Argumento de exceção

O argumento `Catch` Block `exception` é uma instância da classe <xref:System.Exception> ou uma classe derivada da classe `Exception`. A instância de classe de `Exception` corresponde ao erro que ocorreu no bloco de `Try`.

As propriedades do objeto `Exception` ajudam a identificar a causa e o local de uma exceção. Por exemplo, a propriedade <xref:System.Exception.StackTrace%2A> lista os métodos chamados que levaram à exceção, ajudando você a descobrir onde o erro ocorreu no código. <xref:System.Exception.Message%2A> retorna uma mensagem que descreve a exceção. <xref:System.Exception.HelpLink%2A> retorna um link para um arquivo de ajuda associado. <xref:System.Exception.InnerException%2A> retorna o objeto `Exception` que causou a exceção atual ou retorna `Nothing` se não houver nenhum `Exception`original.

## <a name="considerations-when-using-a-trycatch-statement"></a>Considerações ao usar uma tentativa... Instrução Catch

Use uma instrução `Try…Catch` apenas para sinalizar a ocorrência de eventos de programa incomuns ou inesperados. Os motivos para isso incluem o seguinte:

- A captura de exceções em tempo de execução cria sobrecarga adicional e provavelmente será mais lenta do que a verificação prévia para evitar exceções.

- Se um bloco de `Catch` não for manipulado corretamente, a exceção poderá não ser relatada corretamente aos usuários.

- A manipulação de exceções torna um programa mais complexo.

Você nem sempre precisa de uma instrução `Try…Catch` para verificar se há uma condição que provavelmente ocorrerá. O exemplo a seguir verifica se um arquivo existe antes de tentar abri-lo. Isso reduz a necessidade de capturar uma exceção gerada pelo método <xref:System.IO.File.OpenText%2A>.

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

Verifique se o código nos blocos de `Catch` pode relatar exceções adequadamente aos usuários, seja por meio de log seguro de thread ou mensagens apropriadas. Caso contrário, as exceções podem permanecer desconhecidas.

## <a name="async-methods"></a>Métodos assíncronos

Se você marcar um método com o modificador [Async](../modifiers/async.md) , poderá usar o operador [Await](../operators/await-operator.md) no método. Uma instrução com o operador `Await` suspende a execução do método até que a tarefa esperada seja concluída. A tarefa representa um trabalho em andamento. Quando a tarefa associada ao operador de `Await` é concluída, a execução é retomada no mesmo método. Para obter mais informações, consulte [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).

Uma tarefa retornada por um método assíncrono pode terminar em um estado com falha, indicando que ele foi concluído devido a uma exceção sem tratamento. Uma tarefa também pode terminar em um estado cancelado, o que resulta em uma `OperationCanceledException` sendo gerada fora da expressão Await. Para detectar qualquer tipo de exceção, coloque a `Await` expressão associada à tarefa em um bloco de `Try` e Capture a exceção no bloco de `Catch`. Um exemplo é fornecido posteriormente neste tópico.

Uma tarefa pode estar em um estado com falha porque várias exceções foram responsáveis por sua falha. Por exemplo, a tarefa pode ser o resultado de uma chamada para <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Quando você aguarda tal tarefa, a exceção capturada é apenas uma das exceções, e você não pode prever qual exceção será detectada. Um exemplo é fornecido posteriormente neste tópico.

Uma expressão de `Await` não pode estar dentro de um bloco de `Catch` ou de um bloco de `Finally`.

## <a name="iterators"></a>{1&gt;Iteradores&lt;1}

Uma função de iterador ou acessador de `Get` executa uma iteração personalizada em uma coleção. Um iterador usa uma instrução [yield](yield-statement.md) para retornar cada elemento da coleção um de cada vez. Você chama uma função de iterador usando um [para cada... Próxima instrução](for-each-next-statement.md).

Uma instrução `Yield` pode estar dentro de um bloco de `Try`. Um bloco de `Try` que contém uma instrução `Yield` pode ter blocos de `Catch` e pode ter um bloco de `Finally`. Consulte a seção "blocos try em Visual Basic" de [iteradores](../../programming-guide/concepts/iterators.md) para obter um exemplo.

Uma instrução `Yield` não pode estar dentro de um bloco de `Catch` ou um bloco de `Finally`.

Se o corpo de `For Each` (fora da função de iterador) gerar uma exceção, um bloco de `Catch` na função de iterador não será executado, mas um bloco de `Finally` na função de iterador será executado. Um bloco de `Catch` dentro de uma função de iterador captura apenas as exceções que ocorrem dentro da função de iterador.

## <a name="partial-trust-situations"></a>Situações de confiança parcial

Em situações de confiança parcial, como um aplicativo hospedado em um compartilhamento de rede, `Try...Catch...Finally` não captura exceções de segurança que ocorrem antes que o método que contém a chamada seja invocado. O exemplo a seguir, quando você o coloca em um compartilhamento de servidor e executado a partir daí, produz o erro "System. Security. SecurityException: falha na solicitação." Para obter mais informações sobre exceções de segurança, consulte a classe <xref:System.Security.SecurityException>.

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

Nessa situação de confiança parcial, você precisa colocar a instrução `Process.Start` em um `Sub`separado. A chamada inicial para o `Sub` falhará. Isso permite que `Try...Catch` o acompanhe antes que o `Sub` que contém `Process.Start` seja iniciado e a exceção de segurança produzida.

## <a name="examples"></a>Exemplos

### <a name="the-structure-of-trycatchfinally"></a>A estrutura de try... Capturar... Disso

O exemplo a seguir ilustra a estrutura da instrução `Try...Catch...Finally`.

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>Exceção em um método chamado a partir de um bloco try

No exemplo a seguir, o método `CreateException` gera um `NullReferenceException`. O código que gera a exceção não está em um bloco de `Try`. Portanto, o método `CreateException` não trata a exceção. O método `RunSample` manipula a exceção porque a chamada para o método `CreateException` está em um bloco `Try`.

O exemplo inclui `Catch` instruções para vários tipos de exceções, ordenadas da mais específica para a mais geral.

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>A instrução Catch When

O exemplo a seguir mostra como usar uma instrução `Catch When` para filtrar em uma expressão condicional. Se a expressão condicional for avaliada como `True`, o código no bloco de `Catch` será executado.

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>Instruções Try aninhadas

O exemplo a seguir tem uma instrução `Try…Catch` que está contida em um bloco de `Try`. O bloco de `Catch` interno gera uma exceção que tem sua propriedade `InnerException` definida como a exceção original. O bloco de `Catch` externo relata sua própria exceção e a exceção interna.

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>Tratamento de exceção para métodos assíncronos

O exemplo a seguir ilustra o tratamento de exceção para métodos assíncronos. Para capturar uma exceção que se aplica a uma tarefa assíncrona, a expressão `Await` está em um bloco de `Try` do chamador e a exceção é capturada no bloco de `Catch`.

Remova a marca de comentário da linha `Throw New Exception` no exemplo para demonstrar o tratamento de exceção. A exceção é capturada no bloco de `Catch`, a propriedade `IsFaulted` da tarefa é definida como `True`e a propriedade `Exception.InnerException` da tarefa é definida como a exceção.

Remova a marca de comentário da linha `Throw New OperationCancelledException` para demonstrar o que acontece quando você cancela um processo assíncrono. A exceção é capturada no bloco de `Catch` e a propriedade `IsCanceled` da tarefa é definida como `True`. No entanto, em algumas condições que não se aplicam a este exemplo, `IsFaulted` é definido como `True` e `IsCanceled` é definido como `False`.

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>Manipulando várias exceções em métodos assíncronos

O exemplo a seguir ilustra a manipulação de exceção em que várias tarefas podem resultar em várias exceções. O bloco de `Try` tem a expressão `Await` para a tarefa que <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> retornada. A tarefa é concluída quando as três tarefas às quais <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> é aplicado são concluídas.

Cada uma das três tarefas causa uma exceção. O bloco de `Catch` itera através das exceções, que são encontradas na propriedade `Exception.InnerExceptions` da tarefa que `Task.WhenAll` retornada.

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>Veja também

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Instrução Exit](exit-statement.md)
- [Instrução On Error](on-error-statement.md)
- [Melhores práticas para usar snippets de código](/visualstudio/ide/best-practices-for-using-code-snippets)
- [Tratamento de Exceção](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Instrução Throw](throw-statement.md)
