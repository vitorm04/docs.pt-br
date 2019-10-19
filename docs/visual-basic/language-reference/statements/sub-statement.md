---
title: Instrução Sub (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: 7dc0ea1f1b30f5ffb0db8917538adf440c5ef891
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583195"
---
# <a name="sub-statement-visual-basic"></a>Instrução Sub (Visual Basic)

Declara o nome, os parâmetros e o código que definem um procedimento de `Sub`.

## <a name="syntax"></a>Sintaxe

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a>Partes

- `attributelist`

  Opcional. Consulte a [lista de atributos](attribute-list.md).

- `Partial`

  Opcional. Indica a definição de um método parcial. Consulte [métodos parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).

- `accessmodifier`

  Opcional. Pode ser um dos seguintes:

  - [Público](../modifiers/public.md)

  - [Protegido](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Privado](../modifiers/private.md)

  - [Amigo Protegido](../../language-reference/modifiers/protected-friend.md)

  - [Particular Protegido](../../language-reference/modifiers/private-protected.md)

  Consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

- `proceduremodifiers`

  Opcional. Pode ser um dos seguintes:

  - [Sobrecargas](../modifiers/overloads.md)

  - [Substituições](../modifiers/overrides.md)

  - [Substituível](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Opcional. Consulte [compartilhado](../modifiers/shared.md).

- `Shadows`

  Opcional. Consulte [Shadows](../modifiers/shadows.md).

- `Async`

  Opcional. Consulte [Async](../modifiers/async.md).

- `name`

  Necessário. Nome do procedimento. Consulte [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Para criar um procedimento de construtor para uma classe, defina o nome de um procedimento `Sub` para a palavra-chave `New`. Para obter mais informações, consulte [tempo de vida do objeto: como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

- `typeparamlist`

  Opcional. Lista de parâmetros de tipo para um procedimento genérico. Consulte [lista de tipos](type-list.md).

- `parameterlist`

  Opcional. Lista de nomes de variáveis locais que representam os parâmetros deste procedimento. Consulte a [lista de parâmetros](parameter-list.md).

- `Implements`

  Opcional. Indica que este procedimento implementa um ou mais procedimentos de `Sub`, cada um definido em uma interface implementada por este procedimento que contém a classe ou a estrutura. Consulte a [instrução Implements](implements-statement.md).

- `implementslist`

  Necessário se `Implements` for fornecido. Lista de procedimentos de `Sub` que estão sendo implementados.

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

- `End Sub`

  Encerra a definição deste procedimento.

## <a name="remarks"></a>Comentários

Todo o código executável deve estar dentro de um procedimento. Use um procedimento `Sub` quando não quiser retornar um valor para o código de chamada. Use um procedimento `Function` quando desejar retornar um valor.

## <a name="defining-a-sub-procedure"></a>Definindo um procedimento Sub

Você pode definir um procedimento `Sub` apenas no nível do módulo. O contexto de declaração para um procedimento Sub deve, portanto, ser uma classe, uma estrutura, um módulo ou uma interface e não pode ser um arquivo de origem, um namespace, um procedimento ou um bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).

`Sub` procedimentos padrão para acesso público. Você pode ajustar seus níveis de acesso usando os modificadores de acesso.

Se o procedimento usa a palavra-chave `Implements`, a classe ou estrutura que a contém deve ter uma instrução `Implements` que segue imediatamente sua instrução `Class` ou `Structure`. A instrução `Implements` deve incluir cada interface especificada em `implementslist`. No entanto, o nome pelo qual uma interface define a `Sub` (em `definedname`) não precisa corresponder ao nome desse procedimento (em `name`).

## <a name="returning-from-a-sub-procedure"></a>Retornando de um procedimento Sub

Quando um procedimento de `Sub` retorna ao código de chamada, a execução continua com a instrução após a instrução que a chamou.

O exemplo a seguir mostra um retorno de um procedimento de `Sub`.

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

As instruções `Exit Sub` e `Return` causam uma saída imediata de um procedimento `Sub`. Qualquer número de instruções `Exit Sub` e `Return` pode aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Sub` e instruções `Return`.

## <a name="calling-a-sub-procedure"></a>Chamando um procedimento Sub

Você chama um procedimento de `Sub` usando o nome do procedimento em uma instrução e, em seguida, seguindo esse nome com sua lista de argumentos entre parênteses. Você pode omitir os parênteses somente se não fornecer argumentos. No entanto, seu código será mais legível se você sempre incluir os parênteses.

Um procedimento `Sub` e um procedimento de `Function` podem ter parâmetros e executar uma série de instruções. No entanto, um procedimento de `Function` retorna um valor e um procedimento de `Sub` não. Portanto, você não pode usar um procedimento `Sub` em uma expressão.

Você pode usar a palavra-chave `Call` ao chamar um procedimento de `Sub`, mas essa palavra-chave não é recomendada para a maioria dos usos. Para obter mais informações, consulte [Call Statement](call-statement.md).

Às vezes, Visual Basic reorganiza as expressões aritméticas para aumentar a eficiência interna. Por esse motivo, se a lista de argumentos incluir expressões que chamam outros procedimentos, você não deve presumir que essas expressões serão chamadas em uma ordem específica.

## <a name="async-sub-procedures"></a>Procedimentos Async sub

Usando o recurso assíncrono, você pode invocar funções assíncronas sem usar retornos de chamada explícitos ou dividir manualmente seu código em várias funções ou expressões lambda.

Se você marcar um procedimento com o modificador [Async](../modifiers/async.md) , poderá usar o operador [Await](../../../visual-basic/language-reference/operators/await-operator.md) no procedimento. Quando o controle alcança uma expressão de `Await` no procedimento de `Async`, o controle retorna ao chamador e o progresso no procedimento é suspenso até que a tarefa esperada seja concluída. Quando a tarefa for concluída, a execução poderá ser retomada no procedimento.

> [!NOTE]
> Um procedimento `Async` retorna ao chamador quando o primeiro objeto esperado que ainda não está concluído é encontrado ou o final do procedimento `Async` é atingido, o que ocorrer primeiro.

Você também pode marcar uma [instrução de função](function-statement.md) com o modificador de `Async`. Uma função `Async` pode ter um tipo de retorno de <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>. Um exemplo mais adiante neste tópico mostra uma função `Async` que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>.

os procedimentos de `Sub` `Async` são usados principalmente para manipuladores de eventos, em que um valor não pode ser retornado. Um procedimento de `Sub` `Async` não pode ser aguardado e o chamador de um procedimento de `Sub` `Async` não pode capturar exceções que o procedimento de `Sub` gera.

Um procedimento de `Async` não pode declarar parâmetros [ByRef](../modifiers/byref.md) .

Para obter mais informações sobre procedimentos `Async`, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md), [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)e [tipos de retorno assíncronos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="example"></a>Exemplo

O exemplo a seguir usa a instrução `Sub` para definir o nome, os parâmetros e o código que formam o corpo de um procedimento de `Sub`.

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a>Exemplo

No exemplo a seguir, `DelayAsync` é uma `Function` de `Async` que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>. `DelayAsync` tem uma instrução `Return` que retorna um número inteiro. Portanto, a declaração de função de `DelayAsync` deve ter um tipo de retorno de `Task(Of Integer)`. Como o tipo de retorno é `Task(Of Integer)`, a avaliação da expressão `Await` no `DoSomethingAsync` produz um inteiro, como mostra a instrução a seguir: `Dim result As Integer = Await delayTask`.

O procedimento de `startButton_Click` é um exemplo de um procedimento de `Async Sub`. Como `DoSomethingAsync` é uma função `Async`, a tarefa para a chamada para `DoSomethingAsync` deve ser aguardada, como mostra a instrução a seguir: `Await DoSomethingAsync()`. O procedimento de `Sub` de `startButton_Click` deve ser definido com o modificador de `Async` porque ele tem uma expressão de `Await`.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Consulte também

- [Instrução Implements](implements-statement.md)
- [Instrução Function](function-statement.md)
- [Lista de Parâmetros](parameter-list.md)
- [Instrução Dim](dim-statement.md)
- [Instrução Call](call-statement.md)
- [Of](of-clause.md)
- [Matrizes de Parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Como usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Solução de problemas de Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Métodos Parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
