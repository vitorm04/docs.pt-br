---
title: Try... Catch... Instrução Finally – Visual Basic
description: Saiba como usar tratamento de exceções com o Visual Basic instruções Try/Catch/Finally.
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
ms.openlocfilehash: 126f20c86bb47e8002382e069ce6236600394aba
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638766"
---
# <a name="trycatchfinally-statement-visual-basic"></a>Instrução Try...Catch...Finally (Visual Basic)

Fornece uma maneira de lidar com alguns ou todos os erros possíveis que podem ocorrer em um determinado bloco de código, executando ainda o código.

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
|`tryStatements`|Opcional. Instruções onde pode ocorrer um erro. Pode ser uma instrução composta.|
|`Catch`|Opcional. Vários `Catch` blocos permitidos. Se ocorrer uma exceção ao processar o `Try` bloquear, cada `Catch` instrução é examinada na ordem textual para determinar se ele trata a exceção, com `exception` que representa a exceção que foi lançada.|
|`exception`|Opcional. Qualquer nome de variável. O valor inicial de `exception` é o valor do erro gerado. Usado com `Catch` especificar o erro detectado. Se omitido, o `Catch` instrução captura qualquer exceção.|
|`type`|Opcional. Especifica o tipo de filtro de classe. Se o valor de `exception` é do tipo especificado pelo `type` ou de um tipo derivado, o identificador se torna associado ao objeto de exceção.|
|`When`|Opcional. Um `Catch` instrução com uma `When` cláusula captura exceções somente quando `expression` é avaliada como `True`. Um `When` cláusula é aplicada somente depois de verificar o tipo de exceção, e `expression` podem se referir ao identificador que representa a exceção.|
|`expression`|Opcional. Deve ser implicitamente conversível para `Boolean`. Qualquer expressão que descreve um filtro genérico. Normalmente usado para filtrar por número do erro. Usado com `When` palavra-chave para especificar as circunstâncias sob as quais o erro for detectado.|
|`catchStatements`|Opcional. Instruções para tratar erros que ocorrem em associado `Try` bloco. Pode ser uma instrução composta.|
|`Exit Try`|Opcional. Palavra-chave que é interrompida do `Try...Catch...Finally` estrutura. Retoma a execução com o código que segue imediatamente o `End Try` instrução. O `Finally` instrução ainda será executada. Não é permitido em `Finally` blocos.|
|`Finally`|Opcional. Um `Finally` bloco sempre será executado quando a execução deixar qualquer parte do `Try...Catch` instrução.|
|`finallyStatements`|Opcional. Instruções que são executadas após a ocorrência de outro processamento de erro.|
|`End Try`|Encerra o `Try...Catch...Finally` estrutura.|

## <a name="remarks"></a>Comentários

Se você espera que uma exceção específica pode ocorrer durante uma determinada seção de código, coloque o código em um `Try` bloquear e usar um `Catch` bloco para manter o controle e tratar a exceção se ocorrer.

Um `Try…Catch` instrução consiste em um `Try` bloco seguido por um ou mais `Catch` cláusulas, que especificam os manipuladores para várias exceções. Quando uma exceção é gerada um `Try` bloquear, Visual Basic procura o `Catch` instrução que trata a exceção. Se encontrar uma correspondência `Catch` instrução não for encontrada, o Visual Basic examina o método que chamou o método atual, e assim por diante para cima a pilha de chamadas. Se nenhum `Catch` bloco for encontrado, o Visual Basic exibe uma mensagem de exceção sem tratamento para o usuário e interrompe a execução do programa.

Você pode usar mais de uma `Catch` instrução em um `Try…Catch` instrução. Se você fizer isso, a ordem dos `Catch` cláusulas é significativo porque eles são examinados em ordem. Capture as exceções mais específicas antes das menos específicas.

O seguinte `Catch` condições de instrução são menos específicas e irá capturar todas as exceções que derivam do <xref:System.Exception> classe. Você normalmente deve usar um dessas variações como a última `Catch` bloquear o `Try...Catch...Finally` estrutura, depois de capturar todas as exceções específicas que você espera. Fluxo de controle nunca pode atingir um `Catch` bloco que segue a qualquer uma dessas variações.

- O `type` é `Exception`, por exemplo: `Catch ex As Exception`

- A instrução não tem nenhum `exception` variável, por exemplo: `Catch`

Quando um `Try…Catch…Finally` instrução está aninhada em outro `Try` bloco, Visual Basic primeiro examina cada `Catch` instrução em mais interna `Try` bloco. Se nenhuma correspondência `Catch` instrução for encontrada, a pesquisa continua para a `Catch` instruções de externo `Try…Catch…Finally` bloco.

Variáveis locais de um `Try` bloco não estão disponíveis em um `Catch` bloquear porque eles são blocos separados. Se você quiser usar uma variável em mais de um bloco, declarar a variável de fora a `Try...Catch...Finally` estrutura.

> [!TIP]
> O `Try…Catch…Finally` instrução está disponível como um trecho de código do IntelliSense. No Gerenciador de trechos de código, expanda **padrões de código - se, para cada um, Try Catch, propriedade, etc**e então **tratamento de erros (exceções)**. Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).

