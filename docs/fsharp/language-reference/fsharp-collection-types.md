---
title: Tipos de coleção de F#
description: Saiba mais sobre F# tipos de coleção e como eles diferem de tipos de coleção no .NET Framework.
ms.date: 05/16/2016
ms.openlocfilehash: b370d850deaacc961dff9515ffa8c20634af4ed6
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041716"
---
# <a name="f-collection-types"></a>Tipos de coleção de F#

Ao revisar este tópico, você pode determinar que F# tipo de coleção mais adequado a uma necessidade específica. Esses tipos de coleção diferem dos tipos de coleção no .NET Framework, como aqueles na `System.Collections.Generic` namespace, em que o F# tipos de coleção são criados de uma perspectiva de programação funcional em vez de um orientada a objeto Perspectiva. Mais especificamente, apenas a coleção de matriz tem elementos mutáveis. Portanto, quando você modifica uma coleção, você cria uma instância da coleção modificada em vez de alterar a coleção original.

Tipos de coleção também diferem no tipo de estrutura de dados no qual os objetos são armazenados. Estruturas de dados como tabelas de hash, listas vinculadas e matrizes têm diferentes características de desempenho e um conjunto diferente de operações disponíveis.

## <a name="f-collection-types"></a>Tipos de coleção de F#

A tabela a seguir mostra F# tipos de coleção.

