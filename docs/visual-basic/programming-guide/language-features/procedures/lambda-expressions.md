---
title: Expressões lambda
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 1827eb5630ed217527de25fc9d9c2bb8994b9aff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249663"
---
# <a name="lambda-expressions-visual-basic"></a>Expressões lambda (Visual Basic)

Uma *expressão lambda* é uma função ou subrotina sem um nome que pode ser usado onde um delegado é válido. Expressões Lambda podem ser funções ou subrotinas e podem ser de linha única ou multi-linha. Você pode passar valores do escopo atual para uma expressão lambda.

> [!NOTE]
> A `RemoveHandler` declaração é uma exceção. Você não pode passar uma expressão lambda `RemoveHandler`para o parâmetro delegado de .

Você cria expressões lambda `Function` `Sub` usando a palavra-chave, assim como você cria uma função padrão ou subrotina. No entanto, expressões lambda são incluídas em uma declaração.

O exemplo a seguir é uma expressão lambda que incrementa seu argumento e retorna o valor. O exemplo mostra a sintaxe de expressão lambda de linha única e multi-linha para uma função.

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

O exemplo a seguir é uma expressão lambda que escreve um valor para o console. O exemplo mostra a sintaxe de expressão lambda de linha única e multilinha para uma subrotina.

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

Observe que nos exemplos anteriores as expressões lambda são atribuídas a um nome variável. Sempre que você se refere à variável, você invoca a expressão lambda. Você também pode declarar e invocar uma expressão lambda ao mesmo tempo, como mostrado no exemplo a seguir.

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

