---
title: Instruções no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
ms.openlocfilehash: e66acae5e98d561883f4ad59853dfd862c8ebfee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946452"
---
# <a name="statements-in-visual-basic"></a>Instruções no Visual Basic

Uma instrução no Visual Basic é uma instrução completa. Ele pode conter as palavras-chave, operadores, variáveis, constantes e expressões. Cada instrução pertence a uma das seguintes categorias:

- **Instruções de declaração**, qual nome de uma variável, uma constante ou um procedimento e também pode especificar um tipo de dados.

- **Instruções executáveis**, qual iniciar as ações. Essas instruções podem chamar um método ou função, e eles podem executar um loop ou branch por meio de blocos de código. Incluem instruções executáveis **instruções de atribuição**, que atribui um valor ou expressão a uma variável ou constante.

Este tópico descreve cada categoria. Além disso, este tópico descreve como combinar várias instruções em uma única linha e como continuar uma instrução em várias linhas.

## <a name="declaration-statements"></a>Instruções de declaração

Você pode usar instruções de declaração para nomear e definem procedimentos, variáveis, propriedades, matrizes e constantes. Quando você declara um elemento de programação, você também pode definir seu tipo de dados, o nível de acesso e o escopo. Para obter mais informações, consulte [características do elemento declarado](./declared-elements/declared-element-characteristics.md).

O exemplo a seguir contém três declarações.

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

A primeira declaração é a `Sub` instrução. Junto com seus correspondentes `End Sub` instrução, ele declara um procedimento denominado `applyFormat`. Ela também especifica que `applyFormat` é `Public`, que significa que qualquer código que pode fazer referência a ele pode chamá-lo.

A segunda declaração é a `Const` instrução, que declara a constante `limit`, especificando o `Integer` tipo de dados e um valor de 33.

A terceira declaração é a `Dim` instrução, que declara a variável `thisWidget`. O tipo de dados é um objeto específico, ou seja, um objeto criado a partir de `Widget` classe. Você pode declarar uma variável para ser de qualquer tipo de dados elementar ou de qualquer tipo de objeto que é exposto no aplicativo que você está usando.

### <a name="initial-values"></a>Valores iniciais

Quando o código que contém uma instrução de declaração é executado, o Visual Basic reserva de memória exigida para o elemento declarado. Se o elemento contém um valor, o Visual Basic a inicializa com o valor padrão para seu tipo de dados. Para obter mais informações, consulte "Comportamento" em [instrução Dim](../../language-reference/statements/dim-statement.md).

Você pode atribuir um valor inicial para uma variável como parte de sua declaração, como mostra o exemplo a seguir.

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

