---
title: Expressões lambda (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: c45500dc7a1e59a7ac83d43b826ca4cbfca6efb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654788"
---
# <a name="lambda-expressions-visual-basic"></a>Expressões lambda (Visual Basic)
Um *expressão lambda* é uma função ou sub-rotina sem um nome que pode ser usado sempre que um delegado é válido. Expressões lambda podem ser funções ou sub-rotinas e podem ser de linha única ou multilinha. Você pode passar valores do escopo atual para uma expressão lambda.  
  
> [!NOTE]
>  O `RemoveHandler` instrução é uma exceção. Você não pode passar uma expressão lambda para o parâmetro de representante `RemoveHandler`.  
  
 Criar expressões lambda usando o `Function` ou `Sub` palavra-chave, como criar uma função padrão ou sub-rotina. No entanto, as expressões lambda são incluídas em uma instrução.  
  
 O exemplo a seguir é uma expressão lambda que aumenta seu argumento e retorna o valor. O exemplo mostra dois a sintaxe da expressão lambda de linha e de várias linhas para uma função.  
  
 [!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 O exemplo a seguir é uma expressão lambda que grava um valor para o console. O exemplo mostra dois a sintaxe da expressão lambda de linha e de várias linhas de uma sub-rotina.  
  
 [!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 Observe que, nos exemplos anteriores, as expressões lambda são atribuídas a um nome de variável. Sempre que você faz referência à variável, você chama a expressão lambda. Você também pode declarar e chamar uma expressão lambda ao mesmo tempo, conforme mostrado no exemplo a seguir.  
  
 [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 Uma expressão lambda pode ser retornada como o valor de uma chamada de função (como é mostrado no exemplo o [contexto](#context) seção mais adiante neste tópico), ou passada como um argumento para um parâmetro que usa um tipo de delegado, conforme mostrado no exemplo a seguir exemplo.  
  
 [!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a>Sintaxe da expressão lambda  
 A sintaxe de uma expressão lambda é semelhante a de uma função padrão ou sub-rotina. As diferenças são da seguinte maneira:  
  
-   Uma expressão lambda não tem um nome.  
  
-   Expressões lambda não podem ter modificadores, como `Overloads` ou `Overrides`.  
  
-   Funções de única linha lambda não usam um `As` cláusula para designar o tipo de retorno. Em vez disso, o tipo é inferido do valor que o corpo da expressão lambda avalia. Por exemplo, se o corpo da expressão lambda é `cust.City = "London"`, seu tipo de retorno é `Boolean`.  
  
-   Em funções lambda de várias linhas, você pode especificar um tipo de retorno usando um `As` cláusula, ou omita o `As` cláusula para que o tipo de retorno é inferido. Quando o `As` cláusula for omitida de uma função lambda de várias linhas, o tipo de retorno é inferido para ser o tipo dominante de todos os `Return` instruções na função lambda de várias linhas. O *tipo dominante* é um tipo exclusivo alargue para todos os outros tipos. Se esse tipo exclusivo não pode ser determinado, o tipo dominante é o tipo exclusivo que todos os outros tipos de matriz podem restringir a. Se nenhum desses tipos exclusivos puder ser determinado, o tipo dominante será `Object`. Nesse caso, se `Option Strict` é definido como `On`, ocorre um erro do compilador.  
  
     Por exemplo, se as expressões são fornecidas para o `Return` instrução contêm valores do tipo `Integer`, `Long`, e `Double`, a matriz resultante é do tipo `Double`. Ambos `Integer` e `Long` alargar a `Double` e apenas `Double`. Portanto, `Double` é o tipo dominante. Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
-   O corpo de uma função de única linha deve ser uma expressão que retorna um valor, não uma instrução. Não há nenhum `Return` instrução para funções de única linha. O valor retornado pela função de única linha é o valor da expressão no corpo da função.  
  
-   O corpo de uma sub-rotina de linha deve ser instrução de linha única.  
  
-   Funções de linha única e sub-rotinas não incluem um `End Function` ou `End Sub` instrução.  
  
-   Você pode especificar o tipo de dados de um parâmetro de expressão lambda usando o `As` palavra-chave ou o tipo de dados do parâmetro pode ser inferido. Todos os parâmetros devem especificar os tipos de dados ou todos devem ser inferidos.  
  
-   `Optional` e `Paramarray` parâmetros não são permitidos.  
  
-   Parâmetros genéricos não são permitidos.  
  
## <a name="async-lambdas"></a>Lambdas assíncronos  
 Você pode facilmente criar expressões lambda e instruções que incorporam o processamento assíncrono usando o [Async](../../../../visual-basic/language-reference/modifiers/async.md) e [operador Await](../../../../visual-basic/language-reference/operators/await-operator.md) palavras-chave. Por exemplo, o exemplo do Windows Forms a seguir contém um manipulador de eventos que chama e espera um método assíncrono `ExampleMethodAsync`.  
  
```vb  
Public Class Form1  
  
    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' ExampleMethodAsync returns a Task.  
        Await ExampleMethodAsync()  
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 Você pode adicionar o mesmo manipulador de eventos por meio de uma lambda assíncrona em um [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Para adicionar esse manipulador, adicione um modificador `Async` antes da lista de parâmetros lambda, como mostra o exemplo a seguir.  
  
```vb  
Public Class Form1  
  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AddHandler Button1.Click,   
            Async Sub(sender1, e1)  
                ' ExampleMethodAsync returns a Task.  
                Await ExampleMethodAsync()  
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."  
            End Sub  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 Para obter mais informações sobre como criar e usar os métodos assíncronos, consulte [programação assíncrona com Async e Await](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
##  <a name="context"></a> Contexto  
 Uma expressão lambda compartilha seu contexto com o escopo dentro do qual ela está definida. Ele tem os mesmos direitos de acesso que qualquer código escrito no escopo de contenção. Isso inclui acesso a variáveis de membro, funções e sub-rotinas, `Me`e parâmetros e variáveis locais no escopo de contenção.  
  
 Acesso a variáveis locais e parâmetros no escopo de contenção pode ultrapassar o tempo de vida desse escopo. Como um delegado que faz referência a uma expressão lambda não está disponível para coleta de lixo, o acesso às variáveis no ambiente original é mantido. No exemplo a seguir, a variável `target` é local para `makeTheGame`, o método no qual a expressão lambda `playTheGame` está definido. Observe que a expressão lambda retornada, atribuída a `takeAGuess` na `Main`, ainda tem acesso à variável local `target`.  
  
 [!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 O exemplo a seguir demonstra uma ampla variedade de direitos de acesso da expressão lambda aninhada. Quando a expressão lambda retornado é executada de `Main` como `aDel`, ela acessa estes elementos:  
  
-   Um campo da classe na qual ela está definida: `aField`  
  
-   Uma propriedade da classe na qual ela está definida: `aProp`  
  
-   Um parâmetro de método `functionWithNestedLambda`, no qual ela está definida: `level1`  
  
-   Uma variável local de `functionWithNestedLambda`: `localVar`  
  
-   Um parâmetro da expressão lambda na qual ele está aninhado: `level2`  
  
 [!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a>Converter para um tipo delegado  
 Uma expressão lambda pode ser convertida implicitamente para um tipo de representante compatível. Para obter informações sobre os requisitos gerais para compatibilidade, consulte [conversão de delegado reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Por exemplo, o exemplo de código a seguir mostra uma expressão lambda que implicitamente converte em `Func(Of Integer, Boolean)` ou uma assinatura do delegado correspondente.  
  
 [!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 O exemplo de código a seguir mostra uma expressão lambda que implicitamente converte em `Sub(Of Double, String, Double)` ou uma assinatura do delegado correspondente.  
  
 [!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 Quando você atribui expressões lambda a representantes ou passá-las como argumentos para procedimentos, você pode especificar os nomes de parâmetro mas omitir seus tipos de dados, permitindo que os tipos de ser extraídos do representante.  
  
## <a name="examples"></a>Exemplos  
  
-   O exemplo a seguir define uma expressão lambda que retorna `True` se o argumento anulável tem um valor atribuído, e `False` se o valor for `Nothing`.  
  
     [!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   O exemplo a seguir define uma expressão lambda que retorna o índice do último elemento em uma matriz.  
  
     [!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Tipos de Valor Anulável](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Como passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [Como criar uma expressão lambda](./how-to-create-a-lambda-expression.md)  
 [Conversão de Delegado Reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