Uma expressão lambda pode ser devolvida como o valor de uma chamada de função (como é mostrado no exemplo na seção [Contexto](#context) mais tarde neste tópico), ou passada como um argumento para um parâmetro que toma um tipo de delegado, como mostrado no exemplo a seguir.

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a>Sintaxe da expressão lambda

A sintaxe de uma expressão lambda se assemelha à de uma função padrão ou subrotina. As diferenças são:

- Uma expressão lambda não tem um nome.

- Expressões lambda não podem ter `Overloads` modificadores, tais como ou `Overrides`.

- As funções de lambda de `As` linha única não usam uma cláusula para designar o tipo de retorno. Em vez disso, o tipo é inferido do valor que o corpo da expressão lambda avalia. Por exemplo, se o corpo da `cust.City = "London"`expressão lambda `Boolean`é, seu tipo de retorno é .

- Em funções de lambda multi-linha, você pode `As` especificar um tipo `As` de retorno usando uma cláusula ou omitir a cláusula para que o tipo de retorno seja inferido. Quando `As` a cláusula é omitida para uma função lambda multi-linha, o `Return` tipo de retorno é inferido como o tipo dominante de todas as instruções na função lambda multi-linha. O *tipo dominante* é um tipo único que todos os outros tipos podem ampliar. Se este tipo único não puder ser determinado, o tipo dominante é o tipo único que todos os outros tipos na matriz podem se restringir. Se nenhum desses tipos exclusivos puder ser determinado, o tipo dominante será `Object`. Neste caso, `Option Strict` se for `On`definido como , um erro de compilador ocorre.

     Por exemplo, se as expressões fornecidas à `Return` declaração contiverem valores de `Integer`tipo `Long`e `Double`, a matriz resultante for do tipo `Double`. Ambos `Integer` `Long` e `Double` ampliam `Double`para e somente . Portanto, `Double` é o tipo dominante. Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

- O corpo de uma função de linha única deve ser uma expressão que retorna um valor, não uma declaração. Não há `Return` declaração para funções de linha única. O valor devolvido pela função de linha única é o valor da expressão no corpo da função.

- O corpo de uma sub-rotina de linha única deve ser uma declaração de linha única.

- Funções e subrotinas de linha `End Function` única `End Sub` não incluem uma ou declaração.

- Você pode especificar o tipo de dados de `As` um parâmetro de expressão lambda usando a palavra-chave, ou o tipo de dados do parâmetro pode ser inferido. Todos os parâmetros devem ter tipos de dados especificados ou todos devem ser inferidos.

- `Optional`e `Paramarray` parâmetros não são permitidos.

- Parâmetros genéricos não são permitidos.

## <a name="async-lambdas"></a>Lambdas assíncronos

Você pode facilmente criar expressões e instruções lambda que incorporam processamento assíncrono usando as palavras-chave [Async](../../../../visual-basic/language-reference/modifiers/async.md) e [Aguardo Operador.](../../../../visual-basic/language-reference/operators/await-operator.md) Por exemplo, o exemplo do Windows Forms a seguir contém um manipulador de eventos que chama e espera um método assíncrono `ExampleMethodAsync`.

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

Você pode adicionar o mesmo manipulador de eventos usando uma lambda assíncrona em uma [declaração addhandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Para adicionar esse manipulador, adicione um modificador `Async` antes da lista de parâmetros lambda, como mostra o exemplo a seguir.

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

Para obter mais informações sobre como criar e usar métodos assíncronos, consulte [Programação Assíncrona com Assync e Aguarde](../../../../visual-basic/programming-guide/concepts/async/index.md).

## <a name="context"></a>Contexto

Uma expressão lambda compartilha seu contexto com o escopo dentro do qual é definida. Ele tem os mesmos direitos de acesso que qualquer código escrito no escopo de contenção. Isso inclui acesso a variáveis, funções e `Me`subs membros, e parâmetros e variáveis locais no escopo de contenção.

O acesso a variáveis e parâmetros locais no escopo de contenção pode se estender além da vida útil desse escopo. Enquanto um delegado referente a uma expressão lambda não estiver disponível para coleta de lixo, o acesso às variáveis no ambiente original é mantido. No exemplo a `target` seguir, `makeTheGame`a variável é local para `playTheGame` , o método no qual a expressão lambda é definida. Observe que a expressão lambda retornada, atribuída a `takeAGuess` in `Main` `target`, ainda tem acesso à variável local .

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

O exemplo a seguir demonstra a ampla gama de direitos de acesso da expressão lambda aninhada. Quando a expressão lambda retornada `Main` `aDel`é executada a partir de como, ele acessa esses elementos:

- Um campo da classe em que é definido:`aField`

- Uma propriedade da classe em que é definida:`aProp`

- Um parâmetro de `functionWithNestedLambda`método, no qual é definido:`level1`

- Uma variável `functionWithNestedLambda`local de:`localVar`

- Um parâmetro da expressão lambda em que está aninhado:`level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Conversão para um tipo de delegado

Uma expressão lambda pode ser implicitamente convertida para um tipo de delegado compatível. Para obter informações sobre os requisitos gerais para compatibilidade, consulte [Conversão de Delegado Relaxado](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Por exemplo, o exemplo de código a seguir mostra `Func(Of Integer, Boolean)` uma expressão lambda que implicitamente converte ou uma assinatura de delegado correspondente.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

O exemplo de código a seguir mostra uma `Sub(Of Double, String, Double)` expressão lambda que implicitamente se converte ou uma assinatura de delegado correspondente.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

Quando você atribui expressões lambda aos delegados ou passa-as como argumentos para os procedimentos, você pode especificar os nomes dos parâmetros, mas omitir seus tipos de dados, deixando que os tipos sejam retirados do delegado.

## <a name="examples"></a>Exemplos

- O exemplo a seguir define uma `True` expressão lambda que retorna se o `False` argumento do `Nothing`tipo de valor anulado tiver um valor atribuído e se seu valor for .

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- O exemplo a seguir define uma expressão lambda que retorna o índice do último elemento em uma matriz.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>Confira também

- [Procedimentos](./index.md)
- [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Declaração de função](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Tipos de valor anulados](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Como passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Como criar uma expressão lambda](./how-to-create-a-lambda-expression.md)
- [Conversão de delegado reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
