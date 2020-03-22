---
title: Instruções
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
ms.openlocfilehash: f63f0f0212913f95baab2a8a43c4b7f25a859cd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400886"
---
# <a name="statements-in-visual-basic"></a>Instruções no Visual Basic

Uma declaração no Visual Basic é uma instrução completa. Pode conter palavras-chave, operadores, variáveis, constantes e expressões. Cada declaração pertence a uma das seguintes categorias:

- **Declarações De Declaração**, que nomeiam uma variável, constante ou procedimento, e também podem especificar um tipo de dados.

- **Declarações executáveis,** que iniciam ações. Essas instruções podem chamar um método ou função, e podem fazer loop ou ramificar através de blocos de código. As instruções executáveis incluem **Declarações de Atribuição,** que atribuem um valor ou expressão a uma variável ou constante.

Este tópico descreve cada categoria. Além disso, este tópico descreve como combinar várias instruções em uma única linha e como continuar uma instrução em várias linhas.

## <a name="declaration-statements"></a>Instruções de declaração

Você usa declarações para nomear e definir procedimentos, variáveis, propriedades, matrizes e constantes. Quando você declara um elemento de programação, você também pode definir seu tipo de dados, nível de acesso e escopo. Para obter mais informações, consulte [Características do elemento declarado](./declared-elements/declared-element-characteristics.md).

O exemplo a seguir contém três declarações.

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

A primeira declaração é a `Sub` declaração. Juntamente com `End Sub` sua declaração correspondente, `applyFormat`declara um procedimento chamado . Ele também especifica `applyFormat` `Public`que é , o que significa que qualquer código que pode se referir a ele pode chamá-lo.

A segunda declaração é a `Const` declaração, que declara a constante, `limit`especificando o `Integer` tipo de dados e um valor de 33.

A terceira declaração é a `Dim` declaração, que declara a variável `thisWidget`. O tipo de dados é um objeto específico, ou seja, um objeto criado a partir da `Widget` classe. Você pode declarar uma variável como sendo de qualquer tipo de dados elementares ou de qualquer tipo de objeto que esteja exposto no aplicativo que você está usando.

### <a name="initial-values"></a>Valores Iniciais

Quando o código que contém uma declaração é executado, o Visual Basic reserva a memória necessária para o elemento declarado. Se o elemento tiver um valor, o Visual Basic o inicializa para o valor padrão de seu tipo de dados. Para obter mais informações, consulte "Comportamento" na [Declaração Dim](../../language-reference/statements/dim-statement.md).

Você pode atribuir um valor inicial a uma variável como parte de sua declaração, como ilustra o exemplo a seguir.

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

Se uma variável for uma variável de objeto, você pode criar explicitamente uma instância de sua classe ao declará-la usando a palavra-chave [Novo Operador,](../../../visual-basic/language-reference/operators/new-operator.md) como ilustra o exemplo a seguir.

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

Observe que o valor inicial especificado em uma declaração não é atribuído a uma variável até que a execução atinja sua declaração de declaração. Até então, a variável contém o valor padrão para seu tipo de dados.

## <a name="executable-statements"></a>Declarações executáveis

Uma declaração executável realiza uma ação. Ele pode chamar um procedimento, ramificar-se para outro lugar no código, loop através de várias declarações, ou avaliar uma expressão. Uma declaração de atribuição é um caso especial de uma declaração executável.

O exemplo a `If...Then...Else` seguir usa uma estrutura de controle para executar diferentes blocos de código com base no valor de uma variável. Dentro de cada bloco `For...Next` de código, um loop executa um número especificado de vezes.

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

A `If` declaração no exemplo anterior verifica `clockwise`o valor do parâmetro . Se o `True`valor for, `spinClockwise` ele `aWidget`chama o método de . Se o `False`valor for, `spinCounterClockwise` ele `aWidget`chama o método de . A `If...Then...Else` estrutura de `End If`controle termina com .

