---
title: Listas (F#)
description: Saiba mais sobre F# lista uma série imutável, ordenada, de elementos do mesmo tipo.
ms.date: 05/16/2016
ms.openlocfilehash: f7b9054226a1dd004ac78673a059bd1c35e325a5
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297498"
---
# <a name="lists"></a>Listas

> [!NOTE]
> Os links de referência da API neste artigo levarão você até o MSDN.  A referência da API docs.microsoft.com não está completa.

Uma lista em F# é uma série imutável, ordenada, de elementos do mesmo tipo. Para executar operações básicas em listas, usar as funções do [módulo lista](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

## <a name="creating-and-initializing-lists"></a>Criando e inicializando listas

Você pode definir uma lista ao relacionar explicitamente os elementos, separados por ponto e vírgula e entre colchetes, como mostra a linha de código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

Você também pode colocar quebras de linha entre os elementos, caso em que as vírgulas são opcionais. A última sintaxe pode resultar em um código mais legível quando as expressões de inicialização de elemento são mais longas ou quando você quer incluir um comentário para cada elemento.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

Normalmente, todos os elementos da lista devem ser do mesmo tipo. Uma exceção existe quando uma lista em que os elementos são especificados para ser um tipo de base pode ter elementos do tipo derivado. Dessa forma, o que segue é aceitável, porque tanto `Button` quanto `CheckBox` derivam de `Control`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

Você também pode definir os elementos da lista, usando um intervalo indicado por inteiros separados pelo operador de intervalo (`..`), como mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

Uma lista vazia é especificada por um par de colchetes sem nada entre eles.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

Você também pode usar uma expressão de sequência para criar uma lista. Ver [expressões de sequência](sequences.md#sequence-expressions) para obter mais informações. Por exemplo, o código a seguir cria uma lista dos quadrados de números inteiros de 1 a 10.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>Operadores para trabalhar com listas

Você pode anexar elementos a uma lista usando o operador (cons) `::`. Se `list1` for `[2; 3; 4]`, o seguinte código criará `list2` como `[100; 2; 3; 4]`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

Você pode concatenar listas que possuem tipos compatíveis usando o operador `@`, como no código a seguir. Se `list1` for `[2; 3; 4]` e `list2` for `[100; 2; 3; 4]`, esse código criará `list3` como `[2; 3; 4; 100; 2; 3; 4]`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

Funções para executar operações em listas estão disponíveis na [módulo lista](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

Como as listas em F# são imutáveis, quaisquer operações de modificação geram novas listas em vez de modificar as listas existentes.

Listas no F# são implementados como listas vinculadas individualmente, o que significa que as operações que acessam apenas o cabeçalho da lista são (1) e acesso de elemento é O (*n*).

## <a name="properties"></a>Propriedades

O tipo de lista oferece suporte às seguintes propriedades:

|Propriedade|Tipo|Descrição|
|--------|----|-----------|
|[Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|O primeiro elemento.|
|[vazio](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|A propriedade estática que retorna uma lista vazia do tipo apropriado.|
|[IsEmpty](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|`true` se a lista não tiver elementos.|
|[Item](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|O elemento no índice especificado (com base em zero).|
|[Comprimento](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|O número de elementos.|
|[Parte final](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|A lista sem o primeiro elemento.|
A seguir, alguns exemplos de como usar essas propriedades.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a>Usando as listas

A programação com listas permite executar operações complexas com uma pequena quantidade de código. Esta seção descreve operações comuns em listas que são importantes para programação funcional.

### <a name="recursion-with-lists"></a>Recursão com listas

As listas são particularmente adequadas para técnicas de programação recursivas. Considere uma operação que deve ser executada em cada elemento de uma lista. Você pode fazer isso de forma recursiva, operando no cabeçalho da lista e passando para a parte final da lista, que é uma lista menor que consiste na lista original, sem o primeiro elemento, e volte novamente ao próximo nível de recursão.

Para escrever uma função recursiva, você usa o operador cons (`::`) em correspondência de padrões, o que permite separar o cabeçalho de uma lista da parte final da lista.

O exemplo de código a seguir mostra como usar a correspondência de padrões para implementar uma função recursiva que executa operações em uma lista.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

O código anterior funciona bem para pequenas listas, mas para listas maiores, pode estourar a pilha. O código a seguir melhora este código usando um argumento acumulador, uma técnica padrão para trabalhar com funções recursivas. O uso do argumento acumulador torna a parte final da função recursiva, o que economiza espaço em pilha.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

A função `RemoveAllMultiples` é uma função recursiva que usa duas listas. A primeira lista contém os números cujos múltiplos serão removidos e a segunda lista é a lista a partir da qual os números serão removidos. O código no exemplo a seguir usa essa função recursiva para eliminar todos os números não primos de uma lista, deixando uma lista de números primos como o resultado.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

A saída é a seguinte:

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>Funções do módulo

O [módulo lista](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) fornece funções que acessam os elementos de uma lista. O elemento cabeçalho é o mais rápido e fácil de acessar. Use a propriedade [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) ou a função do módulo [List. head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2). Você pode acessar a parte final de uma lista usando o [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) propriedade ou o [List. tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) função. Para localizar um elemento por índice, use o [List. Nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) função. `List.nth` percorre a lista. Portanto, é O (*n*). Se seu código usa `List.nth` com frequência, considere o uso de uma matriz em vez de uma lista. O acesso de elemento em matrizes é O(1).

### <a name="boolean-operations-on-lists"></a>Operações boolianas em listas

O [List. IsEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) função determina se uma lista tem todos os elementos.

O [List. Exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) função se aplica a um valor booliano teste aos elementos de uma lista e retorna `true` se algum elemento satisfizer o teste. [List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) é semelhante, mas opera em pares sucessivos de elementos em duas listas.

O código a seguir demonstra o uso de `List.exists`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

A saída é a seguinte:

```
For list [0; 1; 2; 3], contains zero is true
```

O exemplo a seguir demonstra o uso de `List.exists2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

A saída é a seguinte:

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

Você pode usar [List. ForAll](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) se você deseja testar se todos os elementos de uma lista atendem a uma condição.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

A saída é a seguinte:

```
true
false
```

Da mesma forma, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) determina se todos os elementos nas posições correspondentes em duas listas satisfazem a uma expressão booliana que envolve cada par de elementos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

A saída é a seguinte:

```
true
false
```

### <a name="sort-operations-on-lists"></a>Operações de classificação em listas

O [List. Sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List. SortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), e [List. sortwith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) funções classificar listas. A função de classificação determina qual dessas três funções usar. `List.sort` usa uma comparação genérica padrão. A comparação genérica utiliza operadores globais com base na função de comparação genérica para comparar valores. Funciona de forma eficiente com uma grande variedade de tipos de elementos, tais como tipos numéricos simples, tuplas, registros, uniões discriminadas, listas, matrizes e qualquer tipo que implementa `System.IComparable`. Para os tipos que implementam `System.IComparable`, a comparação genérica usa a função `System.IComparable.CompareTo()`. A comparação genérica também funciona com cadeias de caracteres, mas usa uma ordem de classificação independente de cultura. A comparação genérica não deve ser usada em tipos sem suporte, como os tipos de função. Além disso, o desempenho da comparação genérica padrão é melhor para tipos estruturados pequenos; para tipos estruturados maiores que precisam ser comparados e classificados com frequência, considere implementar `System.IComparable` e fornecer uma implementação eficiente do método `System.IComparable.CompareTo()`.

`List.sortBy` usa uma função que retorna um valor usado como critério de classificação e `List.sortWith` assume uma função de comparação como argumento. Essas duas últimas funções são úteis quando você está trabalhando com tipos que não suportam comparação ou quando a comparação requer mais semântica de comparação complexa, como é o caso das cadeias de caracteres com reconhecimento de cultura.

O exemplo a seguir demonstra o uso de `List.sort`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

A saída é a seguinte:

```
[-2; 1; 4; 5; 8]
```

O exemplo a seguir demonstra o uso de `List.sortBy`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

A saída é a seguinte:

```
[1; -2; 4; 5; 8]
```

O exemplo a seguir demonstra o uso de `List.sortWith`. Neste exemplo, a função de comparação personalizada `compareWidgets` é usada para comparar um primeiro campo de um tipo personalizado e depois outro, quando os valores do primeiro campo são iguais.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

A saída é a seguinte:

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a>Operações de pesquisa em listas

Várias operações de pesquisa têm suporte para listas. A forma mais simples, [List. Find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), permite que você localize o primeiro elemento que corresponde a uma determinada condição.

O exemplo de código a seguir demonstra o uso de `List.find` para encontrar o primeiro número divisível por 5 em uma lista.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

O resultado é 5.

Se os elementos forem transformados primeiro, chame [List. Pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), que usa uma função que retorna uma opção e procura a primeira opção de valor que é `Some(x)`. Em vez de retornar o elemento, `List.pick` retorna o resultado `x`. Se nenhum elemento correspondente for encontrado, `List.pick` lançará `System.Collections.Generic.KeyNotFoundException`. O código a seguir demonstra o uso de `List.pick`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

A saída é a seguinte:

```
"b"
```

Outro grupo de operações de pesquisa [List. tryfind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) e funções relacionadas, retornam um valor de opção. A função `List.tryFind` retorna o primeiro elemento de uma lista que satisfaz a uma condição se tal elemento existir, mas retorna o valor da opção `None` se o elemento não existir. A variação [List. tryfindindex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) retorna o índice do elemento, caso seja encontrado, em vez do próprio elemento. Essas funções são ilustradas no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

A saída é a seguinte:

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>Operações aritméticas em listas

Operações aritméticas comuns, como soma e média são incorporadas a [módulo lista](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788). Para trabalhar com [List. Sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), o tipo de elemento de lista deve suportar o `+` operador e ter um valor igual a zero. Todos os tipos aritméticos internos satisfazem a essas condições. Para trabalhar com [List. Average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), o tipo de elemento deve suportar divisão sem resto, o que exclui tipos integrais, mas permite que tipos de ponto flutuante. O [List. sumby](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) e [List. averageby](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) funções têm uma função como um parâmetro e os resultados dessa função são usados para calcular os valores da soma ou média.

O código a seguir demonstra o uso de `List.sum`, `List.sumBy` e `List.average`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

A saída é `1.000000`.

O código a seguir demonstra o uso de `List.averageBy`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

A saída é `5.5`.

### <a name="lists-and-tuples"></a>Listas e tuplas

As listas que contêm tuplas podem ser manipuladas pelas funções de compactação e descompactação. Essas funções combinam duas listas de valores únicos em uma lista de tuplas ou separam uma lista de tuplas em duas listas de valores únicos. A forma mais simples [List. zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) função usa duas listas de elementos únicos e produz uma única lista de pares de tupla. Outra versão, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), usa três listas de elementos únicos e produz uma única lista de tuplas que tem três elementos. O exemplo de código a seguir demonstra o uso de `List.zip`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

A saída é a seguinte:

```
[(1, -1); (2, -2); (3; -3)]
```

O exemplo de código a seguir demonstra o uso de `List.zip3`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

A saída é a seguinte:

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

O correspondente Descompacte versões, [List. Unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) e [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), usam listas de tuplas e retornam listas em uma tupla, em que a primeira lista contém todos os elementos que estavam primeiros em cada tupla e o segunda lista contém o segundo elemento de cada tupla e assim por diante.

O exemplo de código a seguir demonstra o uso de [List. Unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

A saída é a seguinte:

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

O exemplo de código a seguir demonstra o uso de [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

A saída é a seguinte:

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>Operando em elementos de lista

F# oferece suporte a uma variedade de operações em elementos de lista. É o mais simples [List. iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), que permite que você chame uma função em cada elemento de uma lista. Incluem variações [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), que permite que você execute uma operação em elementos de duas listas, [List. iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), que é como `List.iter` , exceto que o índice de cada elemento é passado como um argumento da função que é chamado para cada elemento, e [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), que é uma combinação da funcionalidade do `List.iter2` e `List.iteri`. O exemplo de código a seguir ilustra essas funções.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

A saída é a seguinte:

```
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

É outra função usada frequentemente que transforma os elementos da lista [List. map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), que permite que você aplicar uma função a cada elemento de uma lista e colocar todos os resultados em uma nova lista. [List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) e [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) são variações que usam várias listas. Você também pode usar [List. MAPI](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) e [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), se, além do elemento, a função precisa ser passada para o índice de cada elemento. A única diferença entre `List.mapi2` e `List.mapi` é que `List.mapi2` funciona com as duas listas. O exemplo a seguir ilustra [List. map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

A saída é a seguinte:

```
[2; 3; 4]
```

O exemplo a seguir demonstra o uso de `List.map2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

A saída é a seguinte:

```
[5; 7; 9]
```

O exemplo a seguir demonstra o uso de `List.map3`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

A saída é a seguinte:

```
[7; 10; 13]
```

O exemplo a seguir demonstra o uso de `List.mapi`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

A saída é a seguinte:

```
[1; 3; 5]
```

O exemplo a seguir demonstra o uso de `List.mapi2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

A saída é a seguinte:

```
[0; 7; 18]
```

[List. Collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) é como `List.map`, exceto que cada elemento produz uma lista e todas essas listas são concatenadas em uma lista final. No código a seguir, cada elemento da lista gera três números. Eles são todos coletados em uma única lista.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

A saída é a seguinte:

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

Você também pode usar [List. Filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), que usa uma condição booliana e produz uma nova lista que consiste apenas em elementos que satisfazem a condição dada.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

A lista resultante é `[2; 4; 6]`.

Uma combinação de mapa e filtro, [List. Choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) permite transformar e selecionar elementos ao mesmo tempo. `List.choose` aplica uma função que retorna uma opção para cada elemento de uma lista e retorna uma nova lista de resultados para os elementos quando a função retorna o valor de opção `Some`.

O código a seguir demonstra o uso de `List.choose` para selecionar palavras em maiúsculas a partir de uma lista de palavras.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

A saída é a seguinte:

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>Operando em várias listas

As listas podem ser reunidas. Para juntar duas listas em um, use [List. Append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426). Para juntar mais de duas listas, use [List. Concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a>Operações de dobra e digitalização

Algumas operações de lista envolvem interdependências entre todos os elementos da lista. As operações de dobra e digitalização são como `List.iter` e `List.map` em que você chamar uma função em cada elemento, mas essas operações fornecem um parâmetro adicional chamado a *acumulador* que carrega as informações por meio de a computação.

Use `List.fold` para executar um cálculo em uma lista.

O exemplo de código a seguir demonstra o uso de [List. Fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) para executar várias operações.

A lista é percorrida; o acumulador `acc` é um valor passado conforme ocorre o progresso do cálculo. O primeiro argumento usa o acumulador e o elemento da lista, retornando o resultado intermediário do cálculo para esse elemento da lista. O segundo argumento é o valor inicial do acumulador.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

As versões dessas funções que têm um dígito no nome da função operam em mais de uma lista. Por exemplo, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) realiza cálculos em duas listas.

O exemplo a seguir demonstra o uso de `List.fold2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold` e [List. Scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) diferem em que `List.fold` retorna o valor final do parâmetro adicional, mas `List.scan` retorna a lista dos valores intermediários (juntamente com o valor final) do parâmetro adicional.

Cada uma dessas funções inclui uma variação inversa, por exemplo, [List. foldback](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), que difere na ordem em que a lista é percorrida e a ordem dos argumentos. Além disso, `List.fold` e `List.foldBack` têm variações, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) e [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), que usam duas listas de comprimento igual. A função executada em cada elemento pode usar elementos correspondentes das duas listas para realizar alguma ação. Os tipos de elementos das duas listas podem ser diferentes, como no exemplo a seguir, em que uma lista contém valores de transação de uma conta bancária e a outra lista contém o tipo de transação: depósito ou retirada.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

Para um cálculo como somatória, `List.fold` e `List.foldBack` têm o mesmo efeito, porque o resultado não depende da ordem de passagem. No exemplo a seguir, `List.foldBack` é usado para adicionar os elementos em uma lista.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

O exemplo a seguir retorna ao exemplo da conta bancária. Desta vez, um novo tipo de transação é adicionado: cálculo de juros. O saldo final agora depende da ordem das transações.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

A função [List. reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) é semelhante a `List.fold` e `List.scan`, exceto que em vez de passar um acumulador separado, `List.reduce` usa uma função que leva dois argumentos do tipo de elemento, em vez de apenas um e um desses argumentos funciona como acumulador, o que significa que ele armazena o resultado intermediário do cálculo. `List.reduce` começa a operar nos dois primeiros elementos da lista e, em seguida, usa o resultado da operação juntamente com o próximo elemento. Como não há um acumulador separado que tem o seu próprio tipo, `List.reduce` pode ser usado no lugar de `List.fold` somente quando o acumulador e o tipo de elemento têm o mesmo tipo. O código a seguir demonstra o uso de `List.reduce`. `List.reduce` lançará uma exceção se a lista fornecida não tiver elementos.

No código a seguir, a primeira chamada para a expressão lambda recebeu os argumentos 2 e 4, retornando 6 e a chamada seguinte recebeu os argumentos 6 e 10, de modo que o resultado é 16.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a>Convertendo entre listas e outros tipos de coleção

O módulo `List` fornece funções para converter de e para sequências e matrizes. Para converter para ou de uma sequência, use [List. toseq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) ou [List. ofseq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0). Para converter de ou para uma matriz, use [List. ToArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) ou [List. ofarray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).

### <a name="additional-operations"></a>Operações adicionais

Para obter informações sobre operações adicionais em listas, consulte o tópico de referência de biblioteca [módulo Collections. List](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Tipos F#](fsharp-types.md)
- [Sequências](sequences.md)
- [Matrizes](arrays.md)
- [Opções](options.md)
