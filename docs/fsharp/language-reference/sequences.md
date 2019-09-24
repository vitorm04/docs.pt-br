---
title: Sequências
description: Saiba como usar F# sequências, quando você tem uma coleção de dados grande e ordenada, mas não espera necessariamente usar todos os elementos.
ms.date: 02/19/2019
ms.openlocfilehash: 63e878c2c11db25a08d449070ab779a6e6a2c2eb
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216765"
---
# <a name="sequences"></a>Sequências

> [!NOTE]
> Os links de referência da API neste artigo levarão você até o MSDN.  A referência da API docs.microsoft.com não está completa.

Uma *sequência* é uma série lógica de elementos de um tipo. As sequências são particularmente úteis quando você tem uma coleção de dados grande e ordenada, mas não espera necessariamente usar todos os elementos. Os elementos de sequência individuais são calculados somente conforme necessário, portanto, uma sequência pode fornecer um melhor desempenho do que uma lista em situações nas quais nem todos os elementos são usados. As `seq<'T>` sequências são representadas pelo tipo, que é um `System.Collections.Generic.IEnumerable`alias para. Portanto, qualquer tipo de .NET Framework que `System.IEnumerable` implemente possa ser usado como uma sequência. O [módulo Seq](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) fornece suporte para manipulações que envolvem sequências.

## <a name="sequence-expressions"></a>Expressões de sequência

Uma *expressão de sequência* é uma expressão que é avaliada como uma sequência. Expressões de sequência podem usar vários formulários. A forma mais simples especifica um intervalo. Por exemplo, `seq { 1 .. 5 }` cria uma sequência que contém cinco elementos, incluindo os pontos de extremidade 1 e 5. Você também pode especificar um incremento (ou decrementar) entre dois pontos duplos. Por exemplo, o código a seguir cria a sequência de múltiplos de 10.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

Expressões de sequência são constituídas F# de expressões que produzem valores da sequência. Eles podem usar a `yield` palavra-chave para produzir valores que se tornam parte da sequência.

Veja a seguir um exemplo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

Você pode usar o `->` operador em vez `yield`de, caso em que você pode omitir a `do` palavra-chave, conforme mostrado no exemplo a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

O código a seguir gera uma lista de pares de coordenadas junto com um índice em uma matriz que representa a grade.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

Uma `if` expressão usada em uma sequência é um filtro. Por exemplo, para gerar uma sequência de apenas números primos, supondo que você tenha `isprime` uma função `int -> bool`do tipo, construa a sequência da seguinte maneira.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

Quando você usa `yield` ou `->` em uma iteração, espera-se que cada iteração gere um único elemento da sequência. Se cada iteração produzir uma sequência de elementos, `yield!`use. Nesse caso, os elementos gerados em cada iteração são concatenados para produzir a sequência final.

Você pode combinar várias expressões juntas em uma expressão de sequência. Os elementos gerados por cada expressão são concatenados juntos. Para obter um exemplo, consulte a seção "exemplos" deste tópico.

## <a name="examples"></a>Exemplos

O primeiro exemplo usa uma expressão de sequência que contém uma iteração, um filtro e um yield para gerar uma matriz. Esse código imprime uma sequência de números primos entre 1 e 100 no console.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

O código a seguir `yield` usa para criar uma tabela de multiplicação que consiste em tuplas de três elementos, cada um consistindo de dois fatores e do produto.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

O exemplo a seguir demonstra o uso `yield!` de para combinar Sequências individuais em uma única sequência final. Nesse caso, as sequências para cada subárvore em uma árvore binária são concatenadas em uma função recursiva para produzir a sequência final.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a>Usando sequências

As sequências dão suporte a muitas das mesmas funções que as [listas](lists.md). As sequências também dão suporte a operações como agrupamento e contagem usando funções de geração de chaves. As sequências também dão suporte a funções mais diversificadas para extração de subsequências.

