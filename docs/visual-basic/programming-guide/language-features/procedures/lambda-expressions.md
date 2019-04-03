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
ms.openlocfilehash: c43739e098a91d54d300fa7074d1563da179c0e9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832106"
---
# <a name="lambda-expressions-visual-basic"></a>Expressões lambda (Visual Basic)
Um *expressão lambda* é uma função ou sub-rotina sem um nome que pode ser usada sempre que um representante é válido. Expressões lambda podem ser funções ou sub-rotinas e podem ser uma linha ou várias linhas. Você pode passar valores do escopo atual para uma expressão lambda.  
  
> [!NOTE]
>  O `RemoveHandler` instrução é uma exceção. Você não pode passar uma expressão lambda para o parâmetro de representante `RemoveHandler`.  
  
 Criar expressões lambda usando o `Function` ou `Sub` palavra-chave, assim como criar uma função padrão ou a sub-rotina. No entanto, as expressões lambda são incluídas em uma instrução.  
  
 O exemplo a seguir é uma expressão lambda que aumenta seu argumento e retorna o valor. O exemplo mostra os dois a sintaxe da expressão lambda de linha única e várias linhas para uma função.  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
 O exemplo a seguir é uma expressão lambda que grava um valor no console. O exemplo mostra os dois a sintaxe da expressão lambda de linha única e várias linhas de uma sub-rotina.  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
 Observe que, nos exemplos anteriores, as expressões lambda são atribuídas a um nome de variável. Sempre que você faz referência à variável, você pode invocar a expressão lambda. Você também pode declarar e chamar uma expressão lambda ao mesmo tempo, conforme mostrado no exemplo a seguir.  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
 Uma expressão lambda pode ser retornada como o valor de uma chamada de função (conforme mostrado no exemplo o [contexto](#context) seção mais adiante neste tópico), ou passada como um argumento para um parâmetro que usa um tipo de delegado, como mostrado a seguir exemplo.  
  
 [!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]  
  
## <a name="lambda-expression-syntax"></a>Sintaxe da expressão lambda  
 A sintaxe de uma expressão lambda lembra a de uma função padrão ou a sub-rotina. As diferenças são da seguinte maneira:  
  
-   Uma expressão lambda não tem um nome.  
  
-   Expressões lambda não podem ter modificadores, como `Overloads` ou `Overrides`.  
  
-   As funções lambda de linha única não usam um `As` cláusula para designar o tipo de retorno. Em vez disso, o tipo é inferido do valor que avalia o corpo da expressão lambda. Por exemplo, se o corpo da expressão lambda é `cust.City = "London"`, seu tipo de retorno é `Boolean`.  
  
-   Em funções lambda de várias linhas, você pode especificar um tipo de retorno usando um `As` cláusula, ou omita o `As` cláusula para que o tipo de retorno é inferido. Quando o `As` cláusula é omitida para uma função lambda de várias linhas, o tipo de retorno é inferido como o tipo dominante de todos os `Return` instruções na função lambda de várias linhas. O *tipo dominante* é um tipo exclusivo que podem ampliar o todos os outros tipos. Se esse tipo exclusivo não puder ser determinado, o tipo dominante é o tipo exclusivo que todos os outros tipos na matriz podem restringir a. Se nenhum desses tipos exclusivos puder ser determinado, o tipo dominante será `Object`. Nesse caso, se `Option Strict` é definido como `On`, ocorre um erro do compilador.  
  
     Por exemplo, se as expressões são fornecidos para o `Return` instrução contêm valores do tipo `Integer`, `Long`, e `Double`, a matriz resultante é do tipo `Double`. Ambos `Integer` e `Long` ampliados com `Double` e somente `Double`. Portanto, `Double` é o tipo dominante. Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
-   O corpo de uma função de única linha deve ser uma expressão que retorna um valor, não uma instrução. Não há nenhum `Return` instrução para funções de linha única. O valor retornado pela função linha única é o valor da expressão no corpo da função.  
  
-   O corpo de uma sub-rotina de linha única deve ser uma instrução de linha única.  
  
-   Funções de linha única e as sub-rotinas não incluem um `End Function` ou `End Sub` instrução.  
  
-   Você pode especificar o tipo de dados de um parâmetro de expressão lambda usando o `As` palavra-chave ou o tipo de dados do parâmetro pode ser inferido. Ou todos os parâmetros devem ter especificado devem ser deduzidos a tipos de dados ou todos.  
  
-   `Optional` e `Paramarray` parâmetros não são permitidos.  
  
-   Parâmetros genéricos não são permitidos.  
  
## <a name="async-lambdas"></a>Lambdas assíncronos  
 Você pode facilmente criar expressões lambda e instruções que incorporem processamento assíncrono usando o [Async](../../../../visual-basic/language-reference/modifiers/async.md) e [operador Await](../../../../visual-basic/language-reference/operators/await-operator.md) palavras-chave. Por exemplo, o exemplo do Windows Forms a seguir contém um manipulador de eventos que chama e espera um método assíncrono `ExampleMethodAsync`.  
  
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
  
 Você pode adicionar o mesmo manipulador de eventos usando um lambda async em um [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Para adicionar esse manipulador, adicione um modificador `Async` antes da lista de parâmetros lambda, como mostra o exemplo a seguir.  
  
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
  
## <a name="context"></a> Contexto  
 Uma expressão lambda compartilha seu contexto com o escopo dentro do qual ele está definido. Ele tem os mesmos direitos de acesso que qualquer código escrito no escopo de contenção. Isso inclui acesso a variáveis de membro, funções e sub-rotinas, `Me`, parâmetros e variáveis locais no escopo de contenção.  
  
 Acesso a variáveis locais e parâmetros no escopo de contenção pode ultrapassar o tempo de vida desse escopo. Desde que um delegado referindo-se a uma expressão lambda não está disponível para coleta de lixo, o acesso às variáveis no ambiente original é mantido. No exemplo a seguir, a variável `target` é local para `makeTheGame`, o método no qual a expressão lambda `playTheGame` está definido. Observe que a expressão lambda retornado, atribuído a `takeAGuess` na `Main`, ainda tem acesso à variável local `target`.  
  
 [!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]  
  
 O exemplo a seguir demonstra uma ampla variedade de direitos de acesso da expressão lambda aninhada. Quando a expressão lambda retornado é executada a partir `Main` como `aDel`, ela acessa estes elementos:  
  
-   Um campo da classe na qual ela é definida: `aField`  
  
-   Uma propriedade da classe na qual ela é definida: `aProp`  
  
-   Um parâmetro de método `functionWithNestedLambda`, no qual ela está definida: `level1`  
  
-   Uma variável local de `functionWithNestedLambda`: `localVar`  
  
-   Um parâmetro da expressão lambda na qual ele está aninhado: `level2`  
  
 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]  
  
## <a name="converting-to-a-delegate-type"></a>Converter em um tipo de delegado  
 Uma expressão lambda pode ser convertida implicitamente em um tipo de delegado compatível. Para obter informações sobre os requisitos gerais para compatibilidade, consulte [conversão de delegado reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Por exemplo, o exemplo de código a seguir mostra uma expressão lambda que converte implicitamente a `Func(Of Integer, Boolean)` ou uma assinatura do delegado correspondente.  
  
 [!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]  
  
 O exemplo de código a seguir mostra uma expressão lambda que converte implicitamente a `Sub(Of Double, String, Double)` ou uma assinatura do delegado correspondente.  
  
 [!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]  
  
 Quando você atribuir as expressões lambda a delegados ou passá-los como argumentos para procedimentos, você pode especificar os nomes de parâmetro mas omitir seus tipos de dados, permitindo que os tipos a ser retirado do delegado.  
  
## <a name="examples"></a>Exemplos  
  
-   O exemplo a seguir define uma expressão lambda que retorna `True` se o argumento que permitem valor nulo tem um valor atribuído, e `False` se o valor for `Nothing`.  
  
     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]  
  
-   O exemplo a seguir define uma expressão lambda que retorna o índice do último elemento em uma matriz.  
  
     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Tipos de Valor Anulável](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Como: Passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Como: Criar uma expressão Lambda](./how-to-create-a-lambda-expression.md)
- [Conversão de Delegado Reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
