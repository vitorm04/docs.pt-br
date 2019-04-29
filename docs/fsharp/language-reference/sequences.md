---
title: Sequências
description: Saiba como usar F# sequências, quando você tem uma grande coleção ordenada de dados, mas não necessariamente pretende usar todos os elementos.
ms.date: 02/19/2019
ms.openlocfilehash: a7791be5e8bd07d81fe9e890fc5896b181f0cb39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770468"
---
# <a name="sequences"></a>Sequências

> [!NOTE]
> Os links de referência da API neste artigo levarão você até o MSDN.  A referência da API docs.microsoft.com não está completa.

Um *sequência* é uma série de lógica de elementos todos de um tipo. As sequências são particularmente úteis quando você tiver uma grande coleção ordenada de dados, mas não necessariamente espera usar todos os elementos. Sequência individual elementos são computados apenas como necessário, para que uma sequência pode fornecer desempenho melhor do que uma lista em situações em que nem todos os elementos são usados. As sequências são representadas pela `seq<'T>` tipo, que é um alias para `System.Collections.Generic.IEnumerable`. Portanto, qualquer tipo .NET Framework que implementa `System.IEnumerable` pode ser usado como uma sequência. O [módulo Seq](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) fornece suporte para as manipulações que envolvem sequências.

## <a name="sequence-expressions"></a>Expressões de sequência

Um *expressão de sequência* é uma expressão que é avaliada como uma sequência. Expressões de sequência podem conter um número de formulários. A forma mais simples Especifica um intervalo. Por exemplo, `seq { 1 .. 5 }` cria uma sequência que contém cinco elementos, incluindo os pontos de extremidade 1 e 5. Você pode também especificar um incremento (ou decrementar) entre dois períodos de double. Por exemplo, o código a seguir cria a sequência de múltiplos de 10.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

Expressões de sequência são compostas de F# expressões que produzem valores da sequência. Eles podem usar o `yield` palavra-chave para produzir valores se tornam parte da sequência.

A seguir está um exemplo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

Você pode usar o `->` em vez do operador `yield`, caso em que você pode omitir o `do` palavra-chave, conforme mostrado no exemplo a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

O código a seguir gera uma lista de pares de coordenadas, juntamente com um índice em uma matriz que representa a grade.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

Um `if` expressão usada em uma sequência é um filtro. Por exemplo, para gerar uma sequência de apenas números primos, supondo que você tenha uma função `isprime` do tipo `int -> bool`, construir a sequência da seguinte maneira.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

Quando você usa `yield` ou `->` em uma iteração, cada iteração é esperada para gerar um único elemento da sequência. Se cada iteração produz uma sequência de elementos, use `yield!`. Nesse caso, os elementos gerados em cada iteração são concatenados para produzir a sequência final.

Você pode combinar várias expressões juntos em uma expressão de sequência. Os elementos gerados por cada expressão são concatenados. Para obter um exemplo, consulte a seção "Exemplos" deste tópico.

## <a name="examples"></a>Exemplos

O primeiro exemplo usa uma expressão de sequência que contém uma iteração, um filtro e um yield para gerar uma matriz. Esse código imprime uma sequência de números primos entre 1 e 100 para o console.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

O seguinte código usa `yield` para criar uma tabela de multiplicação que consiste em tuplas de três elementos, cada uma consistindo em dois fatores e o produto.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

O exemplo a seguir demonstra o uso de `yield!` combinar sequências individuais em uma única sequência final. Nesse caso, as sequências para cada subárvore em uma árvore binária são concatenadas em uma função recursiva para produzir a sequência final.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a>Uso de sequências

Sequências dão suporte a muitas das mesmas funções como [lista](lists.md). Sequências também dão suporte a operações como agrupamento e contagem por meio de funções de geração de chave. Sequências também dão suporte a funções mais diversificadas para extração de subsequências.