## <a name="finally-block"></a>Bloco Finally

Se você tiver uma ou mais instruções que devem ser executados antes de sair do `Try` estrutura, use um `Finally` bloco. O controle passa para o `Finally` bloquear logo antes do `Try…Catch` estrutura. Isso é verdadeiro mesmo se uma exceção ocorre em qualquer lugar dentro do `Try` estrutura.

Um `Finally` bloco é útil para executar qualquer código que deve executar, mesmo se houver uma exceção. O controle é passado para o `Finally` bloco, independentemente de como o `Try...Catch` bloquear sai.

O código em um `Finally` execução do bloco, mesmo se seu código encontrar uma `Return` instrução em um `Try` ou `Catch` bloco. Controle não passa de um `Try` ou `Catch` bloquear para os respectivos `Finally` bloquear nos seguintes casos:

- Uma [instrução End](end-statement.md) for encontrado na `Try` ou `Catch` bloco.

- Um <xref:System.StackOverflowException> é gerada em de `Try` ou `Catch` bloco.

Não é válido para transferir explicitamente a execução em um `Finally` bloco. Transferir a execução de um `Finally` bloco não for válido, exceto por meio de uma exceção.

Se um `Try` instrução não contém pelo menos um `Catch` bloco, ele deve conter um `Finally` bloco.

> [!TIP]
> Se você não precisa capturar exceções específicas, o `Using` instrução se comporta como um `Try…Finally` bloco e garante o descarte dos recursos, independentemente de como você sai do bloco. Isso é verdadeiro mesmo com uma exceção sem tratamento. Para obter mais informações, consulte [Instrução using](using-statement.md).

## <a name="exception-argument"></a>Argumento de exceção

O `Catch` bloco `exception` argumento é uma instância da <xref:System.Exception> classe ou uma classe que deriva de `Exception` classe. O `Exception` instância da classe corresponde ao erro que ocorreu no `Try` bloco.

As propriedades do `Exception` ajuda para identificar a causa e a localização de uma exceção do objeto. Por exemplo, o <xref:System.Exception.StackTrace%2A> propriedade lista os métodos chamados que conduziram à exceção, ajudando você a localizar onde o erro ocorreu no código. <xref:System.Exception.Message%2A> Retorna uma mensagem que descreve a exceção. <xref:System.Exception.HelpLink%2A> Retorna um link para um arquivo de ajuda associado. <xref:System.Exception.InnerException%2A> Retorna o `Exception` retorna o objeto que causou a exceção atual, ou ele `Nothing` se não houver nenhum original `Exception`.

## <a name="considerations-when-using-a-trycatch-statement"></a>Considerações ao usar um bloco Try... Instrução catch

Use um `Try…Catch` instrução somente para sinalizar a ocorrência de eventos do programa incomuns ou inesperados. Motivos para isso incluem o seguinte:

- Capturando exceções no tempo de execução cria uma sobrecarga adicional e provavelmente será mais lento do que a pré-verificação de para evitar exceções.

- Se um `Catch` bloco não é manipulado corretamente, a exceção não pode ser relatada corretamente para os usuários.

- Tratamento de exceção faz com que um programa mais complexos.

Você não precisa sempre um `Try…Catch` instrução para verificar se há uma condição que é provável de ocorrer. O exemplo a seguir verifica se um arquivo existe antes de tentar abri-lo. Isso reduz a necessidade de capturar uma exceção lançada pelo <xref:System.IO.File.OpenText%2A> método.

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

Garantir que o código em `Catch` blocos podem relatar corretamente as exceções para os usuários, seja por meio de registro em log de thread-safe ou mensagens apropriadas. Caso contrário, as exceções podem permanecer desconhecidas.

## <a name="async-methods"></a>Métodos assíncronos

Se você marcar um método com o [Async](../modifiers/async.md) modificador, você pode usar o [Await](../operators/await-operator.md) operador no método. Uma instrução com o `Await` operador suspende a execução do método até que a tarefa aguardada seja concluída. A tarefa representa um trabalho em andamento. Quando a tarefa que está associada com o `Await` operador termina, retoma a execução no mesmo método. Para obter mais informações, consulte [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).

Uma tarefa retornada por um método assíncrono pode terminar com um estado de falha, indicando que ela foi concluída devido a uma exceção sem tratamento. Uma tarefa também pode terminar com um estado cancelado, o que resulta em um `OperationCanceledException` sendo lançadas fora a expressão await. Para capturar qualquer tipo de exceção, coloque o `Await` expressão associada com a tarefa em um `Try` bloquear e capturar a exceção no `Catch` bloco. Um exemplo é fornecido neste tópico.

Uma tarefa pode ser em um estado de falha, porque várias exceções eram responsáveis por sua falha. Por exemplo, a tarefa pode ser o resultado de uma chamada para <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Quando você espera uma tarefa, a exceção capturada é apenas uma das exceções, e você não pode prever qual exceção será capturada. Um exemplo é fornecido neste tópico.