O `For...Next` loop dentro de cada bloco chama o método apropriado `revolutions` de um número de vezes igual ao valor do parâmetro.

## <a name="assignment-statements"></a>Declarações de atribuição

As demonstrações de atribuição realizam operações de atribuição, que`=`consistem em pegar o valor do lado direito do operador de atribuição ( ) e armazená-lo no elemento à esquerda, como no exemplo a seguir.

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

No exemplo anterior, a declaração de cessão `v`armazena o valor literal 42 na variável .

### <a name="eligible-programming-elements"></a>Elementos de programação elegíveis

O elemento de programação no lado esquerdo do operador de atribuição deve ser capaz de aceitar e armazenar um valor. Isso significa que deve ser uma variável ou propriedade que não seja [ReadOnly,](../../../visual-basic/language-reference/modifiers/readonly.md)ou deve ser um elemento de matriz. No contexto de uma declaração de atribuição, tal elemento às vezes é chamado *de valor lvalue*, por "valor esquerdo".

O valor no lado direito do operador de atribuição é gerado por uma expressão, que pode consistir em qualquer combinação de literais, constantes, variáveis, propriedades, elementos de matriz, outras expressões ou chamadas de função. O exemplo a seguir ilustra isto.

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

O exemplo anterior adiciona o `y` valor mantido em `z`variável ao valor mantido na variável `findResult`e, em seguida, adiciona o valor retornado pela chamada à função . O valor total desta expressão é `x`então armazenado em variável .

### <a name="data-types-in-assignment-statements"></a>Tipos de dados em demonstrações de atribuição

Além dos valores numéricos, o `String` operador de atribuição também pode atribuir valores, como ilustra o exemplo a seguir.

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

Você também pode `Boolean` atribuir valores, usando uma `Boolean` expressão literal ou literal, `Boolean` como ilustra o exemplo a seguir.

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

Da mesma forma, você pode atribuir valores `Char` `Date`apropriados `Object` a elementos de programação do , ou tipo de dados. Você também pode atribuir uma instância de objeto a um elemento declarado como sendo da classe a partir da qual essa instância é criada.

### <a name="compound-assignment-statements"></a>Declarações de atribuição composta

*As instruções de atribuição composta* primeiro executam uma operação em uma expressão antes de atribuí-la a um elemento de programação. O exemplo a seguir ilustra um `+=`desses operadores, que incrementa o valor da variável no lado esquerdo do operador pelo valor da expressão à direita.

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

O exemplo anterior adiciona 1 `n`ao valor de , `n`e, em seguida, armazena esse novo valor em . É um equivalente abreviado da seguinte declaração:

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

Uma variedade de operações de atribuição composta pode ser realizada usando operadores deste tipo. Para obter uma lista desses operadores e mais informações sobre eles, consulte [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md).

O operador de atribuição de concatenação (`&=`) é útil para adicionar uma string ao fim das strings já existentes, como ilustra o exemplo a seguir.

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>Conversões de tipo em declarações de atribuição

O valor atribuído a uma variável, propriedade ou elemento de matriz deve ser de um tipo de dados apropriado para esse elemento de destino. Em geral, você deve tentar gerar um valor do mesmo tipo de dados que o do elemento de destino. No entanto, alguns tipos podem ser convertidos para outros tipos durante a atribuição.

Para obter informações sobre a conversão entre os tipos de dados, consulte [Conversões de tipo no Visual Basic](./data-types/type-conversions.md). Em resumo, o Visual Basic converte automaticamente um valor de um determinado tipo para qualquer outro tipo ao qual ele se expande. Uma *conversão de ampliação* é aquela em que sempre tem sucesso no tempo de execução e não perde nenhum dado. Por exemplo, o Visual `Integer` Basic `Double` converte `Integer` um valor `Double`para quando apropriado, porque se expande para . Para obter mais informações, consulte [Ampliando e restringindo conversões](./data-types/widening-and-narrowing-conversions.md).