Muitos tipos de dados, como listas, matrizes, conjuntos e mapas são implicitamente sequências porque elas são coleções enumeráveis. Uma função que usa uma sequência como um argumento funciona com qualquer um dos comuns F# tipos de dados, além de qualquer tipo de dados do .NET Framework que implementa `System.Collections.Generic.IEnumerable<'T>`. Compare isso para uma função que usa uma lista como um argumento, o que pode levar apenas listas. O tipo `seq<'T>` é uma abreviação de tipo de `IEnumerable<'T>`. Isso significa que qualquer tipo que implementa o genérico `System.Collections.Generic.IEnumerable<'T>`, que inclui matrizes, listas, define e mapas em F#e também a maioria dos tipos do .NET Framework coleção, é compatível com o `seq` de tipo e pode ser usado sempre que uma sequência é esperada .

## <a name="module-functions"></a>Funções do módulo

O [módulo Seq](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) na [FSharp namespace](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) contém funções para trabalhar com sequências. Essas funções funcionam com listas, matrizes, mapas e conjuntos, bem, porque todos esses tipos são enumerable e, portanto, podem ser tratados como sequências.

## <a name="creating-sequences"></a>Criação de sequências

Você pode criar sequências usando expressões de sequência, conforme descrito anteriormente, ou usando determinadas funções.