Muitos tipos de dados, como listas, matrizes, conjuntos e mapas são implicitamente sequências porque são coleções enumeráveis. Uma função que usa uma sequência como um argumento funciona com qualquer um dos tipos F# de dados comuns, além de qualquer .NET Framework tipo de dados que `System.Collections.Generic.IEnumerable<'T>`implementa. Compare isso com uma função que usa uma lista como um argumento, que só pode receber listas. O tipo `seq<'T>` é uma abreviação de tipo `IEnumerable<'T>`para. Isso significa que qualquer tipo que implementa o genérico `System.Collections.Generic.IEnumerable<'T>`, que inclui matrizes, listas, conjuntos e mapas no F#, e também a maioria .NET Framework tipos de coleção, é compatível `seq` com o tipo e pode ser usado sempre que uma sequência é esperada .

## <a name="module-functions"></a>Funções do módulo

O [módulo Seq](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) no [namespace Microsoft. FSharp. Collections](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) contém funções para trabalhar com sequências. Essas funções funcionam com listas, matrizes, mapas e conjuntos também, porque todos esses tipos são enumeráveis e, portanto, podem ser tratados como sequências.

## <a name="creating-sequences"></a>Criando sequências

Você pode criar sequências usando expressões de sequência, conforme descrito anteriormente, ou usando determinadas funções.

Você pode criar uma sequência vazia usando [Seq. Empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)ou pode criar uma sequência de apenas um elemento especificado usando [Seq. Singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet9.fs)]

Você pode usar [Seq. init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) para criar uma sequência para a qual os elementos são criados usando uma função que você fornece. Você também fornece um tamanho para a sequência. Essa função é exatamente como [list. init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), exceto que os elementos não são criados até que você itere pela sequência. O código a seguir ilustra o uso `Seq.init`de.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet10.fs)]

A saída é

```console
0 10 20 30 40
```

Usando [Seq. ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) e [Seq&#60;. ofList não&#62; funcionam](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), você pode criar sequências de matrizes e listas. No entanto, você também pode converter matrizes e listas em sequências usando um operador cast. As duas técnicas são mostradas no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet11.fs)]

Usando [Seq. Cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), você pode criar uma sequência de uma coleção de tipo fraco, como aquelas definidas em `System.Collections`. Essas coleções tipadas de forma fraca têm o `System.Object` tipo de elemento e são enumeradas usando o tipo `System.Collections.Generic.IEnumerable&#96;1` não genérico. O código a seguir ilustra o uso `Seq.cast` de para converter `System.Collections.ArrayList` um em uma sequência.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet12.fs)]

Você pode definir sequências infinitas usando a função [Seq. initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) . Para tal sequência, você fornece uma função que gera cada elemento do índice do elemento. Sequências infinitas são possíveis devido à avaliação lenta; os elementos são criados conforme necessário chamando a função que você especificar. O exemplo de código a seguir produz uma sequência infinita de números de ponto flutuante, neste caso, a série alternada de recíprocos de quadrados de inteiros sucessivos.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet13.fs)]

[Seq. desdobrar](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) gera uma sequência de uma função de computação que usa um estado e a transforma para produzir cada elemento subsequente na sequência. O estado é apenas um valor que é usado para computar cada elemento e pode ser alterado conforme cada elemento é computado. O segundo argumento para `Seq.unfold` é o valor inicial usado para iniciar a sequência. `Seq.unfold`usa um tipo de opção para o estado, que permite que você finalize a sequência retornando `None` o valor. O código a seguir mostra dois exemplos de `seq1` sequências `fib`e, que são gerados por `unfold` uma operação. A primeira, `seq1`, é apenas uma sequência simples com números de até 20. O segundo, `fib`,, `unfold` usa para calcular a sequência Fibonacci. Como cada elemento na sequência Fibonacci é a soma dos dois números de Fibonacci anteriores, o valor de estado é uma tupla que consiste nos dois números anteriores na sequência. O valor inicial é `(1,1)`, os dois primeiros números na sequência.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet14.fs)]

A saída é a seguinte:

