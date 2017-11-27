---
title: "Diretrizes de formatação de código (F#)"
description: "Saiba mais diretrizes de formatação de recuo de código para o F # linguagem para legibilidade, a estética, a padronização e a compilação de programação."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3f79717c-f84e-448d-9ce4-90e40a644ba1
ms.openlocfilehash: cc56c67f356b99defd8dc28770f87be1f58443c5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="code-formatting-guidelines"></a>Diretrizes de formatação de código

Este tópico resume as diretrizes de código de recuo para F #. Como a linguagem F # é sensível a quebras de linha e recuo, não é apenas uma questão de legibilidade, problema estético ou problema de padronização de codificação para formatar o código corretamente. Você deve formatar seu código corretamente compilar corretamente.


## <a name="general-rules-for-indentation"></a>Regras gerais para de recuo
Quando o recuo for necessário, você deve usar espaços, tabulações não. É necessário pelo menos um espaço. Sua organização pode criar padrões de codificação para especificar o número de espaços a serem usados para recuo; três ou quatro espaços de recuo em cada nível onde ocorre o recuo é comum. Você pode configurar o Visual Studio para corresponder aos padrões de recuo de sua organização, alterando as opções de `Options` caixa de diálogo, que está disponível na `Tools` menu. No `Text Editor` nó, expanda `F#` e, em seguida, clique em `Tabs`. Para obter uma descrição das opções disponíveis, consulte [opções, Editor de texto, todos os idiomas, guias](https://msdn.microsoft.com/library/7sffa753.aspx).

Em geral, quando o compilador analisa seu código, ele mantém uma pilha interna que indica o nível de aninhamento atual. Quando o conteúdo é recuado, um novo nível de aninhamento é criado ou enviada por push para esta pilha interna. Quando uma construção termina, o nível é exibido. Recuo é uma maneira para sinalizar o final de um nível e exibir a pilha interna, mas determinados símbolos também fazer com que o nível deve ser exibido, como o `end` palavra-chave, ou uma chave de fechamento ou parênteses.

Definição de função de código em uma construção de várias linhas, como uma definição de tipo `try...with` construção e construções de loop devem ser recuados em relação a linha de abertura da construção. A primeira linha recuada estabelece uma posição de coluna para código subsequente na construção da mesma. O nível de recuo é chamado um *contexto*. A posição da coluna define uma coluna mínimo, conhecida como um *linha fora*, para subsequentes linhas de código que estão no mesmo contexto. Quando uma linha de código é encontrada é recuado menor que a posição de coluna estabelecida, o compilador assumirá que o contexto foi concluída e que você está agora codificando do próximo nível, o contexto anterior. O termo *fora* é usado para descrever a condição em que uma linha de código dispara o final de uma construção porque ele não é recuado distante o suficiente. Em outras palavras, o código para a esquerda de uma linha fora está fora. No código recuado corretamente, você pode tirar proveito da regra de fora para delinear final das construções. Se você usar o recuo incorretamente, uma condição fora pode fazer com que o compilador emite um aviso ou pode levar à interpretação incorreta do seu código.

Linhas fora são determinadas da seguinte maneira.


- Um `=` token associado a um `let` apresenta uma linha fora a coluna do primeiro token após o `=` sinal.


- Em um `if...then...else` expressão, a posição da coluna do primeiro token após o `then` palavra-chave ou o `else` palavra-chave introduz uma linha fora.


- Em um `try...with` expressão, o primeiro token após `try` apresenta uma linha fora.


- Em um `match` expressão, o primeiro token após `with` e o primeiro token após cada `->` introduzir linhas fora.


- O primeiro token após `with` em um tipo de extensão apresenta uma linha fora.


- O primeiro token após uma chave de abertura ou parênteses, ou após o `begin` palavra-chave, apresenta uma linha fora.


- O primeiro caractere em palavras-chave `let`, `if`, e `module` introduzir linhas fora.


Os exemplos de código a seguir ilustram as regras de recuo. Aqui, as instruções de impressão dependem de recuo para associá-los com o contexto apropriado. Toda vez que o recuo deslocado, o contexto é exibido e retorna para o contexto anterior. Portanto, um espaço é impressa no final de cada iteração; "Concluído"! só é impressa uma vez porque o recuo fora estabelece que não é parte do loop. A impressão de cadeia de caracteres "Contexto de nível superior" não faz parte da função. Portanto, ele é impresso pela primeira vez, durante a inicialização estática, antes da função é chamada.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet1.fs)]