Você pode criar uma sequência vazia, usando [SEQ. Empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), ou você pode criar uma sequência de apenas um elemento especificado usando [SEQ. singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

Você pode usar [SEQ. init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) para criar uma sequência para o qual os elementos são criados usando uma função que você fornecer. Você também pode fornecer um tamanho para a sequência. Essa função é como [List. init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), exceto que os elementos não são criados até que você itere pela sequência. O código a seguir ilustra o uso de `Seq.init`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

A saída é

```
0 10 20 30 40
```

Usando [SEQ. ofarray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) e [SEQ. oflist&#60;|&#62; função](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), você pode criar sequências de matrizes e listas. No entanto, você também pode converter matrizes e listas para sequências usando um operador cast. Ambas as técnicas são mostradas no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

Usando [SEQ. cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), você pode criar uma sequência de uma coleção sem rigidez de tipos, como aquelas definidas em `System.Collections`. Essas coleções sem rigidez de tipos têm o tipo de elemento `System.Object` e são enumeradas usando não genérica `System.Collections.Generic.IEnumerable&#96;1` tipo. O código a seguir ilustra o uso de `Seq.cast` para converter um `System.Collections.ArrayList` em uma sequência.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

Você pode definir infinitas sequências usando o [SEQ. initinfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) função. Para a sequência, você deve fornecer uma função que gera cada elemento do índice do elemento. Sequências de infinitas são possíveis devido a avaliação lenta; elementos são criados conforme necessário, chamando a função que você especificar. O exemplo de código a seguir produz uma sequência infinita de flutuante números de ponto, neste caso, a série alternada de recíprocos dos quadrados de inteiros sucessivos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

[Função SEQ. unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) gera uma sequência de uma função de computação que leva a um estado e os transforma para produzir cada elemento subsequente na sequência. O estado é apenas um valor que é usado para calcular cada elemento e pode alterar conforme cada elemento é calculado. O segundo argumento para `Seq.unfold` é o valor inicial que é usado para iniciar a sequência. `Seq.unfold` usa um tipo de opção para o estado, o que permite que você encerrar a sequência, retornando o `None` valor. O código a seguir mostra dois exemplos de sequências `seq1` e `fib`, que são gerados por um `unfold` operação. A primeira, `seq1`, é apenas uma sequência simple com números de até 20. A segunda `fib`, usa `unfold` para calcular a sequência de Fibonacci. Como cada elemento na sequência de Fibonacci é a soma dos dois números Fibonacci anteriores, o valor de estado é uma tupla que consiste em dois números anteriores na sequência. O valor inicial é `(1,1)`, os primeiros dois números na sequência.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

A saída é a seguinte:

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

O código a seguir é um exemplo que usa muitas das funções do módulo sequência descritas aqui para gerar e os valores de sequências infinitas de computação. O código pode levar alguns minutos para ser executado.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a>Pesquisar e localizar elementos

Sequências de dar suporte a funcionalidade disponível com listas: [SEQ. Exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [SEQ. Find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [SEQ. FindIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [SEQ. Pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [SEQ. tryfind ](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), e [SEQ. tryfindindex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a). As versões dessas funções que estão disponíveis para sequências de avaliam a sequência apenas até o elemento que está sendo pesquisado. Para obter exemplos, consulte [lista](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).

## <a name="obtaining-subsequences"></a>Obtenção de subsequências

[SEQ. Filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) e [SEQ. Choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) são como as funções correspondentes que estão disponíveis para as listas, exceto que a filtragem e escolher não ocorrerá até que os elementos de sequência são avaliados.

[SEQ. Truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) cria uma sequência de outra sequência, mas limita a sequência de um número especificado de elementos. [SEQ. Take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) cria uma nova sequência que contém apenas um número especificado de elementos desde o início de uma sequência. Se houver menos elementos na sequência que você especificar para tirar, `Seq.take` lança um `System.InvalidOperationException`. A diferença entre `Seq.take` e `Seq.truncate` é que `Seq.truncate` não produz um erro se o número de elementos é menos do que o número especificado.

O código a seguir mostra o comportamento de e as diferenças entre `Seq.truncate` e `Seq.take`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

A saída antes do erro ocorrer, é da seguinte maneira.

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

Usando [SEQ. TakeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), você pode especificar uma função de predicado (uma função booleana) e criar uma sequência de outra sequência composta por esses elementos da sequência original para o qual o predicado é `true`, mas parar antes do primeiro elemento para o qual o predicado retornar `false`. [SEQ. Skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) retorna uma sequência que ignora um número especificado de primeiros elementos de outra sequência e retorna os elementos restantes. [SEQ. SkipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) retorna uma sequência que ignora os primeiros elementos de outra sequência, desde que o predicado retornar `true`e, em seguida, retorna os elementos restantes, começando com o primeiro elemento para o qual o predicado retornar `false`.

O exemplo de código a seguir ilustra o comportamento de e as diferenças entre `Seq.takeWhile`, `Seq.skip`, e `Seq.skipWhile`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

A saída é a seguinte.

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Transformação de sequências

[Função SEQ. Pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) cria uma nova sequência na qual sucessivos elementos da sequência de entrada são agrupados em tuplas.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

[Função SEQ. windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) é como `Seq.pairwise`, exceto que, em vez de produzir uma sequência de tuplas, ele produz uma sequência de matrizes que contêm cópias dos elementos adjacentes (um *janela*) da sequência. Você pode especificar o número de elementos adjacentes que você deseja em cada matriz.

O exemplo de código a seguir demonstra o uso de `Seq.windowed`. Nesse caso, o número de elementos na janela é 3. O exemplo usa `printSeq`, que é definido no exemplo de código anterior.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet180.fs)]

A saída é a seguinte.

Sequência inicial:

```
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>Operações com várias sequências

[SEQ. zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) e [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) usam dois ou três sequências e produzem uma sequência de tuplas. Essas funções são como as funções correspondentes disponíveis para [lista](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d). Não há nenhuma funcionalidade correspondente para separar uma sequência em duas ou mais sequências. Se você precisar dessa funcionalidade para uma sequência, converter a sequência em uma lista e use [List. Unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

## <a name="sorting-comparing-and-grouping"></a>Classificação, comparação e agrupamento

Funções de classificação com suporte para listas também funcionam com sequências. Isso inclui [SEQ. Sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) e [SEQ. SortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f). Essas funções percorrer toda a sequência.

Comparar duas sequências usando o [SEQ. comparewith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) função. A função compara sucessivos elementos por sua vez e é interrompido quando encontra o primeiro par desigual. Todos os elementos adicionais não contribuem para a comparação.

O código a seguir demonstra o uso de `Seq.compareWith`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

No código anterior, apenas o primeiro elemento é calculado e examinado, e o resultado é -1.

[Função SEQ. CountBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) usa uma função que gera um valor chamado um *chave* para cada elemento. Uma chave é gerada para cada elemento, chamando essa função em cada elemento. `Seq.countBy` em seguida, retorna uma sequência que contém os valores de chave e uma contagem do número de elementos que gerou cada valor da chave.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

A saída é a seguinte.

```
(1, 34) (2, 33) (0, 33)
```

A saída anterior mostra que havia 34 elementos da sequência original que gerou a chave 1, 33 valores que produziu a chave 2 e valores de 33 que produziu a tecla 0.

Você pode agrupar os elementos de uma sequência chamando [SEQ. GroupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd). `Seq.groupBy` usa uma sequência e uma função que gera uma chave de um elemento. A função é executada em cada elemento da sequência. `Seq.groupBy` Retorna uma sequência de tuplas, onde o primeiro elemento de cada tupla é a chave e o segundo é uma sequência de elementos que produzem essa chave.

O exemplo de código a seguir mostra o uso de `Seq.groupBy` para particionar a sequência de números de 1 a 100 em três grupos que têm valores de chave distintos 0, 1 e 2.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

A saída é a seguinte.

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

Você pode criar uma sequência que elimina elementos duplicados, chamando [SEQ. DISTINCT](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401). Ou você pode usar [SEQ. distinctby](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), que usa uma função de geração de chave a ser chamado em cada elemento. A sequência resultante contém elementos da sequência original que têm chaves exclusivas; os elementos posteriores que produzem uma chave duplicada para um elemento anterior são descartados.

O exemplo de código a seguir ilustra o uso de `Seq.distinct`. `Seq.distinct` é demonstrado pelo gerar sequências que representam números binários e, em seguida, mostrando que os elementos de apenas distintos são 0 e 1.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

O código a seguir demonstra `Seq.distinctBy` iniciando com uma sequência que contém números positivos e negativos e usando a função de valor absoluto da função de geração de chave. A sequência resultante não tem todos os números positivos que correspondem aos números negativos na sequência, porque os números negativos aparecem anteriormente na sequência e, portanto, são selecionados, em vez de números positivos que têm o mesmo absoluto valor ou chave.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>Sequências em cache e somente leitura

[SEQ. ReadOnly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) cria uma cópia somente leitura de uma sequência. `Seq.readonly` é útil quando você tem uma coleção de leitura / gravação, como uma matriz, e você não deseja modificar a coleção original. Essa função pode ser usada para preservar o encapsulamento de dados. No exemplo de código a seguir, um tipo que contém uma matriz é criado. Uma propriedade expõe a matriz, mas em vez de retornar uma matriz, ele retorna uma sequência que é criada a partir da matriz usando `Seq.readonly`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

[SEQ. cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) cria uma versão armazenada de uma sequência. Use `Seq.cache` para evitar a reavaliação de uma sequência ou quando você tem vários threads que usam uma sequência, mas certifique-se de que cada elemento é tratado apenas uma vez. Quando você tiver uma sequência que está sendo usada por vários threads, você pode ter um thread que enumera e calcula os valores de sequência original e threads restantes podem usar a sequência armazenada em cache.

## <a name="performing-computations-on-sequences"></a>Executar cálculos em sequências

Operações aritméticas simples serão semelhantes às de listas, tais como [SEQ. Average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [SEQ. Sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [SEQ. averageby](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [SEQ. sumby](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)e assim por diante.

[Função SEQ. Fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [SEQ. reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), e [SEQ. Scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) são como as funções correspondentes que estão disponíveis para listas. Sequências de dar suporte a um subconjunto das variações completos dessas funções que lista o suporte. Para obter mais informações e exemplos, consulte [lista](lists.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Tipos F#](fsharp-types.md)