Se uma variável é uma variável de objeto, você pode criar explicitamente uma instância de sua classe quando você declará-la usando o [novo operador](../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave, como o exemplo a seguir ilustra.

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

Observe que o valor inicial especificado em uma instrução de declaração não é atribuído a uma variável até que a execução atinge sua instrução de declaração. Até esse momento, a variável contém o valor padrão para seu tipo de dados.

## <a name="executable-statements"></a>Instruções executáveis

Uma instrução executável executa uma ação. Ele pode chamar um procedimento, o branch para outro lugar no código, o loop por meio de várias instruções, ou avaliar uma expressão. Uma instrução de atribuição é um caso especial de uma instrução executável.

O exemplo a seguir usa um `If...Then...Else` estrutura para executar diferentes blocos de código com base no valor de uma variável de controle. Dentro de cada bloco de código, um `For...Next` loop é executado em um número de vezes especificado.

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

O `If` instrução no exemplo anterior verifica o valor do parâmetro `clockwise`. Se o valor for `True`, ele chama o `spinClockwise` método `aWidget`. Se o valor for `False`, ele chama o `spinCounterClockwise` método `aWidget`. O `If...Then...Else` estrutura de controle termina com `End If`.

O `For...Next` loop em cada bloco chama o método apropriado um número de vezes igual ao valor da `revolutions` parâmetro.

## <a name="assignment-statements"></a>Instruções de atribuição

Instruções de atribuição realizarem operações de atribuição, que consistem em fazer o valor à direita do operador de atribuição (`=`) e armazená-lo no elemento à esquerda, como no exemplo a seguir.

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

No exemplo anterior, a instrução de atribuição armazena o valor literal 42 na variável `v`.

### <a name="eligible-programming-elements"></a>Elementos de programação qualificados

O elemento de programação no lado esquerdo do operador de atribuição deve ser capaz de aceitar e armazenar um valor. Isso significa que ele deve ser uma variável ou propriedade que não seja [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), ou deve ser um elemento de matriz. No contexto de uma instrução de atribuição, esse elemento é chamado, às vezes, uma *lvalue*, para "valor esquerdo".

O valor à direita do operador de atribuição é gerado por uma expressão, que pode consistir em qualquer combinação de literais, constantes, variáveis, propriedades, elementos de matriz, outras expressões ou chamadas de função. O exemplo a seguir ilustra essa situação.

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

O exemplo anterior adiciona o valor mantido na variável `y` para o valor mantido na variável `z`e, em seguida, adiciona o valor retornado pela chamada à função `findResult`. O valor total dessa expressão é armazenado na variável `x`.

### <a name="data-types-in-assignment-statements"></a>Tipos de dados em instruções de atribuição

Além dos valores numéricos, o operador de atribuição também pode atribuir `String` valores, como mostra o exemplo a seguir.

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

Você também pode atribuir `Boolean` valores, usando um `Boolean` literal ou um `Boolean` expressão, como o exemplo a seguir ilustra.

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

Da mesma forma, você pode atribuir os valores apropriados para elementos de programação do `Char`, `Date`, ou `Object` tipo de dados. Você também pode atribuir uma instância de objeto para um elemento declarado para ser da classe na qual essa instância é criada.

### <a name="compound-assignment-statements"></a>Instruções de atribuição composta

*Instruções de atribuição compostas* primeiro executar uma operação em uma expressão antes de atribuí-lo a um elemento de programação. O exemplo a seguir ilustra um destes operadores `+=`, que incrementa o valor da variável no lado esquerdo do operador pelo valor da expressão no lado direito.

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

O exemplo anterior adiciona 1 ao valor de `n`e, em seguida, armazena esse valor novo no `n`. É uma abreviação equivalente da instrução a seguir:

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

Uma variedade de operações de atribuição composta pode ser executada usando operadores desse tipo. Para obter uma lista desses operadores e obter mais informações sobre eles, consulte [operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md).

O operador de atribuição de concatenação (`&=`) é útil para adicionar uma cadeia de caracteres ao final da já existentes cadeias de caracteres, como mostra o exemplo a seguir.

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>Conversões de tipo em instruções de atribuição

O valor atribuído a uma variável, propriedade ou elemento da matriz deve ser de um tipo de dados adequado a esse elemento de destino. Em geral, você deve tentar gerar um valor do mesmo tipo de dados que o elemento de destino. No entanto, alguns tipos podem ser convertidos em outros tipos durante a atribuição.

Para obter informações sobre como converter entre tipos de dados, consulte [conversões de tipo no Visual Basic](./data-types/type-conversions.md). Em suma, o Visual Basic converte automaticamente um valor de um determinado tipo em qualquer outro tipo ao qual ele amplia. Um *conversão de ampliação* é um em que sempre terá êxito em tempo de execução e não perderá os dados. Por exemplo, o Visual Basic converte um `Integer` de valor para `Double` quando apropriado, pois `Integer` amplia a `Double`. Para obter mais informações, consulte [Ampliando e restringindo conversões](./data-types/widening-and-narrowing-conversions.md).

*Conversões de estreitamento* (aquelas que não são de ampliação) carregam um risco de falha em tempo de execução ou de perda de dados. Você pode executar uma conversão redutora explicitamente usando uma função de conversão de tipo, ou você pode direcionar o compilador a executar todas as conversões implicitamente pela configuração `Option Strict Off`. Para obter mais informações, consulte [conversões implícitas e explícitas](./data-types/implicit-and-explicit-conversions.md).

## <a name="putting-multiple-statements-on-one-line"></a>Colocar várias instruções em uma única linha

Você pode ter várias instruções em uma única linha, separada por dois-pontos (`:`) caracteres. O exemplo a seguir ilustra essa situação.

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

Embora, ocasionalmente, é conveniente, essa forma de sintaxe torna o código difícil de ler e manter. Portanto, é recomendável que você mantenha uma única instrução para uma linha.

## <a name="continuing-a-statement-over-multiple-lines"></a>Continuar uma instrução em várias linhas

Uma instrução geralmente se encaixa em uma única linha, mas quando ele for muito grande, você pode continuá-lo para a próxima linha usando uma sequência de continuação de linha, que consiste em um espaço seguido por um caractere de sublinhado (`_`) seguido por um retorno de carro. No exemplo a seguir, o `MsgBox` instrução executável é continuada em duas linhas.

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>Continuação implícita de linha

Em muitos casos, você pode continuar uma instrução na próxima linha consecutiva sem usar o caractere de sublinhado (`_`). Os seguintes elementos de sintaxe de instrução continuam implicitamente na próxima linha de código.

- Depois de uma vírgula (`,`). Por exemplo:

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- Após um parêntese de abertura (`(`) ou antes de um parêntese de fechamento (`)`). Por exemplo:

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- Depois de abrir uma chave (`{`) ou antes de uma chave de fechamento (`}`). Por exemplo:

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    Para obter mais informações, consulte [inicializadores de objeto: Tipos nomeados e anônimos](./objects-and-classes/object-initializers-named-and-anonymous-types.md) ou [inicializadores de coleção](./collection-initializers/index.md).

- Após um aberto de expressão incorporada (`<%=`) ou antes do fechamento de uma expressão inserida (`%>`) dentro de um literal XML. Por exemplo:

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   Para obter mais informações, consulte [expressões inseridas no XML](./xml/embedded-expressions-in-xml.md).

- Após o operador de concatenação (`&`). Por exemplo:

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   Para obter mais informações, consulte [operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Depois de operadores de atribuição (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`). Por exemplo:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Para obter mais informações, consulte [operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Depois de operadores binários (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) dentro de uma expressão. Por exemplo:

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   Para obter mais informações, consulte [operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Após o `Is` e `IsNot` operadores. Por exemplo:

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   Para obter mais informações, consulte [operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Depois de um caractere de qualificador de membro (`.`) e antes do nome do membro. Por exemplo:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   No entanto, você deve incluir um caractere de continuação de linha (`_`) após um caractere de qualificador de membro quando você estiver usando o `With` instrução ou fornecendo valores na lista de inicialização para um tipo. Considere a possibilidade de quebrar a linha após o operador de atribuição (por exemplo, `=`) quando você estiver usando `With` instruções ou listas de inicialização de objeto. Por exemplo:

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   Para obter mais informações, consulte [com... Terminar com a instrução](../../../visual-basic/language-reference/statements/with-end-with-statement.md) ou [inicializadores de objeto: Tipos nomeados e anônimos](./objects-and-classes/object-initializers-named-and-anonymous-types.md).

- Depois de um qualificador de propriedade de eixo XML (`.` ou `.@` ou `...`). No entanto, você deve incluir um caractere de continuação de linha (`_`) quando você especifica um qualificador de membro quando você estiver usando o `With` palavra-chave. Por exemplo:

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   Para obter mais informações, consulte [propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/index.md).

- Após um menor-que (<) de entrada ou antes de uma maior-sinal (`>`) quando você especifica um atributo. Além disso, após uma maior-sinal (`>`) quando você especifica um atributo. No entanto, você deve incluir um caractere de continuação de linha (`_`) quando você especifica os atributos de nível de assembly ou módulo. Por exemplo:

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   Para obter mais informações, consulte [visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md).

- Antes e depois de operadores de consulta (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, e `Descending`). Não é possível dividir uma linha entre as palavras-chave dos operadores de consulta que são compostos de várias palavras-chave (`Order By`, `Group Join`, `Take While`, e `Skip While`). Por exemplo:

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   Para obter mais informações, consulte [consultas](../../../visual-basic/language-reference/queries/index.md).

- Após o `In` palavra-chave em um `For Each` instrução. Por exemplo:

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   Para obter mais informações, consulte [para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md).

- Após o `From` palavra-chave em um inicializador de coleção. Por exemplo:

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   Para obter mais informações, consulte [Inicializadores de coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

## <a name="adding-comments"></a>Adicionando comentários

Código-fonte nem sempre é auto-explicativa, até mesmo para o programador que escreveu. Para ajudar a documentar seu código, portanto, a maioria dos programadores fazem uso liberal dos comentários inseridos. Comentários no código podem explicar um procedimento ou uma instrução específica para qualquer pessoa ler ou trabalhar com ele mais tarde. Visual Basic ignora os comentários durante a compilação, e elas não afetam o código compilado.

Linhas de comentários começam com um apóstrofo (`'`) ou `REM` seguido por um espaço. Eles podem ser adicionados em qualquer lugar no código, exceto em uma cadeia de caracteres. Para acrescentar um comentário a uma instrução, insira um apóstrofo ou `REM` depois da instrução, seguida de comentário. Comentários também podem entrar em sua própria linha separada. O exemplo a seguir demonstra essas possibilidades.

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>Verificação de erros de compilação

Se, depois que você digitar uma linha de código, a linha é exibida com um sublinhado ondulado em azul (uma mensagem de erro pode aparecer), há um erro de sintaxe na instrução. Você deve descobrir o que há de errado com a instrução (por procurando na lista de tarefas, ou passando o mouse sobre o erro com o ponteiro do mouse e ler a mensagem de erro) e corrigi-lo. Até que você resolveu todos os erros de sintaxe em seu código, seu programa não será compilado corretamente.

## <a name="related-sections"></a>Seções relacionadas

|Termo|Definição|
|---|---|
|[Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)|Fornece links para páginas de referência de linguagem que abrangem de operadores de atribuição, como `=`, `*=`, e `&=`.|
|[Operadores e Expressões](./operators-and-expressions/index.md)|Mostra como combinar elementos com operadores para gerar novos valores.|
|[Como: quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Mostra como dividir uma única instrução em várias linhas e como colocar várias instruções na mesma linha.|
|[Como: rotular instruções](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Mostra como rotular uma linha de código.|
