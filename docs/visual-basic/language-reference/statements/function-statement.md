---
title: Instrução Function (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 046a3a7d50d15cd3e59205998554a4c330d4552c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581841"
---
# <a name="function-statement-visual-basic"></a>Instrução Function (Visual Basic)

Declara o nome, os parâmetros e o código que definem um procedimento de `Function`.

## <a name="syntax"></a>Sintaxe

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a>Partes

- `attributelist`

  Opcional. Consulte a [lista de atributos](attribute-list.md).

- `accessmodifier`

  Opcional. Pode ser um dos seguintes:

  - [Público](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Privado](../../../visual-basic/language-reference/modifiers/private.md)

  - [Amigo Protegido](../../language-reference/modifiers/protected-friend.md)

  - [Particular Protegido](../../language-reference/modifiers/private-protected.md)

  Consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

- `proceduremodifiers`

  Opcional. Pode ser um dos seguintes:

  - [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Opcional. Consulte [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).

- `Shadows`

  Opcional. Consulte [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).

- `Async`

  Opcional. Consulte [Async](../../../visual-basic/language-reference/modifiers/async.md).

- `Iterator`

  Opcional. Consulte [iterador](../../../visual-basic/language-reference/modifiers/iterator.md).

- `name`

  Necessário. Nome do procedimento. Consulte [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

- `typeparamlist`

  Opcional. Lista de parâmetros de tipo para um procedimento genérico. Consulte [lista de tipos](type-list.md).

- `parameterlist`

  Opcional. Lista de nomes de variáveis locais que representam os parâmetros deste procedimento. Consulte a [lista de parâmetros](parameter-list.md).

- `returntype`

  Necessário se `Option Strict` for `On`. Tipo de dados do valor retornado por este procedimento.

- `Implements`

  Opcional. Indica que este procedimento implementa um ou mais procedimentos de `Function`, cada um definido em uma interface implementada por este procedimento que contém a classe ou a estrutura. Consulte a [instrução Implements](implements-statement.md).

- `implementslist`

  Necessário se `Implements` for fornecido. Lista de procedimentos de `Function` que estão sendo implementados.

  `implementedprocedure [ , implementedprocedure ... ]`

  Cada `implementedprocedure` tem a seguinte sintaxe e partes:

  `interface.definedname`

  |Parte|Descrição|
  |---|---|
  |`interface`|Necessário. Nome de uma interface implementada por este procedimento que contém a classe ou a estrutura.|
  |`definedname`|Necessário. Nome pelo qual o procedimento é definido em `interface`.|

- `Handles`

  Opcional. Indica que esse procedimento pode manipular um ou mais eventos específicos. Consulte [identificadores](handles-clause.md).

- `eventlist`

  Necessário se `Handles` for fornecido. Lista de eventos que este procedimento manipula.

  `eventspecifier [ , eventspecifier ... ]`

  Cada `eventspecifier` tem a seguinte sintaxe e partes:

  `eventvariable.event`

  |Parte|Descrição|
  |---|---|
  |`eventvariable`|Necessário. Variável de objeto declarada com o tipo de dados da classe ou estrutura que gera o evento.|
  |`event`|Necessário. Nome do evento que este procedimento manipula.|

- `statements`

  Opcional. Bloco de instruções a serem executadas neste procedimento.

- `End Function`

  Encerra a definição deste procedimento.

## <a name="remarks"></a>Comentários

Todo o código executável deve estar dentro de um procedimento. Cada procedimento, por sua vez, é declarado dentro de uma classe, uma estrutura ou um módulo que é chamado de classe, estrutura ou módulo que o contém.

Para retornar um valor para o código de chamada, use um procedimento de `Function`; caso contrário, use um procedimento `Sub`.

## <a name="defining-a-function"></a>Definindo uma função

Você pode definir um procedimento `Function` apenas no nível do módulo. Portanto, o contexto de declaração para uma função deve ser uma classe, uma estrutura, um módulo ou uma interface e não pode ser um arquivo de origem, um namespace, um procedimento ou um bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).

`Function` procedimentos padrão para acesso público. Você pode ajustar seus níveis de acesso com os modificadores de acesso.

Um procedimento `Function` pode declarar o tipo de dados do valor que o procedimento retorna. Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, uma estrutura, uma classe ou uma interface. Se você não especificar o parâmetro `returntype`, o procedimento retornará `Object`.

Se esse procedimento usar a palavra-chave `Implements`, a classe ou estrutura que a contém também deverá ter uma instrução `Implements` que siga imediatamente sua instrução `Class` ou `Structure`. A instrução `Implements` deve incluir cada interface especificada em `implementslist`. No entanto, o nome pelo qual uma interface define a `Function` (em `definedname`) não precisa corresponder ao nome desse procedimento (em `name`).

> [!NOTE]
> Você pode usar expressões lambda para definir expressões de função embutidas. Para obter mais informações, consulte [expressão de função](../../../visual-basic/language-reference/operators/function-expression.md) e [expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="returning-from-a-function"></a>Retornando de uma função

Quando o procedimento de `Function` retorna ao código de chamada, a execução continua com a instrução que segue a instrução que chamou o procedimento.

Para retornar um valor de uma função, você pode atribuir o valor ao nome da função ou incluí-lo em uma instrução `Return`.

A instrução `Return` atribui simultaneamente o valor de retorno e sai da função, como mostra o exemplo a seguir.

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

O exemplo a seguir atribui o valor de retorno ao nome da função `myFunction` e, em seguida, usa a instrução `Exit Function` para retornar.

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

As instruções `Exit Function` e `Return` causam uma saída imediata de um procedimento `Function`. Qualquer número de instruções `Exit Function` e `Return` pode aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Function` e instruções `Return`.

Se você usar `Exit Function` sem atribuir um valor a `name`, o procedimento retornará o valor padrão para o tipo de dados especificado em `returntype`. Se `returntype` não for especificado, o procedimento retornará `Nothing`, que é o valor padrão para `Object`.

## <a name="calling-a-function"></a>Chamando uma Função

Você chama um procedimento de `Function` usando o nome do procedimento, seguido pela lista de argumentos entre parênteses, em uma expressão. Você pode omitir os parênteses somente se não estiver fornecendo nenhum argumento. No entanto, seu código será mais legível se você sempre incluir os parênteses.

Você chama um procedimento `Function` da mesma maneira que chama qualquer função de biblioteca, como `Sqrt`, `Cos` ou `ChrW`.

Você também pode chamar uma função usando a palavra-chave `Call`. Nesse caso, o valor de retorno é ignorado. O uso da palavra-chave `Call` não é recomendado na maioria dos casos. Para obter mais informações, consulte [Call Statement](call-statement.md).

Às vezes, Visual Basic reorganiza as expressões aritméticas para aumentar a eficiência interna. Por esse motivo, você não deve usar um procedimento `Function` em uma expressão aritmética quando a função altera o valor de variáveis na mesma expressão.

## <a name="async-functions"></a>Funções assíncronas

O recurso *Async* permite invocar funções assíncronas sem usar retornos de chamada explícitos ou dividir manualmente seu código em várias funções ou expressões lambda.

Se você marcar uma função com o modificador [Async](../../../visual-basic/language-reference/modifiers/async.md) , poderá usar o operador [Await](../../../visual-basic/language-reference/operators/await-operator.md) na função. Quando o controle alcança uma expressão de `Await` na função `Async`, o controle retorna ao chamador e o progresso na função é suspenso até que a tarefa esperada seja concluída. Quando a tarefa for concluída, a execução poderá ser retomada na função.

> [!NOTE]
> Um procedimento `Async` retorna ao chamador quando encontra o primeiro objeto esperado que ainda não está completo, ou chega ao final do procedimento de `Async`, o que ocorrer primeiro.

Uma função `Async` pode ter um tipo de retorno de <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>. Um exemplo de uma função `Async` que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601> é fornecido abaixo.

Uma função `Async` não pode declarar parâmetros [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) .

Uma [instrução sub](sub-statement.md) também pode ser marcada com o modificador de `Async`. Isso é usado principalmente para manipuladores de eventos, em que um valor não pode ser retornado. Um procedimento de `Sub` `Async` não pode ser aguardado e o chamador de um procedimento de `Sub` `Async` não pode capturar exceções que são geradas pelo procedimento `Sub`.

Para obter mais informações sobre `Async` funções, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md), [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)e [tipos de retorno assíncronos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="iterator-functions"></a>Funções de iterador

Uma função de *iterador* executa uma iteração personalizada em uma coleção, como uma lista ou matriz. Uma função de iterador usa a instrução [yield](yield-statement.md) para retornar cada elemento um de cada vez. Quando uma instrução [yield](yield-statement.md) é atingida, o local atual no código é lembrado. A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.

Você chama um iterador do código do cliente usando um [para cada... Próxima](for-each-next-statement.md) instrução.

O tipo de retorno de uma função de iterador pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.

Para obter mais informações, consulte [Iteradores](../../programming-guide/concepts/iterators.md).

## <a name="example"></a>Exemplo

O exemplo a seguir usa a instrução `Function` para declarar o nome, os parâmetros e o código que formam o corpo de um procedimento de `Function`. O modificador `ParamArray` permite que a função aceite um número variável de argumentos.

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a>Exemplo

O exemplo a seguir invoca a função declarada no exemplo anterior.

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a>Exemplo

No exemplo a seguir, `DelayAsync` é uma `Function` de `Async` que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>. `DelayAsync` tem uma instrução `Return` que retorna um número inteiro. Portanto, a declaração de função de `DelayAsync` precisa ter um tipo de retorno de `Task(Of Integer)`. Como o tipo de retorno é `Task(Of Integer)`, a avaliação da expressão `Await` no `DoSomethingAsync` produz um inteiro. Isso é demonstrado nesta instrução: `Dim result As Integer = Await delayTask`.

O procedimento de `startButton_Click` é um exemplo de um procedimento de `Async Sub`. Como `DoSomethingAsync` é uma função `Async`, a tarefa para a chamada para `DoSomethingAsync` deve ser aguardada, como a instrução a seguir demonstra: `Await DoSomethingAsync()`. O procedimento de `Sub` de `startButton_Click` deve ser definido com o modificador de `Async` porque ele tem uma expressão de `Await`.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Consulte também

- [Instrução Sub](sub-statement.md)
- [Procedimentos de Função](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [Lista de Parâmetros](parameter-list.md)
- [Instrução Dim](dim-statement.md)
- [Instrução Call](call-statement.md)
- [Of](of-clause.md)
- [Matrizes de Parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Como usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Solução de problemas de Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Expressão de Função](../../../visual-basic/language-reference/operators/function-expression.md)