A saída é a seguinte.

```
Top-level context

(Negative number) Zero 1 2 3 Done!
```

Quando você quebrar linhas longas, a continuação da linha deve recuada além da construção de delimitador. Por exemplo, argumentos de função devem ser recuados além do primeiro caractere do nome da função, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet2.fs)]

Há exceções a essas regras, conforme descrito na próxima seção.


## <a name="indentation-in-modules"></a>Recuo em módulos
Em um módulo local deverá ser recuado em relação ao módulo, mas o código em um módulo de nível superior não precisa ser recuado. Elementos de Namespace não precisam ser recuado.

Os exemplos de código a seguir ilustram isso.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet3.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet4.fs)]

Para obter mais informações, consulte [módulos](modules.md).


## <a name="exceptions-to-the-basic-indentation-rules"></a>Exceções às regras básicas de recuo
A regra geral, conforme descrito na seção anterior, é que as construções de várias linhas devem ser recuado em relação ao recuo da primeira linha da construção e que o fim da construção é determinado pelo quando ocorre a primeira linha de fora. Uma exceção à regra sobre quando a fim de contextos é que algumas construções, como o `try...with` expressão, o `if...then...else` expressão e o uso de `and` sintaxe para declarar mutuamente funções recursivas ou tipos, tem várias partes. Recuar as últimas partes, como `then` e `else` em um `if...then...else` expressão, no mesmo nível como o token que inicia a expressão, mas em vez de indicar um final para o contexto, ele representa a próxima parte do mesmo contexto. Portanto, um `if...then...else` expressão pode ser gravada como no exemplo de código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet5.fs)]

A exceção à regra fora se aplicam somente ao `then` e `else` palavras-chave. Portanto, embora não seja um erro para recuar o `then` e `else` Além disso, com falha recuar as linhas de código em um `then` bloco produz um aviso. Isso é ilustrado em linhas de código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet6.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet7.fs)]

Para o código em um `else` bloco, uma regra especial adicional se aplica. O aviso no exemplo anterior somente ocorre no código no `then` blocos, não no código no `else` bloco. Isso permite que você escreva código que verifica se há várias condições no início de uma função sem forçar o restante do código para a função, que pode estar em um `else` bloco a ser recuado. Assim, você pode escrever o seguinte sem gerar um aviso.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet8.fs)]

Outra exceção à regra de contextos terminam quando uma linha não ficará recuada quanto uma linha anterior é infixo operadores, como `+` e `|>`. Linhas que começam com operadores fixos são permitidas para começar a `(1 + oplength)` colunas antes que a posição normal sem disparar um final para o contexto onde `oplength` é o número de caracteres que compõem o operador. Isso faz com que o primeiro token depois do operador para alinhar com a linha anterior.

Por exemplo, no código a seguir, o `+` símbolo tem permissão para ser recuadas duas colunas menor do que a linha anterior.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet9.fs)]

Embora o recuo geralmente aumenta à medida que o nível de aninhamento se torna maior, há várias construções em que o compilador permite que você redefina o recuo para uma posição inferior da coluna.

As construções que permitem uma redefinição da posição de coluna são os seguintes:


- Corpos de funções anônimas. No código a seguir, a expressão de impressão é iniciado em uma posição de coluna mais à esquerda que o `fun` palavra-chave. No entanto, a linha não deve começar em uma coluna à esquerda do início do nível de recuo anterior (ou seja, à esquerda do `L` em `List`).
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet10.fs)]

- Construções entre parênteses ou por `begin` e `end` em uma `then` ou `else` block de um `if...then...else` expressão, fornecido o recuo é não menos do que a posição de coluna a `if` palavra-chave. Essa exceção permite que um estilo de codificação no qual um parêntese de abertura ou `begin` é usado no final de uma linha após `then` ou `else`.


- Corpos de módulos, classes, interfaces e estruturas delimitadas por `begin...end`, `{...}`, `class...end`, ou `interface...end`. Isso permite que um estilo no qual a palavra-chave de abertura de uma definição de tipo pode ser na mesma linha como o nome do tipo sem fazer com que todo o corpo a ser recuado além da palavra-chave de abertura.
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet13.fs)]


## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)