Uma `Await` expressão não pode ser dentro de uma `Catch` bloco ou `Finally` bloco.

## <a name="iterators"></a>Iterators

Uma função de iterador ou `Get` acessador realiza uma iteração personalizada em uma coleção. Um iterador usa uma [Yield](yield-statement.md) instrução para retornar cada elemento da coleção um por vez. Chamar uma função de iterador usando uma [para cada um... Próxima instrução](for-each-next-statement.md).

Um `Yield` instrução pode ser dentro de um `Try` bloco. Um `Try` bloco que contém uma `Yield` instrução pode ter `Catch` bloqueia e pode ter um `Finally` bloco. Consulte a seção "Experimente blocos no Visual Basic" [iteradores](../../programming-guide/concepts/iterators.md) para obter um exemplo.

Um `Yield` instrução não pode estar dentro de uma `Catch` bloco ou uma `Finally` bloco.

Se o `For Each` corpo (fora da função de iterador) lança uma exceção, uma `Catch` bloco na função de iterador não é executado, mas um `Finally` bloco na função de iterador será executado. Um `Catch` bloco dentro de uma função de iterador captura somente exceções que ocorrem dentro da função de iterador.

## <a name="partial-trust-situations"></a>Situações de confiança parcial

Em situações de confiança parcial, como um aplicativo hospedado em um compartilhamento de rede, `Try...Catch...Finally` não capturará exceções de segurança que ocorrem antes que o método que contém a chamada é invocado. O exemplo a seguir, quando você colocá-lo em um compartilhamento de servidor e executar a partir daí, produz o erro "System.Security.SecurityException: Falha na solicitação." Para obter mais informações sobre exceções de segurança, consulte o <xref:System.Security.SecurityException> classe.

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

Em tal uma situação de confiança parcial, você precisa colocar o `Process.Start` instrução em um separado `Sub`. A chamada inicial para o `Sub` falhará. Isso permite `Try...Catch` quer capturá-la antes do `Sub` que contém `Process.Start` é iniciado e a exceção de segurança produzidos.

## <a name="examples"></a>Exemplos

### <a name="the-structure-of-trycatchfinally"></a>A estrutura de Try... Catch... Por fim

O exemplo a seguir ilustra a estrutura do `Try...Catch...Finally` instrução.

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>Exceção em um método chamado a partir de um bloco Try

No exemplo a seguir, o `CreateException` método lança um `NullReferenceException`. O código que gera a exceção não está em um `Try` bloco. Portanto, o `CreateException` não lidam com a exceção. O `RunSample` lidam com a exceção porque a chamada para o `CreateException` método está em um `Try` bloco.

O exemplo inclui `Catch` instruções para vários tipos de exceções, ordenados do mais específico para o mais geral.

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>A instrução Catch quando

O exemplo a seguir mostra como usar um `Catch When` instrução para filtrar em uma expressão condicional. Se a expressão condicional é avaliada como `True`, o código a `Catch` execução do bloco.

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>Instruções de Try aninhadas

O exemplo a seguir tem um `Try…Catch` instrução que está contida em um `Try` bloco. Interno `Catch` bloco lançar uma exceção que tem seu `InnerException` propriedade definida para a exceção original. Externo `Catch` bloco relata sua própria exceção e a exceção interna.

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>Tratamento de exceção para métodos assíncronos

O exemplo a seguir ilustra o tratamento de exceção para métodos assíncronos. Para capturar uma exceção que se aplica a uma tarefa assíncrona, o `Await` expressão está em um `Try` bloco do chamador e a exceção é capturado no `Catch` bloco.

Remova a marca de comentário da linha `Throw New Exception` no exemplo para demonstrar o tratamento de exceção. A exceção é capturada na `Catch` bloquear, a tarefa `IsFaulted` estiver definida como `True`e a tarefa `Exception.InnerException` estiver definida como a exceção.

Remova a marca de comentário da linha `Throw New OperationCancelledException` para demonstrar o que acontece quando você cancela um processo assíncrono. A exceção é capturada na `Catch` bloco e a tarefa `IsCanceled` estiver definida como `True`. No entanto, em algumas condições que não se aplicam a este exemplo, `IsFaulted` é definido como `True` e `IsCanceled` é definido como `False`.

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>Manipulando várias exceções nos métodos assíncronos

O exemplo a seguir ilustra a manipulação de exceção em que várias tarefas podem resultar em várias exceções. O `Try` bloco tem o `Await` expressão para a tarefa que <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> retornado. A tarefa é concluída quando as três tarefas para o qual <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> é aplicado estão concluídas.

Cada uma das três tarefas causa uma exceção. O `Catch` bloco itera por meio de exceções, que se encontram na `Exception.InnerExceptions` propriedade da tarefa que `Task.WhenAll` retornado.

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Instrução Exit](exit-statement.md)
- [Instrução On Error](on-error-statement.md)
- [Melhores práticas para usar snippets de código](/visualstudio/ide/best-practices-for-using-code-snippets)
- [Tratamento de Exceção](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Instrução Throw](throw-statement.md)
