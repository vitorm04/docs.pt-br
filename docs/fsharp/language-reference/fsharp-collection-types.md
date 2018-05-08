---
title: Tipos de coleção de F#
description: 'Saiba mais sobre os tipos de coleção de F # e como elas diferem de tipos de coleção do .NET Framework.'
ms.date: 05/16/2016
ms.openlocfilehash: a94dc300d984ca31baf1eb7d1073e23b51ebd030
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="f-collection-types"></a>Tipos de coleção de F#

Ao analisar este tópico, você pode determinar quais F # coleção tipo mais adequado às especial. Esses tipos de coleção diferem dos tipos de coleção no .NET Framework, como aqueles no `System.Collections.Generic` namespace, em que os tipos de coleção de F # destinam-se de uma perspectiva de programação funcional em vez de uma perspectiva orientada a objeto. Mais especificamente, a coleção de matriz tem elementos mutáveis. Portanto, quando você modifica uma coleção, você cria uma instância da coleção modificada em vez de alterar a coleção original.

Tipos de coleção também diferem no tipo de estrutura de dados no qual os objetos são armazenados. Estruturas de dados como tabelas de hash, vinculadas listas e matrizes têm diferentes características de desempenho e um conjunto diferente de operações disponíveis.


## <a name="f-collection-types"></a>Tipos de coleção de F#
A tabela a seguir mostra os tipos de coleção de F #.