|Tipo|Descrição|Links relacionados|
|----|-----------|-------------|
|[List](https://msdn.microsoft.com/library/c627b668-477b-4409-91ed-06d7f1b3e4a7)|Uma série imutável, ordenada, de elementos do mesmo tipo. Implementado como uma lista vinculada.|[Listas](lists.md)<br /><br />[Módulo List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)|
|[matriz](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)|Uma coleção de tamanho fixo, com base em zero, mutável de elementos de dados consecutivos que são todos do mesmo tipo.|[Matrizes](arrays.md)<br /><br />[Módulo array](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)<br /><br />[Módulo Array2D](https://msdn.microsoft.com/library/ae1a9746-7817-4430-bcdb-a79c2411bbd3)<br /><br />[Módulo Array3D](https://msdn.microsoft.com/library/c8355e2d-add8-48a4-8aa6-1c57ae74c560)|
|[seq](https://msdn.microsoft.com/library/2f0c87c6-8a0d-4d33-92a6-10d1d037ce75)|Uma série de lógica de elementos que são todos de um tipo. As sequências são particularmente úteis quando você tiver uma grande coleção ordenada de dados, mas não necessariamente pretende usar todos os elementos. Individual sequência de elementos são computados apenas como necessários, portanto, uma sequência pode executar melhor do que uma lista se não todos os elementos são usados. As sequências são representadas pela `seq<'T>` tipo, que é um alias para `IEnumerable<T>`. Portanto, qualquer tipo .NET Framework que implementa `System.Collections.Generic.IEnumerable<'T>` pode ser usado como uma sequência.|[Sequências](sequences.md)<br /><br />[Módulo SEQ](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)|
|[mapa](https://msdn.microsoft.com/library/975316ea-55e3-4987-9994-90897ad45664)|Um dicionário imutável de elementos. Elementos são acessados por chave.|[Módulo de mapa](https://msdn.microsoft.com/library/bfe61ead-f16c-416f-af98-56dbcbe23e4f)|
|[Set](https://msdn.microsoft.com/library/50cebdce-0cd7-4c5c-8ebc-f3a9e90b38d8)|Um conjunto imutável que se baseia em árvores binárias, onde a comparação é o F# função de comparação estrutural, que potencialmente usa implementações do `System.IComparable` interface em valores de chave.|[Definir módulo](https://msdn.microsoft.com/library/61efa732-d55d-4c32-993f-628e2f98e6a0)|

### <a name="table-of-functions"></a>Tabela de funções

Esta seção compara as funções que estão disponíveis no F# tipos de coleção. Dada a complexidade computacional da função, onde N é o tamanho da primeira coleção, e M é o tamanho da segunda coleção, se houver. Um traço (-) indica que essa função não está disponível na coleção. Como as sequências são avaliadas lentamente, uma função como SEQ. DISTINCT talvez (1) porque ele retorna imediatamente, embora ela ainda afeta o desempenho da sequência de quando enumerada.

|Função|Matriz|Lista|Sequência|Mapa|Set|Descrição|
|--------|-----|----|--------|---|---|-----------|
|acrescentar|O(M)|(N)|(N)|-|-|Retorna uma nova coleção que contém os elementos da coleção primeiro, seguido por elementos da segunda coleção.|
|adicionar|-|-|-|O (log N)|O (log N)|Retorna uma nova coleção com o elemento adicionado.|
|Média|(N)|(N)|(N)|-|-|Retorna a média dos elementos na coleção.|
|averageBy|(N)|(N)|(N)|-|-|Retorna a média dos resultados da função fornecido aplicado a cada elemento.|
|blit|(N)|-|-|-|-|Copia uma seção de uma matriz.|
|cache|-|-|(N)|-|-|Calcula e armazena os elementos de uma sequência.|
|cast|-|-|(N)|-|-|Converte os elementos no tipo especificado.|
|Escolha|(N)|(N)|(N)|-|-|Aplica-se a função fornecida `f` a cada elemento `x` da lista. Retorna a lista que contém os resultados para cada elemento em que a função retorna `Some(f(x))`.|
|coletar|(N)|(N)|(N)|-|-|Aplica-se a função fornecida para cada elemento da coleção, concatena todos os resultados e retorna a lista combinada.|
|compareWith|-|-|(N)|-|-|Compara duas sequências usando a função de comparação fornecido, elemento por elemento.|
|concat|(N)|(N)|(N)|-|-|Combina as determinado enumeração-de-enumerações como uma única enumeração concatenada.|
|contém|-|-|-|-|O (log N)|Retorna VERDADEIRO se o conjunto contiver o elemento especificado.|
|containsKey|-|-|-|O (log N)|-|Testa se um elemento está no domínio de um mapa.|
|count|-|-|-|-|(N)|Retorna o número de elementos no conjunto.|
|countBy|-|-|(N)|-|-|Aplica uma função de geração de chave para cada elemento de uma sequência e retorna uma sequência que gera as chaves exclusivas e seu número de ocorrências na sequência original.|
|copy|(N)|-|(N)|-|-|Copia a coleção.|
|criar|(N)|-|-|-|-|Cria uma matriz de elementos inteiros são todos inicialmente o valor especificado.|
|delay|-|-|O(1)|-|-|Retorna uma sequência que é criada da especificação atrasada determinada de uma sequência.|
|diferença|-|-|-|-|O (M &#42; log N)|Retorna um novo conjunto com os elementos do segundo conjunto removidos do primeiro conjunto.|
|Distintos|||(1)&AMP;#42;|||Retorna uma sequência que não contém nenhum entradas duplicadas de acordo com comparações de igualdade e hash genéricas nas entradas. Se um elemento ocorre várias vezes na sequência, ocorrências posteriores serão descartadas.|
|distinctBy|||(1)&AMP;#42;|||Retorna uma sequência que não contém nenhum entradas duplicadas de acordo com as comparações de igualdade e hash genéricas nas chaves que retorna a função de geração de chave fornecida. Se um elemento ocorre várias vezes na sequência, ocorrências posteriores serão descartadas.|
|empty|O(1)|O(1)|O(1)|O(1)|O(1)|Cria uma coleção vazia.|
|existe|(N)|(N)|(N)|O (log N)|O (log N)|Testa se qualquer elemento da sequência satisfaz o predicado em questão.|
|exists2|O(min(N,M))|-|O(min(N,M))|||Testa se qualquer par de elementos correspondentes das sequências de entrada satisfaz o predicado em questão.|
|fill|(N)|||||Define um intervalo de elementos da matriz como o valor especificado.|
|filtrar|(N)|(N)|(N)|(N)|(N)|Retorna uma nova coleção que contém apenas os elementos da coleção para a qual o predicado determinado retorna `true`.|
|find|(N)|(N)|(N)|O (log N)|-|Retorna o primeiro elemento para o qual a função fornecida retorna `true`. Retorna `System.Collections.Generic.KeyNotFoundException` se não houver tal elemento.|
|findIndex|(N)|(N)|(N)|-|-|Retorna o índice do primeiro elemento na matriz que satisfaz o predicado em questão. Gera `System.Collections.Generic.KeyNotFoundException` se nenhum elemento satisfaz o predicado.|
|findKey|-|-|-|O (log N)|-|Avalia a função em cada mapeamento da coleção e retorna a chave para o mapeamento primeiro onde a função retorna `true`. Se esse elemento não existir, essa função gera `System.Collections.Generic.KeyNotFoundException`.|
|número de partições|(N)|(N)|(N)|(N)|(N)|Aplica uma função a cada elemento da coleção, um argumento acumulador por meio da computação de threading. Se a função de entrada é f e os elementos são i0... no, esta função calcula f (... (f s i0)...) No.|
|fold2|(N)|(N)|-|-|-|Aplica uma função aos elementos correspondentes de duas coleções, threading um argumento acumulador por meio da computação. As coleções devem ter tamanhos idênticos. Se a função de entrada é f e os elementos são i0... no e... j0 jN, esta função calcula f (... (f s i0 j0)...) Em jN.|
|foldBack|(N)|(N)|-|(N)|(N)|Aplica uma função a cada elemento da coleção, um argumento acumulador por meio da computação de threading. Se a função de entrada é f e os elementos são i0... no, esta função calcula i0 f (... (f em s)).|
|foldBack2|(N)|(N)|-|-|-|Aplica uma função aos elementos correspondentes de duas coleções, threading um argumento acumulador por meio da computação. As coleções devem ter tamanhos idênticos. Se a função de entrada é f e os elementos são i0... no e... j0 jN, esta função calcula f i0 j0 (... (f em jN s)).|
|forall|(N)|(N)|(N)|(N)|(N)|Testa se todos os elementos da coleção satisfazem o predicado em questão.|
|forall2|(N)|(N)|(N)|-|-|Testa se todos os elementos correspondentes da coleção satisfazem o predicado em questão pairwise.|
|obter / enésimo|O(1)|(N)|(N)|-|-|Retorna um elemento da coleção devida à sua indexação.|
|Head|-|O(1)|O(1)|-|-|Retorna o primeiro elemento da coleção.|
|init|(N)|(N)|O(1)|-|-|Cria uma coleção de dada a dimensão e uma função geradora para calcular os elementos.|
|initInfinite|-|-|O(1)|-|-|Gera uma sequência que, quando iteradas, retorna elementos sucessivos chamando a função determinada.|
|intersect|-|-|-|-|O (log N &#42; log M)|Calcula a interseção de dois conjuntos.|
|intersectMany|-|-|-|-|S (N1 &AMP;#42; N2...)|Calcula a interseção de uma sequência de conjuntos. A sequência não deve ficar vazia.|
|isEmpty|O(1)|O(1)|O(1)|O(1)|-|Retorna `true` se a coleção está vazia.|
|isProperSubset|-|-|-|-|O (M &#42; log N)|Retorna `true` se todos os elementos do primeiro conjunto estão no segundo conjunto, e pelo menos um elemento do segundo conjunto não está no primeiro conjunto.|
|isProperSuperset|-|-|-|-|O (M &#42; log N)|Retorna `true` se todos os elementos do segundo conjunto estiverem no primeiro conjunto, e pelo menos um elemento do primeiro conjunto não está no segundo conjunto.|
|isSubset|-|-|-|-|O (M &#42; log N)|Retorna `true` se todos os elementos do primeiro conjunto estiverem no segundo conjunto.|
|isSuperset|-|-|-|-|O (M &#42; log N)|Retorna `true` se todos os elementos do segundo conjunto estiverem no primeiro conjunto.|
|Iter|(N)|(N)|(N)|(N)|(N)|Aplica-se a função fornecida para cada elemento da coleção.|
|iteri|(N)|(N)|(N)|-|-|Aplica-se a função fornecida para cada elemento da coleção. O inteiro que é passado para a função indica o índice do elemento.|
|iteri2|(N)|(N)|-|-|-|Aplica-se a função fornecida a um par de elementos que são desenhados de índices correspondentes em duas matrizes. O inteiro que é passado para a função indica o índice dos elementos. As duas matrizes devem ter o mesmo comprimento.|
|iter2|(N)|(N)|(N)|-|-|Aplica-se a função fornecida a um par de elementos que são desenhados de índices correspondentes em duas matrizes. As duas matrizes devem ter o mesmo comprimento.|
|last|O(1)|(N)|(N)|-|-|Retorna o último item na coleção aplicável.|
|length|O(1)|(N)|(N)|-|-|Retorna o número de elementos na coleção.|
|map|(N)|(N)|O(1)|-|-|Cria uma coleção cujos elementos são os resultados da aplicação da função fornecida para cada elemento da matriz.|
|map2|(N)|(N)|O(1)|-|-|Cria uma coleção cujos elementos são os resultados da aplicação da função fornecida para os elementos correspondentes das duas coleções de pares. As duas matrizes de entrada devem ter o mesmo tamanho.|
|map3|-|(N)|-|-|-|Cria uma coleção cujos elementos são os resultados da aplicação da função fornecida para os elementos correspondentes das três coleções simultaneamente.|
|mapi|(N)|(N)|(N)|-|-|Cria uma matriz cujos elementos são os resultados da aplicação da função fornecida para cada elemento da matriz. O índice de inteiro que é passado para a função indica o índice do elemento que está sendo transformado.|
|mapi2|(N)|(N)|-|-|-|Cria uma coleção cujos elementos são os resultados da aplicação da função fornecida para os elementos correspondentes das duas coleções emparelhadas, também passando o índice dos elementos. As duas matrizes de entrada devem ter o mesmo tamanho.|
|max|(N)|(N)|(N)|-|-|Retorna o maior elemento na coleção, comparada usando o [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) operador.|
|maxBy|(N)|(N)|(N)|-|-|Retorna o maior elemento na coleção, em comparação com o uso [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) no resultado da função.|
|maxElement|-|-|-|-|O (log N)|Retorna o maior elemento no conjunto de acordo com a ordem que é usado para o conjunto.|
|min|(N)|(N)|(N)|-|-|Retorna o menor elemento na coleção, comparada usando o [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) operador.|
|minBy|(N)|(N)|(N)|-|-|Retorna o menor elemento na coleção, comparada usando o [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) operador sobre o resultado da função.|
|minElement|-|-|-|-|O (log N)|Retorna o elemento mais baixo no conjunto de acordo com a ordem que é usado para o conjunto.|
|ofArray|-|(N)|O(1)|(N)|(N)|Cria uma coleção que contém os mesmos elementos que a matriz fornecida.|
|ofList|(N)|-|O(1)|(N)|(N)|Cria uma coleção que contém os mesmos elementos que a lista fornecida.|
|ofSeq|(N)|(N)|-|(N)|(N)|Cria uma coleção que contém os mesmos elementos que a sequência determinada.|
|paridade|-|-|(N)|-|-|Retorna uma sequência de cada elemento na sequência de entrada e seu predecessor, exceto o primeiro elemento, que é retornado somente como o predecessor do segundo elemento.|
|partition|(N)|(N)|-|(N)|(N)|Divide a coleção em duas coleções. A primeira coleção contém os elementos para os quais o predicado determinado retorna `true`, e a segunda coleção contém os elementos para os quais o predicado determinado retorna `false`.|
|permute|(N)|(N)|-|-|-|Retorna uma matriz com todos os elementos permutados de acordo com a permutação especificada.|
|Escolher|(N)|(N)|(N)|O (log N)|-|Aplica-se a função fornecida para sucessivos elementos, retornando o primeiro resultado em que a função retorna alguns. Se a função nunca retorna alguns, `System.Collections.Generic.KeyNotFoundException` é gerado.|
|readonly|-|-|(N)|-|-|Cria um objeto de sequência que delega para o objeto de sequência determinada. Essa operação garante que uma conversão de tipo não é possível redescobrir e modificar a sequência original. Por exemplo, se considerando uma matriz, a sequência retornada retornará os elementos da matriz, mas você não pode converter o objeto de sequência retornada em uma matriz.|
|reduce|(N)|(N)|(N)|-|-|Aplica uma função a cada elemento da coleção, um argumento acumulador por meio da computação de threading. Essa função é iniciado com a aplicação da função para os primeiros dois elementos, passa esse resultado em uma função, juntamente com o terceiro elemento e assim por diante. A função retorna o resultado final.|
|reduceBack|(N)|(N)|-|-|-|Aplica uma função a cada elemento da coleção, um argumento acumulador por meio da computação de threading. Se a função de entrada é f e os elementos são i0... no, esta função calcula i0 f (... (f em-1)).|
|remove|-|-|-|O (log N)|O (log N)|Remove um elemento de domínio do mapa. Nenhuma exceção é gerada se o elemento não estiver presente.|
|replicar|-|(N)|-|-|-|Cria uma lista de um comprimento especificado com cada elemento definido como o valor especificado.|
|rev|(N)|(N)|-|-|-|Retorna uma nova lista com os elementos na ordem inversa.|
|verificação|(N)|(N)|(N)|-|-|Aplica uma função a cada elemento da coleção, um argumento acumulador por meio da computação de threading. Essa operação se aplica a função para o segundo argumento e o primeiro elemento da lista. A operação, em seguida, passa esse resultado em uma função, juntamente com o segundo elemento, e assim por diante. Por fim, a operação retorna a lista de resultados intermediários e o resultado final.|
|scanBack|(N)|(N)|-|-|-|É semelhante a operação foldBack, mas retorna os resultados intermediários e finais.|
|singleton|-|-|O(1)|-|O(1)|Retorna uma sequência que produz apenas um item.|
|set|O(1)|-|-|-|-|Define um elemento de uma matriz como o valor especificado.|
|skip|-|-|(N)|-|-|Retorna uma sequência que ignora N elementos da sequência de base e, em seguida, gera os elementos restantes da sequência.|
|SkipWhile|-|-|(N)|-|-|Retorna uma sequência que, quando iteradas, ignora elementos da sequência subjacente enquanto o determinado retorna predicado `true` e, em seguida, gera os elementos restantes da sequência.|
|sort|Média do (log N de N)<br /><br />O(N^2) pior caso|O (log N de N)|O (log N de N)|-|-|Classifica a coleção por valor do elemento. Elementos são comparados usando [comparar](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortBy|Média do (log N de N)<br /><br />O(N^2) pior caso|O (log N de N)|O (log N de N)|-|-|Classifica a lista fornecida usando chaves que fornece a projeção de determinado. As chaves são comparadas usando [comparar](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlace|Média do (log N de N)<br /><br />O(N^2) pior caso|-|-|-|-|Classifica os elementos de uma matriz a mutação em vigor e usando a função de comparação especificado. Elementos são comparados usando [comparar](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceBy|Média do (log N de N)<br /><br />O(N^2) pior caso|-|-|-|-|Classifica os elementos de uma matriz a mutação em vigor e usando a projeção fornecida para as chaves. Elementos são comparados usando [comparar](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceWith|Média do (log N de N)<br /><br />O(N^2) pior caso|-|-|-|-|Classifica os elementos de uma matriz a mutação em vigor e usando a função de comparação fornecido como a ordem.|
|sortWith|Média do (log N de N)<br /><br />O(N^2) pior caso|O (log N de N)|-|-|-|Classifica os elementos de uma coleção, usando a função de comparação fornecido como a ordem e retornando uma nova coleção.|
|sub|(N)|-|-|-|-|Cria uma matriz que contém o subintervalo determinado iniciando o índice e o comprimento especificado.|
|sum|(N)|(N)|(N)|-|-|Retorna a soma dos elementos na coleção.|
|sumBy|(N)|(N)|(N)|-|-|Retorna a soma dos resultados gerados pela aplicação da função para cada elemento da coleção.|
|Parte final|-|O(1)|-|-|-|Retorna a lista sem o primeiro elemento.|
|Take|-|-|(N)|-|-|Retorna os elementos da sequência de até uma contagem especificada.|
|takeWhile|-|-|O(1)|-|-|Retorna uma sequência que, quando iteradas, produz elementos da sequência subjacente enquanto o determinado retorna predicado `true` e, em seguida, não retorna mais nenhum elemento.|
|toArray|-|(N)|(N)|(N)|(N)|Cria uma matriz de determinada coleção.|
|toList|(N)|-|(N)|(N)|(N)|Cria uma lista da coleção fornecida.|
|toSeq|O(1)|O(1)|-|O(1)|O(1)|Cria uma sequência de determinada coleção.|
|Truncar|-|-|O(1)|-|-|Retorna uma sequência que, quando enumerada, retorna não mais do que elementos N seguintes.|
|tryFind|(N)|(N)|(N)|O (log N)|-|Pesquisa um elemento que satisfaz um predicado em questão.|
|tryFindIndex|(N)|(N)|(N)|-|-|Procura o primeiro elemento que satisfaz um predicado especificado e retorna o índice do elemento correspondente, ou `None` se não houver tal elemento.|
|tryFindKey|-|-|-|O (log N)|-|Retorna a chave do primeiro mapeamento da coleção que satisfaz o predicado em questão, ou retorna `None` se não houver tal elemento.|
|tryPick|(N)|(N)|(N)|O (log N)|-|Aplica-se a função fornecida para sucessivos elementos, retornando o primeiro resultado em que a função retorna `Some` para algum valor. Se esse elemento não existir, a operação retorna `None`.|
|Desdobrar|-|-|(N)|-|-|Retorna uma sequência que contém os elementos que gera a determinada computação.|
|union|-|-|-|-|O (M &#42; log N)|Calcula a união de dois conjuntos.|
|unionMany|-|-|-|-|S (N1 &AMP;#42; N2...)|Calcula a união de uma sequência de conjuntos.|
|unzip|(N)|(N)|(N)|-|-|Divide uma lista de pares em duas listas.|
|unzip3|(N)|(N)|(N)|-|-|Divide uma lista de triplos em três listas.|
|em janelas|-|-|(N)|-|-|Retorna uma sequência que gera janelas deslizantes do que contém elementos que são obtidos de sequência de entrada. Cada janela é retornada como uma nova matriz.|
|zip|(N)|(N)|(N)|-|-|Combina duas coleções em uma lista de pares. As duas listas devem ter tamanhos iguais.|
|zip3|(N)|(N)|(N)|-|-|Combina três coleções em uma lista de triplos. As listas devem ter tamanhos iguais.|

## <a name="see-also"></a>Consulte também

- [Tipos F#](fsharp-types.md)
- [Referência da Linguagem F#](index.md)