```console
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

O código a seguir é um exemplo que usa muitas das funções de módulo de sequência descritas aqui para gerar e calcular os valores de sequências infinitas. O código pode levar alguns minutos para ser executado.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a>Pesquisando e Localizando elementos

As sequências dão suporte à funcionalidade disponível com listas: [Seq. Exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq. exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq. Find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq. FindIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [Seq. escolha](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq. tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)e [Seq. tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a). As versões dessas funções que estão disponíveis para sequências avaliam a sequência somente até o elemento que está sendo pesquisado. Para obter exemplos, consulte [listas](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).

## <a name="obtaining-subsequences"></a>Obtendo subsequências

[Seq. Filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) e [Seq. Choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) são como as funções correspondentes que estão disponíveis para listas, exceto que a filtragem e a escolha não ocorrem até que os elementos de sequência sejam avaliados.

[Seq. Truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) cria uma sequência de outra sequência, mas limita a sequência a um número especificado de elementos. [Seq. Take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) cria uma nova sequência que contém apenas um número especificado de elementos desde o início de uma sequência. Se houver menos elementos na sequência do que você especificar para executar, `Seq.take` o lançará um. `System.InvalidOperationException` A diferença entre `Seq.take` e `Seq.truncate` é que `Seq.truncate` o não produzirá um erro se o número de elementos for menor que o número especificado.

O código a seguir mostra o comportamento e as diferenças `Seq.truncate` entre `Seq.take`e.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet16.fs)]

A saída, antes da ocorrência do erro, é a seguinte.

```console
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

Usando [Seq. TakeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), você pode especificar uma função de predicado (uma função booleana) e criar uma sequência de outra sequência composta desses elementos da sequência original para a qual o predicado é `true`, mas parar antes do primeiro elemento para o qual o predicado retorna `false`. [Seq. Skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) retorna uma sequência que ignora um número especificado dos primeiros elementos de outra sequência e retorna os elementos restantes. [Seq. SkipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) retorna uma sequência que ignora os primeiros elementos de outra sequência, desde que o predicado `true`retorne e, em seguida, retorne os elementos restantes, começando com o primeiro elemento `false` para o qual o predicado retorna .

O exemplo de código a seguir ilustra o comportamento e as `Seq.takeWhile`diferenças `Seq.skip`entre, `Seq.skipWhile`e.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet17.fs)]

A saída é a seguinte.

```console
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Transformando sequências

[Seq. emparelha](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) cria uma nova sequência na qual os elementos sucessivos da sequência de entrada são agrupados em tuplas.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet18.fs)]

O [Seq. Window](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) é como `Seq.pairwise`, exceto que, em vez de produzir uma sequência de tuplas, ele produz uma sequência de matrizes que contêm cópias de elementos adjacentes (uma *janela*) da sequência. Você especifica o número de elementos adjacentes que deseja em cada matriz.

O exemplo de código a seguir demonstra o uso de `Seq.windowed`. Nesse caso, o número de elementos na janela é 3. O exemplo usa `printSeq`, que é definido no exemplo de código anterior.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet180.fs)]

A saída é a seguinte.

Sequência inicial:

```console
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>Operações com várias sequências

[Seq. zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) e [Seq. zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) usam duas ou três sequências e produzem uma sequência de tuplas. Essas funções são como as funções correspondentes disponíveis para [listas](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d). Não há nenhuma funcionalidade correspondente para separar uma sequência em duas ou mais sequências. Se você precisar dessa funcionalidade para uma sequência, converta a sequência em uma lista e use [list. Unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

## <a name="sorting-comparing-and-grouping"></a>Classificando, comparando e agrupando

As funções de classificação com suporte para listas também funcionam com sequências. Isso inclui [Seq. Sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) e [Seq. sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f). Essas funções iteram por toda a sequência.

Você compara duas sequências usando a função [Seq. compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) . A função compara os elementos sucessivos por vez e para quando encontra o primeiro par desigual. Quaisquer elementos adicionais não contribuem para a comparação.

O código a seguir demonstra o uso de `Seq.compareWith`.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet19.fs)]