*O estreitamento das conversões* (aquelas que não estão aumentando) tem o risco de falha no tempo de execução ou de perda de dados. Você pode executar uma conversão de estreitamento explicitamente usando uma função de conversão de tipo, ou `Option Strict Off`você pode direcionar o compilador para executar todas as conversões implicitamente por configuração . Para obter mais informações, consulte [Conversões Implícitas e Explícitas](./data-types/implicit-and-explicit-conversions.md).

## <a name="putting-multiple-statements-on-one-line"></a>Colocando várias declarações em uma linha

Você pode ter várias instruções em uma`:`única linha separadapelo caractere colon ( ) O exemplo a seguir ilustra isto.

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

Embora ocasionalmente conveniente, esta forma de sintaxe torna seu código difícil de ler e manter. Assim, recomenda-se que você mantenha uma declaração em uma linha.

## <a name="continuing-a-statement-over-multiple-lines"></a>Continuando uma declaração sobre várias linhas

Uma declaração geralmente se encaixa em uma linha, mas quando é muito longa, você pode continuar na próxima linha usando uma`_`seqüência de continuação de linha, que consiste em um espaço seguido por um personagem sublinhado ( ) seguido por um retorno de carruagem. No exemplo a `MsgBox` seguir, a declaração executável é continuada em duas linhas.

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>Continuação da linha implícita

Em muitos casos, você pode continuar uma declaração na`_`próxima linha consecutiva sem usar o caractere sublinhado ( ). Os seguintes elementos de sintaxe continuam implicitamente a declaração na próxima linha de código.

- Depois de uma`,`comma ( ). Por exemplo: 

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- Depois de um parêntese aberto (`(`) ou`)`antes de um parêntese de fechamento ( ). Por exemplo: 

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- Depois de uma cinta`{`encaracolada aberta (`}`) ou antes de fechar a cinta encaracolada (). Por exemplo: 

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    Para obter mais informações, consulte [Iniciadores de objeto: Tipos nomeados e anônimos](./objects-and-classes/object-initializers-named-and-anonymous-types.md) ou [iniciadores de coleção](./collection-initializers/index.md).

- Depois de uma`<%=`expressão embutida aberta ( )`%>`ou antes do fechamento de uma expressão incorporada ( ) dentro de um XML literal. Por exemplo: 

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   Para obter mais informações, consulte [Expressões incorporadas em XML](./xml/embedded-expressions-in-xml.md).