|Tipo|Descrição|Links relacionados|
|----|-----------|-------------|
|[List](https://msdn.microsoft.com/library/c627b668-477b-4409-91ed-06d7f1b3e4a7)|Uma série de imutável, ordenada de elementos do mesmo tipo. Implementado como uma lista vinculada.|[Listas](lists.md)<br /><br />[Módulo List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)|
|[matriz](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)|Uma coleção de tamanho fixo, com base em zero, mutável de elementos consecutivos de dados que são todas do mesmo tipo.|[Matrizes](arrays.md)<br /><br />[Módulo array](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)<br /><br />[Módulo Array2D](https://msdn.microsoft.com/library/ae1a9746-7817-4430-bcdb-a79c2411bbd3)<br /><br />[Módulo Array3D](https://msdn.microsoft.com/library/c8355e2d-add8-48a4-8aa6-1c57ae74c560)|
|[SEQ](https://msdn.microsoft.com/library/2f0c87c6-8a0d-4d33-92a6-10d1d037ce75)|Uma série de lógica de elementos que são de um tipo. As sequências são particularmente útil quando você tiver um grande ordenados de coleta de dados, mas necessariamente não pretende usar todos os elementos. Sequência individual elementos são computados apenas como necessário, para uma sequência pode executar melhor do que uma lista se não todos os elementos são usados. As sequências são representadas pelo `seq<'T>` tipo, que é um alias para `IEnumerable<T>`. Portanto, qualquer tipo do .NET Framework que implementa `System.Collections.Generic.IEnumerable<'T>` pode ser usado como uma sequência.|[Sequências](sequences.md)<br /><br />[Módulo SEQ](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)|
|[mapa](https://msdn.microsoft.com/library/975316ea-55e3-4987-9994-90897ad45664)|Um dicionário imutável de elementos. Elementos são acessados por chave.|[Módulo de mapa](https://msdn.microsoft.com/library/bfe61ead-f16c-416f-af98-56dbcbe23e4f)|
|[Set](https://msdn.microsoft.com/library/50cebdce-0cd7-4c5c-8ebc-f3a9e90b38d8)|Um conjunto imutável se baseia em árvores de binários, onde comparação é a função de comparação estrutural F #, que usa potencialmente implementações do `System.IComparable` interface em valores de chave.|[Módulo de conjunto](https://msdn.microsoft.com/library/61efa732-d55d-4c32-993f-628e2f98e6a0)|

### <a name="table-of-functions"></a>Tabela de funções
Esta seção compara as funções que estão disponíveis em tipos de coleção de F #. A complexidade computacional da função for especificada, onde N é o tamanho da coleção primeiro e M é o tamanho da segunda coleção, se houver. Um traço (-) indica que essa função não está disponível na coleção. Como as sequências são avaliadas lentamente, uma função como SEQ pode ser (1) porque retorna imediatamente, embora ele ainda afeta o desempenho da sequência de quando enumerada.



|Função|Matriz|Lista|Sequência|Mapa|Definir|Descrição|
|--------|-----|----|--------|---|---|-----------|
|acrescentar|O(M)|(N)|(N)|-|-|Retorna uma nova coleção que contém os elementos da coleção primeiro, seguido de elementos da segunda coleção.|
|adicionar|-|-|-|O (log N)|O (log N)|Retorna uma nova coleção com os elementos adicionados.|
|Média|(N)|(N)|(N)|-|-|Retorna a média dos elementos na coleção.|
|averageBy|(N)|(N)|(N)|-|-|Retorna a média dos resultados da função fornecido aplicada a cada elemento.|
|blit|(N)|-|-|-|-|Copia uma seção de uma matriz.|
|cache|-|-|(N)|-|-|Calcula e armazena os elementos de uma sequência.|
|cast|-|-|(N)|-|-|Converte os elementos para o tipo especificado.|
|Escolha|(N)|(N)|(N)|-|-|Aplica-se a função determinada `f` para cada elemento `x` da lista. Retorna a lista que contém os resultados para cada elemento em que a função retornará `Some(f(x))`.|
|coletar|(N)|(N)|(N)|-|-|Aplica-se a função fornecida para cada elemento da coleção, concatena todos os resultados e retorna a lista combinada.|
|compareWith|-|-|(N)|-|-|Compara duas sequências usando a função de comparação fornecido pelo elemento.|
|concat|(N)|(N)|(N)|-|-|Combina as determinado enumeração-de-enumerações como uma única enumeração concatenada.|
|contém|-|-|-|-|O (log N)|Retorna VERDADEIRO se o conjunto contém o elemento especificado.|
|containsKey|-|-|-|O (log N)|-|Testa se um elemento está no domínio de um mapa.|
|count|-|-|-|-|(N)|Retorna o número de elementos no conjunto.|
|countBy|-|-|(N)|-|-|Aplica uma função de geração de chave para cada elemento de uma sequência e retorna uma sequência que gera as chaves exclusivas e o número de ocorrências na sequência original.|
|copy|(N)|-|(N)|-|-|Copia a coleção.|
|criar|(N)|-|-|-|-|Cria uma matriz de elementos inteiras todos inicialmente o valor especificado.|
|atraso|-|-|O(1)|-|-|Retorna uma sequência que é criada da especificação de atrasada determinada de uma sequência.|
|diferença|-|-|-|-|O (M &#42; log N)|Retorna um novo conjunto com os elementos do segundo conjunto removidos do primeiro conjunto.|
|DISTINCT|||(1)&AMP;#42;|||Retorna uma sequência que não contém nenhum entradas duplicadas de acordo com genéricas comparações de igualdade e de hash nas entradas. Se um elemento ocorrer várias vezes na sequência, ocorrências posteriores serão descartadas.|
|distinctBy|||(1)&AMP;#42;|||Retorna uma sequência que não contém nenhum entradas duplicadas de acordo com as comparações de igualdade e hash genéricas nas chaves que retorna a função de geração de chave fornecida. Se um elemento ocorrer várias vezes na sequência, ocorrências posteriores serão descartadas.|
|empty|O(1)|O(1)|O(1)|O(1)|O(1)|Cria uma coleção vazia.|
|existe|(N)|(N)|(N)|O (log N)|O (log N)|Testa se qualquer elemento da sequência satisfazem o predicado em questão.|
|exists2|O(min(N,M))|-|O(min(N,M))|||Testa se qualquer par de elementos correspondentes das sequências de entrada satisfaz o predicado em questão.|
|fill|(N)|||||Define um intervalo de elementos da matriz como o valor especificado.|
|filtrar|(N)|(N)|(N)|(N)|(N)|Retorna uma nova coleção que contém apenas os elementos da coleção para a qual o predicado em questão retorna `true`.|
|find|(N)|(N)|(N)|O (log N)|-|Retorna o primeiro elemento para o qual a função determinada retorna `true`. Retorna `System.Collections.Generic.KeyNotFoundException` se esse elemento não existe.|
|findIndex|(N)|(N)|(N)|-|-|Retorna o índice do primeiro elemento na matriz que satisfaz o predicado em questão. Gera `System.Collections.Generic.KeyNotFoundException` se nenhum elemento satisfaz o predicado.|
|findKey|-|-|-|O (log N)|-|Avalia a função em cada mapeamento da coleção e retorna a chave para o mapeamento primeiro onde a função retornará `true`. Se esse elemento não existe, esta função gera `System.Collections.Generic.KeyNotFoundException`.|
|Dobra|(N)|(N)|(N)|(N)|(N)|Aplica uma função para cada elemento da coleção, um argumento acumulador por meio da computação de threading. Se a função de entrada é f e os elementos são i0... no, essa função calcula f (... (f s i0)...) No.|
|fold2|(N)|(N)|-|-|-|Aplica uma função para os elementos correspondentes das duas coleções, de um argumento acumulador por meio da computação de threading. As coleções devem ter tamanhos idênticos. Se a função de entrada é f e os elementos são i0... no e... j0 jN, essa função calcula f (... (f s i0 j0)...) Em jN.|
|foldBack|(N)|(N)|-|(N)|(N)|Aplica uma função para cada elemento da coleção, um argumento acumulador por meio da computação de threading. Se a função de entrada é f e os elementos são i0... no, essa função calcula f i0 (... (f em s)).|
|foldBack2|(N)|(N)|-|-|-|Aplica uma função para os elementos correspondentes das duas coleções, de um argumento acumulador por meio da computação de threading. As coleções devem ter tamanhos idênticos. Se a função de entrada é f e os elementos são i0... no e... j0 jN, essa função calcula f i0 j0 (... (f em jN s)).|
|ForAll|(N)|(N)|(N)|(N)|(N)|Verifica se todos os elementos da coleção satisfazem o predicado em questão.|
|forall2|(N)|(N)|(N)|-|-|Verifica se todos os elementos correspondentes da coleção satisfazem o predicado em questão pairwise.|
|obter / enésimo|O(1)|(N)|(N)|-|-|Retorna um elemento de uma coleção fornecida seu índice.|
|Cabeçalho|-|O(1)|O(1)|-|-|Retorna o primeiro elemento da coleção.|
|Init|(N)|(N)|O(1)|-|-|Cria uma coleção fornecida a dimensão e uma função de gerador para computar os elementos.|
|initInfinite|-|-|O(1)|-|-|Gera uma sequência que, quando iteradas, retorna elementos sucessivos chamando a função determinada.|
|Se cruzam|-|-|-|-|O (log N &#42; log M)|Calcula a interseção de dois conjuntos.|
|intersectMany|-|-|-|-|O (N1 &AMP;#42; N2...)|Calcula a interseção de uma sequência de conjuntos. A sequência não deve ficar vazia.|
|IsEmpty|O(1)|O(1)|O(1)|O(1)|-|Retorna `true` se a coleção está vazia.|
|isProperSubset|-|-|-|-|O (M &#42; log N)|Retorna `true` se todos os elementos do primeiro conjunto no segundo conjunto, e pelo menos um elemento do segundo conjunto não está no primeiro conjunto.|
|isProperSuperset|-|-|-|-|O (M &#42; log N)|Retorna `true` se todos os elementos do segundo conjunto são o primeiro conjunto e pelo menos um elemento do primeiro conjunto não está no segundo conjunto.|
|isSubset|-|-|-|-|O (M &#42; log N)|Retorna `true` se todos os elementos do primeiro conjunto no segundo conjunto.|
|isSuperset|-|-|-|-|O (M &#42; log N)|Retorna `true` se todos os elementos do segundo conjunto são o primeiro conjunto.|
|iter|(N)|(N)|(N)|(N)|(N)|Aplica-se a função fornecida para cada elemento da coleção.|
|iteri|(N)|(N)|(N)|-|-|Aplica-se a função fornecida para cada elemento da coleção. O inteiro que é passado para a função indica o índice do elemento.|
|iteri2|(N)|(N)|-|-|-|Aplica-se a função fornecida para um par de elementos que são desenhadas de correspondência de índices em duas matrizes. O inteiro que é passado para a função indica o índice dos elementos. As duas matrizes devem ter o mesmo comprimento.|
|iter2|(N)|(N)|(N)|-|-|Aplica-se a função fornecida para um par de elementos que são desenhadas de correspondência de índices em duas matrizes. As duas matrizes devem ter o mesmo comprimento.|
|length|O(1)|(N)|(N)|-|-|Retorna o número de elementos na coleção.|
|map|(N)|(N)|O(1)|-|-|Cria uma coleção cujos elementos são os resultados da aplicação da função fornecida para cada elemento da matriz.|
|map2|(N)|(N)|O(1)|-|-|Cria uma coleção cujos elementos são os resultados da aplicação da função de determinada para os elementos correspondentes das duas coleções de cache. As duas matrizes de entrada devem ter o mesmo comprimento.|
|map3|-|(N)|-|-|-|Cria uma coleção cujos elementos são os resultados da aplicação da função de determinada para os elementos correspondentes das três coleções simultaneamente.|
|MAPI|(N)|(N)|(N)|-|-|Cria uma matriz cujos elementos são os resultados da aplicação da função fornecida para cada elemento da matriz. O índice de inteiro que é passado para a função indica o índice do elemento que está sendo transformado.|
|mapi2|(N)|(N)|-|-|-|Cria uma coleção cujos elementos são os resultados da aplicação da função fornecida para os elementos correspondentes das duas coleções emparelhadas, também, passando o índice dos elementos. As duas matrizes de entrada devem ter o mesmo comprimento.|
|max|(N)|(N)|(N)|-|-|Retorna o maior elemento na coleção, em comparação com o uso de [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) operador.|
|maxBy|(N)|(N)|(N)|-|-|Retorna o maior elemento na coleção, comparada usando [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) sobre o resultado da função.|
|maxElement|-|-|-|-|O (log N)|Retorna o maior elemento no conjunto de acordo com a ordem que é usado para o conjunto.|
|min|(N)|(N)|(N)|-|-|Retorna o menor elemento na coleção, em comparação com o uso de [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) operador.|
|minBy|(N)|(N)|(N)|-|-|Retorna o menor elemento na coleção, em comparação com o uso de [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) operador sobre o resultado da função.|
|minElement|-|-|-|-|O (log N)|Retorna o elemento mais baixo no conjunto de acordo com a ordem que é usado para o conjunto.|
|ofArray|-|(N)|O(1)|(N)|(N)|Cria uma coleção que contém os mesmos elementos que a matriz fornecida.|
|ofList|(N)|-|O(1)|(N)|(N)|Cria uma coleção que contém os mesmos elementos que a lista fornecida.|
|ofSeq|(N)|(N)|-|(N)|(N)|Cria uma coleção que contém os mesmos elementos que a sequência de determinado.|
|Pairwise|-|-|(N)|-|-|Retorna uma sequência de cada elemento na sequência de entrada e seu antecessor, exceto o primeiro elemento, que é retornado somente como o predecessor do segundo elemento.|
|partition|(N)|(N)|-|(N)|(N)|Divide a coleção em duas coleções. A primeira coleção contém os elementos para o qual o predicado em questão retorna `true`, e a segunda coleção contém os elementos para o qual o predicado em questão retorna `false`.|
|permute|(N)|(N)|-|-|-|Retorna uma matriz com todos os elementos permutados de acordo com a permutação especificada.|
|Escolher|(N)|(N)|(N)|O (log N)|-|Aplica-se a função fornecida para elementos sucessivos, retornando o primeiro resultado em que a função retorna alguns. Se a função nunca retorna, `System.Collections.Generic.KeyNotFoundException` é gerado.|
|readonly|-|-|(N)|-|-|Cria um objeto de sequência que delega para o objeto de sequência de determinado. Esta operação garante que uma conversão de tipo não é possível redescobrir e modificar a sequência original. Por exemplo, se uma matriz de dados, a sequência retornada retornará os elementos da matriz, mas você não pode converter o objeto de sequência retornado para uma matriz.|
|reduce|(N)|(N)|(N)|-|-|Aplica uma função para cada elemento da coleção, um argumento acumulador por meio da computação de threading. Essa função é iniciado, aplicando a função para os primeiros dois elementos, passa esse resultado para a função junto com o terceiro elemento e assim por diante. A função retorna o resultado final.|
|reduceBack|(N)|(N)|-|-|-|Aplica uma função para cada elemento da coleção, um argumento acumulador por meio da computação de threading. Se a função de entrada é f e os elementos são i0... no, essa função calcula f i0 (... (f na-1)).|
|remove|-|-|-|O (log N)|O (log N)|Remove um elemento de domínio do mapa. Nenhuma exceção é gerada se o elemento não estiver presente.|
|Replicar|-|(N)|-|-|-|Cria uma lista de um comprimento especificado com cada elemento definido como o valor especificado.|
|Rev|(N)|(N)|-|-|-|Retorna uma nova lista com os elementos na ordem inversa.|
|verificação|(N)|(N)|(N)|-|-|Aplica uma função para cada elemento da coleção, um argumento acumulador por meio da computação de threading. Essa operação se aplica a função para o segundo argumento e o primeiro elemento da lista. A operação, em seguida, passa esse resultado para a função junto com o segundo elemento e assim por diante. Por fim, a operação retorna a lista de resultados intermediários e o resultado final.|
|scanBack|(N)|(N)|-|-|-|Assemelha-se a operação de foldBack mas retorna os resultados intermediários e finais.|
|Singleton|-|-|O(1)|-|O(1)|Retorna uma sequência que gera apenas um item.|
|set|O(1)|-|-|-|-|Define um elemento de uma matriz para o valor especificado.|
|skip|-|-|(N)|-|-|Retorna uma sequência que ignora elementos N da sequência de base e, em seguida, gera os elementos restantes da sequência.|
|skipWhile|-|-|(N)|-|-|Retorna uma sequência que, quando iteradas, ignora elementos da sequência de subjacente enquanto o determinado retorna predicado `true` e, em seguida, gera os elementos restantes da sequência.|
|sort|Média do (log de N N)<br /><br />O(N^2) pior caso|O (log de N N)|O (log de N N)|-|-|Classifica a coleção por valor do elemento. Elementos são comparados usando [comparar](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortBy|Média do (log de N N)<br /><br />O(N^2) pior caso|O (log de N N)|O (log de N N)|-|-|Classifica a lista fornecida usando chaves que fornece a projeção determinada. As chaves são comparadas usando [comparar](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlace|Média do (log de N N)<br /><br />O(N^2) pior caso|-|-|-|-|Classifica os elementos de uma matriz a mutação em vigor e usando a função de comparação especificado. Elementos são comparados usando [comparar](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceBy|Média do (log de N N)<br /><br />O(N^2) pior caso|-|-|-|-|Classifica os elementos de uma matriz a mutação em vigor e usando a projeção fornecida para as chaves. Elementos são comparados usando [comparar](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceWith|Média do (log de N N)<br /><br />O(N^2) pior caso|-|-|-|-|Classifica os elementos de uma matriz a mutação em vigor e usando a função de comparação fornecido como a ordem.|
|sortWith|Média do (log de N N)<br /><br />O(N^2) pior caso|O (log de N N)|-|-|-|Classifica os elementos de uma coleção, usando a função de comparação fornecido como a ordem e retornando uma nova coleção.|
|sub|(N)|-|-|-|-|Cria uma matriz que contém subintervalo determinado iniciando o índice e o comprimento especificado.|
|sum|(N)|(N)|(N)|-|-|Retorna a soma dos elementos na coleção.|
|sumBy|(N)|(N)|(N)|-|-|Retorna a soma dos resultados que são gerados, aplicando a função para cada elemento da coleção.|
|Final|-|O(1)|-|-|-|Retorna a lista sem o primeiro elemento.|
|Take|-|-|(N)|-|-|Retorna os elementos da sequência de até uma contagem especificada.|
|takeWhile|-|-|O(1)|-|-|Retorna uma sequência que, quando iteradas, produz elementos da sequência de subjacente enquanto o determinado retorna predicado `true` e, em seguida, retorna não mais elementos.|
|ToArray|-|(N)|(N)|(N)|(N)|Cria uma matriz de determinada coleção.|
|ToList|(N)|-|(N)|(N)|(N)|Cria uma lista de determinada coleção.|
|toSeq|O(1)|O(1)|-|O(1)|O(1)|Cria uma sequência de determinada coleção.|
|Truncar|-|-|O(1)|-|-|Retorna uma sequência que, quando enumerada, retorna não mais de N elementos.|
|tryFind|(N)|(N)|(N)|O (log N)|-|Pesquisa um elemento que satisfaz um predicado em questão.|
|tryFindIndex|(N)|(N)|(N)|-|-|Procura o primeiro elemento que atende um predicado em questão e retorna o índice do elemento correspondente, ou `None` se esse elemento não existe.|
|tryFindKey|-|-|-|O (log N)|-|Retorna a chave do primeiro mapeamento da coleção que satisfaz o predicado especificado ou retorna `None` se esse elemento não existe.|
|tryPick|(N)|(N)|(N)|O (log N)|-|Aplica-se a função fornecida para elementos sucessivos, retornando o primeiro resultado em que a função retorna `Some` para algum valor. Se esse elemento não existe, a operação retorna `None`.|
|Desdobrar|-|-|(N)|-|-|Retorna uma sequência que contém os elementos que gera a computação determinada.|
|union|-|-|-|-|O (M &#42; log N)|Calcula a união de dois conjuntos.|
|unionMany|-|-|-|-|O (N1 &AMP;#42; N2...)|Calcula a união de uma sequência de conjuntos.|
|unzip|(N)|(N)|(N)|-|-|Uma lista de pares é dividida em duas listas.|
|unzip3|(N)|(N)|(N)|-|-|Uma lista de triplos é dividida em três listas.|
|em janelas|-|-|(N)|-|-|Retorna uma sequência que gera janelas deslizantes do que contém elementos que são desenhados de sequência de entrada. Cada janela é retornada como uma nova matriz.|
|CEP|(N)|(N)|(N)|-|-|Combina duas coleções em uma lista de pares. As duas listas devem ter tamanhos iguais.|
|zip3|(N)|(N)|(N)|-|-|Combina três coleções em uma lista de triplos. A lista deve ter tamanhos iguais.|

## <a name="see-also"></a>Consulte também
[Tipos F#](fsharp-types.md)

[Referência da Linguagem F#](index.md)