No código anterior, apenas o primeiro elemento é computado e examinado, e o resultado é-1.

[Seq. countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) usa uma função que gera um valor chamado *chave* para cada elemento. Uma chave é gerada para cada elemento chamando essa função em cada elemento. `Seq.countBy`em seguida, retorna uma sequência que contém os valores de chave e uma contagem do número de elementos que geraram cada valor da chave.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet201.fs)]

A saída é a seguinte.

```console
(1, 34) (2, 33) (0, 33)
```

A saída anterior mostra que havia 34 elementos da sequência original que produziram os valores de chave 1, 33 que produziram a chave 2 e 33 valores que produziram a chave 0.

Você pode agrupar elementos de uma sequência chamando [Seq. GroupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd). `Seq.groupBy`usa uma sequência e uma função que gera uma chave de um elemento. A função é executada em cada elemento da sequência. `Seq.groupBy`Retorna uma sequência de tuplas, em que o primeiro elemento de cada tupla é a chave e a segunda é uma sequência de elementos que produzem essa chave.

O exemplo de código a seguir mostra o `Seq.groupBy` uso de para particionar a sequência de números de 1 a 100 em três grupos que têm os valores de chave distintos 0, 1 e 2.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet202.fs)]

A saída é a seguinte.

```console
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

Você pode criar uma sequência que elimina elementos duplicados chamando [Seq. Distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401). Ou você pode usar [Seq. distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), que usa uma função de geração de chaves a ser chamada em cada elemento. A sequência resultante contém elementos da sequência original que têm chaves exclusivas; os elementos posteriores que produzem uma chave duplicada para um elemento anterior são descartados.

O exemplo de código a seguir ilustra o `Seq.distinct`uso de. `Seq.distinct`é demonstrado pela geração de sequências que representam números binários e, em seguida, mostrando que os únicos elementos distintos são 0 e 1.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet22.fs)]

O código a seguir `Seq.distinctBy` demonstra iniciando com uma sequência que contém números negativos e positivos e usando a função de valor absoluto como a função de geração de chaves. A sequência resultante não tem todos os números positivos que correspondem aos números negativos na sequência, pois os números negativos aparecem anteriormente na sequência e, portanto, são selecionados em vez dos números positivos que têm o mesmo absoluto valor ou chave.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>Sequências ReadOnly e armazenadas em cache

[Seq. ReadOnly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) cria uma cópia somente leitura de uma sequência. `Seq.readonly`é útil quando você tem uma coleção de leitura/gravação, como uma matriz, e não deseja modificar a coleção original. Essa função pode ser usada para preservar o encapsulamento de dados. No exemplo de código a seguir, um tipo que contém uma matriz é criado. Uma propriedade expõe a matriz, mas em vez de retornar uma matriz, ela retorna uma sequência que é criada a partir da matriz `Seq.readonly`usando.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet24.fs)]

[Seq. cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) cria uma versão armazenada de uma sequência. Use `Seq.cache` para evitar a reavaliação de uma sequência, ou quando você tiver vários threads que usam uma sequência, mas você deve certificar-se de que cada elemento seja acionado apenas uma vez. Quando você tem uma sequência que está sendo usada por vários threads, você pode ter um thread que enumera e computa os valores para a sequência original, e os threads restantes podem usar a sequência armazenada em cache.

## <a name="performing-computations-on-sequences"></a>Executando cálculos em sequências

Operações aritméticas simples são como as de listas, como [Seq. Average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq. Sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq. averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq. sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)e assim por diante.

[Seq. fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq. reduz](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)e [Seq. scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) são como as funções correspondentes que estão disponíveis para listas. As sequências dão suporte a um subconjunto das variações completas dessas funções que listam o suporte. Para obter mais informações e exemplos, consulte [listas](lists.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Tipos F#](fsharp-types.md)