- Após o operador de`&`concatenação ( ). Por exemplo: 

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   Para obter mais informações, consulte [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Após operadores`=`de `&=` `:=`atribuição ( `\=`, `^=` `<<=`, `>>=`, `+=`, `-=`, `*=`, `/=`, , , , . Por exemplo: 

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Para obter mais informações, consulte [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Depois de operadores`+` `-`binários `Mod` `<>`( `<` `>`, `<=` `>=`, `^` `/` `*`, `<<` `And`, `AndAlso`, , , , , , , , `>>`, , , `Or`, `OrElse`, `Like`) `Xor`dentro de uma expressão. Por exemplo: 

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   Para obter mais informações, consulte [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Depois `Is` dos `IsNot` operadores. Por exemplo: 

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   Para obter mais informações, consulte [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Após um personagem`.`qualificador de membro ( ) e antes do nome do membro. Por exemplo: 

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   No entanto, você deve incluir`_`um caractere de continuação de `With` linha ( ) seguindo um caractere qualificador de membro quando você estiver usando a declaração ou fornecendo valores na lista de inicialização para um tipo. Considere quebrar a linha após o `=`operador de atribuição (por exemplo) quando estiver usando `With` instruções ou listas de inicialização de objetos. Por exemplo: 

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   Para obter mais informações, consulte [Com... Fim com iniciadores de declaração](../../../visual-basic/language-reference/statements/with-end-with-statement.md) ou [objeto: tipos nomeados e anônimos](./objects-and-classes/object-initializers-named-and-anonymous-types.md).

- Após um qualificador de`.` `.@` propriedade `...`do eixo XML (ou ). No entanto, você deve incluir`_`um caractere de continuação de `With` linha ( ) quando você especificar um qualificador de membro quando estiver usando a palavra-chave. Por exemplo: 

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   Para obter mais informações, consulte [Propriedades do Eixo XML](../../../visual-basic/language-reference/xml-axis/index.md).

- Depois de um sinal menor que (<) ou`>`antes de um sinal maior do que () quando você especificar um atributo. Também depois de um`>`sinal maior do que () quando você especifica rumide a um atributo. No entanto, você deve incluir`_`um caractere de continuação de linha ( ) quando você especificar atributos de nível de montagem ou nível de módulo. Por exemplo: 

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   Para obter mais informações, consulte [Atributos visão geral](../../../visual-basic/programming-guide/concepts/attributes/index.md).

- Antes e depois dos`Aggregate`operadores de consulta ( `Skip`, `Skip While` `Take`, `Take While` `Where` `In` `Into` `On` `Ascending` `Descending` `Distinct` `From` `Group By`, `Group Join`, , `Join`, `Let` `Order By`, , `Select`, , , , , , , , e ). Você não pode quebrar uma linha entre as palavras-chave dos operadores `Take While`de `Skip While`consulta que são compostas de múltiplas palavras-chave (`Order By`, `Group Join`, e ). Por exemplo: 

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   Para obter mais informações, consulte [Consultas](../../../visual-basic/language-reference/queries/index.md).

- Depois `In` da palavra-chave em uma `For Each` declaração. Por exemplo: 

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   Para obter mais informações, consulte [Para Cada... Próxima Declaração](../../../visual-basic/language-reference/statements/for-each-next-statement.md).

- Depois `From` da palavra-chave em um inicializador de coleção. Por exemplo: 

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   Para obter mais informações, consulte [Inicializadores de coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

## <a name="adding-comments"></a>Adicionando comentários

O código fonte nem sempre é auto-explicativo, mesmo para o programador que o escreveu. Para ajudar a documentar seu código, portanto, a maioria dos programadores faz uso liberal de comentários incorporados. Comentários em código podem explicar um procedimento ou uma instrução específica para quem lê ou trabalha com ele mais tarde. O Visual Basic ignora comentários durante a compilação e eles não afetam o código compilado.

As linhas de comentários começam`'`com `REM` um apóstrofo () ou seguidas por um espaço. Eles podem ser adicionados em qualquer lugar do código, exceto dentro de uma seqüência. Para anexar um comentário a uma declaração, `REM` insira um apóstrofo ou após a declaração, seguido do comentário. Os comentários também podem ir em sua própria linha separada. O exemplo a seguir demonstra essas possibilidades.

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>Verificando erros de compilação

Se, depois de digitar uma linha de código, a linha for exibida com um sublinhado azul ondulado (uma mensagem de erro também pode aparecer), há um erro de sintaxe na declaração. Você deve descobrir o que está errado com a declaração (olhando na lista de tarefas ou pairando sobre o erro com o ponteiro do mouse e lendo a mensagem de erro) e corrigi-la. Até que você tenha corrigido todos os erros de sintaxe em seu código, seu programa falhará em compilar corretamente.

## <a name="related-sections"></a>Seções relacionadas

|Termo|Definição|
|---|---|
|[Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)|Fornece links para páginas de referência `=`de `*=`idioma `&=`que abrangem operadores de atribuição, tais como , e .|
|[Operadores e Expressões](./operators-and-expressions/index.md)|Mostra como combinar elementos com operadores para produzir novos valores.|
|[Como quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Mostra como quebrar uma única instrução em várias linhas e como colocar várias instruções na mesma linha.|
|[Como rotular instruções](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Mostra como rotular uma linha de código.|
