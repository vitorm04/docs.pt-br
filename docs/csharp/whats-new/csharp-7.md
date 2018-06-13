---
title: Novidades no C# 7.0 – Guia do C#
description: Obtenha uma visão geral dos novos recursos que virão na futura versão 7 da linguagem C#.
ms.date: 12/21/2016
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: a78b30411d734d6dadc52b7dbd402763d4eb7f5e
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956403"
---
# <a name="whats-new-in-c-70"></a>Novidades no C# 7.0

O C# 7.0 adiciona vários recursos novos à linguagem C#:
* [Variáveis `out`](#out-variables)
    - Você pode declarar valores `out` embutidos como argumentos para o método em que eles são usados.
* [Tuplas](#tuples)
    - Você pode criar tipos simples e sem nome que contêm vários campos públicos. Compiladores e ferramentas IDE entendem a semântica desses tipos.
* [Descarta](#discards)
    - Descartes são variáveis temporárias de somente gravação usadas em atribuições quando o valor atribuído não tem importância. Elas são particularmente úteis ao desconstruir tuplas e tipos definidos pelo usuário, bem como ao chamar métodos com parâmetros `out`.
* [Correspondência Padrão](#pattern-matching)
    - Você pode criar a lógica de ramificação com base em tipos e valores arbitrários dos membros desses tipos.
* [locais e retornos de `ref`](#ref-locals-and-returns)
    - Argumentos de método e variáveis locais podem ser referências a outros armazenamentos.
* [Funções Locais](#local-functions)
    - Você pode aninhar funções dentro de outras funções para limitar seu escopo e visibilidade.
* [Mais membros aptos para expressão](#more-expression-bodied-members)
    - A lista de membros que podem ser criados usando expressões cresceu.
* [Expressões `throw`](#throw-expressions)
    - Você pode lançar exceções em construções de código que anteriormente não eram permitidas porque `throw` era uma instrução. 
* [Tipos de retorno assíncrono generalizado](#generalized-async-return-types)
    - Os métodos declarados com o modificador `async` podem retornar outros tipos além de `Task` e `Task<T>`.
* [Aprimoramentos da sintaxe de literais numéricos](#numeric-literal-syntax-improvements)
    - Novos tokens aprimoram a legibilidade para constantes numéricas.

O restante deste tópico aborda cada um dos recursos. Para cada recurso, você aprenderá o raciocínio por trás dele. Você aprenderá a sintaxe. Você verá alguns cenários de exemplo em que o uso do novo recurso o tornará mais produtivos como desenvolvedor. 

## <a name="out-variables"></a>Variáveis `out`

A sintaxe existente que dá suporte a parâmetros `out` foi aperfeiçoada nesta versão.  

Anteriormente, você precisaria separar a declaração da variável out e sua inicialização em duas instruções diferentes:

[!code-csharp[OutVariableOldStyle](../../../samples/snippets/csharp/new-in-7/program.cs#03_OutVariableOldStyle "classic out variable declaration")]

Agora você pode declarar variáveis `out` na lista de argumentos de uma chamada de método, em vez de escrever uma instrução de declaração separada:

[!code-csharp[OutVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#01_OutVariableDeclarations "Out variable declarations")]

Você talvez queira especificar o tipo da variável `out` para maior clareza, conforme mostrado acima. No entanto, a linguagem dá suporte ao uso de variável local de tipo implícito:

[!code-csharp[OutVarVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#02_OutVarVariableDeclarations "Implicitly typed Out variable")]

* O código é mais fácil de ler. 
    - Você declara a variável out onde a usa, não em outra linha acima.
* Não é necessário atribuir um valor inicial.
    - Ao declarar a variável `out` onde ela é usada em uma chamada de método, você não pode usá-la acidentalmente antes de ela ser atribuída.

O uso mais comum para esse recurso será o padrão `Try`. Nesse padrão, um método retorna um `bool` indicando êxito ou falha e uma variável `out` que fornece o resultado se o método tiver êxito.

Ao usar a declaração de variável `out`, a variável declarada "vaza" no escopo externo da instrução if. Isso permite que você use a variável posteriormente:

```csharp
if (!int.TryParse(input, out int result))
{    
    return null;
}

return result;
```

## <a name="tuples"></a>Tuplas

> [!NOTE]
> Os novos recursos de tuplas exigem os tipos <xref:System.ValueTuple>.
> Você deve adicionar o pacote NuGet [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) para usá-lo em plataformas que não incluem os tipos.
>
> Isso é semelhante a outros recursos de linguagem que dependem de tipos entregues no framework. Os exemplos incluem `async` e `await` que dependem da interface `INotifyCompletion`, além do LINQ que depende de `IEnumerable<T>`. No entanto, o mecanismo de entrega está mudando conforme o .NET se torna mais independente de plataforma. O .NET Framework pode não ser enviados sempre na mesma cadência que o compilador de linguagem. Quando novos recursos de linguagem dependerem de novos tipos, esses tipos estarão disponíveis como pacotes do NuGet quando os recursos de linguagem forem enviados. Conforme esses novos tipos são adicionados à API padrão do .NET e fornecidos como parte do framework, o requisito de pacote do NuGet será removido.

O C# fornece uma sintaxe avançada para classes e structs que são usados para explicar a intenção do design. Mas, às vezes, essa sintaxe avançada requer trabalho adicional com poucas vantagens. Geralmente, você pode escrever métodos que precisam de uma estrutura simples que contém mais de um elemento de dados. Para dar suporte a esses cenários foram adicionadas *tuplas* ao C#. As tuplas são estruturas de dados leves que contêm vários campos para representar os membros de dados.
Os campos não são validados e você não pode definir seus próprios métodos

> [!NOTE]
> As tuplas estavam disponíveis antes do C# 7.0, mas elas eram ineficientes e não tinham nenhum suporte de linguagem.
> Isso significava que os elementos de tupla só podiam ser referenciados como `Item1`, `Item2` e assim por diante. O C# 7.0 introduz o suporte de linguagem para tuplas, que permite nomes semânticos para os campos de uma tupla, usando tipos de tupla novos e mais eficientes.

Crie uma tupla atribuindo um valor a cada membro:

[!code-csharp[UnnamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#04_UnnamedTuple "Unnamed tuple")]

A atribuição cria uma tupla cujos membros são `Item1` e `Item2`, que podem ser usados da mesma forma que <xref:System.Tuple>. Você pode alterar a sintaxe para criar uma tupla que fornece nomes semânticos para cada um dos membros da tupla:

[!code-csharp[NamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#05_NamedTuple "Named tuple")]

A tupla `namedLetters` contém campos denominados `Alpha` e `Beta`. Esses nomes existem somente em tempo de compilação e não são preservados, por exemplo, ao inspecionar a tupla usando a reflexão em tempo de execução.

Em uma atribuição de tupla, você também pode especificar os nomes dos campos no lado direito da atribuição:

[!code-csharp[ImplicitNamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#06_ImplicitNamedTuple "Implicitly named tuple")]

Você pode especificar nomes para os campos no lado esquerdo e direito da atribuição:

[!code-csharp[NamedTupleConflict](../../../samples/snippets/csharp/new-in-7/program.cs#07_NamedTupleConflict "Named tuple conflict")]

A linha acima gera um aviso, `CS8123`, informando que os nomes no lado direito da atribuição, `Alpha` e `Beta`, são ignorados porque eles estão em conflito com os nomes no lado esquerdo, `First` e `Second`.

Os exemplos acima mostram a sintaxe básica para declarar tuplas. As tuplas são mais úteis como tipos de retorno para os métodos `private` e `internal`. As tuplas fornecem uma sintaxe simples para esses métodos retornarem vários valores distintos: salve o trabalho de criação de um `class` ou um `struct` que define o tipo retornado. Não é necessário criar um novo tipo.

Criar uma tupla é mais eficiente e produtivo.
É uma sintaxe mais simples e leve para definir uma estrutura de dados que contém mais de um valor. O método de exemplo a seguir retorna os valores mínimo e máximo encontrados em uma sequência de inteiros:

[!code-csharp[TupleReturningMethod](../../../samples/snippets/csharp/new-in-7/program.cs#08_TupleReturningMethod "Tuple returning method")]

Usar tuplas dessa maneira oferece várias vantagens:

* Você salva o trabalho de criação de um `class` ou um `struct` que define o tipo retornado. 
* Você não precisa criar um novo tipo.
* Os aprimoramentos de linguagem removem a necessidade de chamar os métodos <xref:System.Tuple.Create``1(``0)>.

A declaração do método fornece os nomes dos campos da tupla que é retornada. Quando você chama o método, o valor retornado é uma tupla cujos campos são `Max` e `Min`:

[!code-csharp[CallingTupleMethod](../../../samples/snippets/csharp/new-in-7/program.cs#09_CallingTupleMethod "Calling a tuple returning method")]

Pode haver ocasiões em que você deseja descompactar os membros de uma tupla que foram retornados de um método.  Você pode fazer isso declarando variáveis separadas para cada um dos valores na tupla. Isso é chamado de *desconstruir* a tupla:

[!code-csharp[CallingWithDeconstructor](../../../samples/snippets/csharp/new-in-7/program.cs#10_CallingWithDeconstructor "Deconstructing a tuple")]

Você também pode fornecer uma desconstrução semelhante para qualquer tipo no .NET. Isso é feito escrevendo um método `Deconstruct` como um membro da classe. esse método `Deconstruct` fornece um conjunto de argumentos `out` para cada uma das propriedades que você deseja extrair. Considere essa classe `Point` que fornece um método desconstrutor que extrai as coordenadas `X` e `Y`:

[!code-csharp[PointWithDeconstruction](../../../samples/snippets/csharp/new-in-7/point.cs#11_PointWithDeconstruction "Point with deconstruction method")]
 
Extraia os campos individuais atribuindo um `Point` a uma tupla:

[!code-csharp[DeconstructPoint](../../../samples/snippets/csharp/new-in-7/program.cs#12_DeconstructPoint "Deconstruct a point")]

Você não está vinculado aos nomes definidos no método `Deconstruct`. Você pode renomear as variáveis de extração como parte da atribuição:  

[!code-csharp[DeconstructNames](../../../samples/snippets/csharp/new-in-7/program.cs#13_DeconstructNames "Deconstruct with new names")]

Você pode aprender sobre tuplas de forma mais aprofundada no [tópico sobre tuplas](../tuples.md).

## <a name="discards"></a>Descartes

Geralmente, ao desconstruir uma tupla ou chamar um método com parâmetros `out`, você é forçado a definir uma variável cujo valor não é importante e você não pretende usar. O C# adiciona suporte para *descartes* para lidar com esse cenário. Um descarte é uma variável de somente gravação cujo nome é `_` (o caractere de sublinhado); você pode atribuir todos os valores que você pretende descartar à variável única. Um descarte é como uma variável não atribuída. Além da instrução de atribuição, o descarte não pode ser usado no código.

Os descartes são compatíveis com os seguintes cenários:

* Ao desconstruir tuplas ou tipos definidos pelo usuário.

* Ao chamar métodos com parâmetros [out](../language-reference/keywords/out-parameter-modifier.md).

* Em uma operação de correspondência de padrões com as instruções [is](../language-reference/keywords/is.md) e [switch](../language-reference/keywords/switch.md).

* Como um identificador autônomo quando você deseja identificar explicitamente o valor de uma atribuição como um descarte.

O exemplo a seguir define um método `QueryCityDataForYears` que retorna uma tupla de 6 que contém dados de dois anos diferentes para uma cidade. A chamada do método no exemplo é relacionada somente com os dois valores de população retornados pelo método e, por isso, trata os valores restantes na tupla como descartes ao desconstruir a tupla.

[!code-csharp[Tuple-discard](../../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Para obter mais informações, consulte [Descartes](../discards.md).
 
## <a name="pattern-matching"></a>Correspondência de padrões

*Correspondência de padrões* é um recurso que permite que você implemente a expedição do método em propriedades diferentes do tipo de um objeto. Você provavelmente já está familiarizado com a expedição de método com base no tipo de um objeto. Em programação orientada a objetos, os métodos de substituição e virtual fornecem a sintaxe da linguagem para implementar a expedição de método com base em um tipo de objeto. As classes base e derivada fornecem implementações diferentes. Expressões de correspondência de padrões estendem esse conceito para que você possa implementar facilmente padrões de expedição semelhantes para elementos de dados e tipos que não são relacionados por meio de uma hierarquia de herança. 

A correspondência de padrões tem suporte a expressões `is` e `switch`. Cada uma delas permite inspecionar um objeto e suas propriedades para determinar se esse objeto satisfaz o padrão procurado. Você usa a palavra-chave `when` para especificar regras adicionais para o padrão.

### <a name="is-expression"></a>Expressão `is`

A expressão de padrão `is` estende o operador familiar `is` para consultar um objeto além de seu tipo.

Vamos começar com um cenário simples. Vamos adicionar recursos a este cenário que demonstram como expressões de correspondência de padrões tornam algoritmos que funcionam com tipos não relacionados fáceis. Começaremos com um método que calcula a soma de uma série de rolagens de dado:

[!code-csharp[SumDieRolls](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#14_SumDieRolls "Sum die rolls")]

Você pode pensar rapidamente que precisa localizar a soma dos lançamentos de dado em que alguns dos lançamentos são feitos com vários dados (dados é plural de dado). Parte da sequência de entrada pode ser vários resultados, em vez de um único número:

[!code-csharp[SumDieRollsWithGroups](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#15_SumDieRollsWithGroups "Sum die rolls with groups")]

A expressão padrão `is` funciona muito bem nesse cenário. Como parte da verificação de tipo, você escreve uma inicialização de variável. Isso cria uma nova variável do tipo de tempo de execução validado.

Conforme você continua a expandir esses cenários, pode descobrir que cria mais instruções `if` e `else if`. Assim que isso se tornar complicado, provavelmente você desejará mudar para expressões padrão `switch`.

### <a name="switch-statement-updates"></a>Atualizações da instrução `switch`

A *expressão de correspondência* tem uma sintaxe familiar, com base na instrução `switch` que já faz parte da linguagem C#. Vamos converter o código existente para usar uma expressão de correspondência antes de adicionar novas expressões case: 

[!code-csharp[SumUsingSwitch](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#16_SumUsingSwitch "Sum using switch")]

As expressões de correspondência têm uma sintaxe ligeiramente diferente das expressões `is`, em que você declara o tipo e a variável no início da expressão `case`.

As expressões de correspondência também dão suporte a constantes. Isso pode poupar tempo ao fatorar expressões case simples:

[!code-csharp[SwitchWithConstants](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#17_SwitchWithConstants "Switch with constants")]

O código acima adiciona expressões case de `0` como um case especial de `int` e `null` como um case especial quando não há nenhuma entrada. Isso demonstra um novo recurso importante em expressões de padrão switch: a ordem das expressões `case` agora importa. O case `0` deve aparecer antes do case `int` geral. Caso contrário, o primeiro padrão a ser correspondido seria o case `int`, mesmo quando o valor fosse `0`. Se você acidentalmente ordenar expressões de correspondência de forma que uma expressão posterior já tenha sido tratada, o compilador sinalizará isso e gerará um erro.

Esse mesmo comportamento habilita o case especial para uma sequência de entrada vazia.
Você pode ver que o case de um item `IEnumerable` que tem elementos deve aparecer antes do case `IEnumerable` geral.

Esta versão também adicionou um case `default`. O case `default` sempre é avaliado por último, independentemente da ordem em que ele aparece na origem. Por esse motivo, a convenção é colocar o case `default` por último.

Por fim, vamos adicionar um último `case` para um novo estilo de dado. Alguns jogos usam dados de percentil para representar intervalos maiores de números. 

> [!NOTE]
> Dois dados de percentil de 10 faces podem representar todos os números de 0 a 99. Um dado tem os lados rotulados como `00`, `10`, `20`,... `90`. O outro dado tem os lados rotulados como `0`, `1`, `2`,... `9`. Some os valores dos dois dados e você pode obter todos os números de 0 a 99.

Para adicionar esse tipo de dado à sua coleção, primeiro defina um tipo para representar os dados do percentil. A propriedade `TensDigit` armazena valores `0`, `10`, `20`, até `90`:

[!code-csharp[18_PercentileDice](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#18_PercentileDice "Percentile Die type")]

Em seguida, adicione uma expressão de correspondência `case` para o novo tipo:

[!code-csharp[SwitchWithNewTypes](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#19_SwitchWithNewTypes "Include Percentile Die type")]

A nova sintaxe para expressões de correspondência de padrões torna mais fácil criar algoritmos de expedição com base no tipo de um objeto ou outras propriedades, usando uma sintaxe clara e concisa. Expressões de correspondência de padrões permitem esses constructos em tipos de dados que não são relacionados por herança.

Você pode aprender mais sobre a correspondência de padrões no tópico dedicado à [correspondência de padrões no C#](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Locais e retornos de ref

Esse recurso permite que os algoritmos que usam e retornam referências para as variáveis definidas em outro lugar. Um exemplo é trabalhar com matrizes grandes e localizar um único local com determinadas características. Um método retornaria os dois índices para um único local na matriz:

[!code-csharp[FindReturningIndices](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#20_FindReturningIndices "Find returning indices")]

Há muitos problemas com esse código. Em primeiro lugar, ele é um método público que está retornando uma tupla. A linguagem dá suporte a isso, mas tipos definidos pelo usuário (classes ou estruturas) são preferenciais para APIs públicas.

Em segundo lugar, esse método está retornando os índices para o item na matriz.
Isso leva os chamadores a escreverem um código que usa esses índices para desreferenciar a matriz e modificar um único elemento:

[!code-csharp[UpdateItemFromIndices](../../../samples/snippets/csharp/new-in-7/program.cs#21_UpdateItemFromIndices "Update Item From Indices")]

Você prefere escrever um método que retorna uma *referência* para o elemento da matriz que deseja alterar. Você apenas poderia fazer isso usando código não seguro e retornando um ponteiro para um `int` em versões anteriores.

Vamos examinar uma série de alterações para demonstrar o recurso local de ref e mostrar como criar um método que retorna uma referência ao armazenamento interno.
Ao longo do caminho, você aprenderá as regras do recurso de retorno de ref e local de ref que impedem que você acidentalmente o use de maneira indevida.

Comece modificando a declaração do método `Find` para que ele retorne um `ref int` em vez de uma tupla. Em seguida, modifique a instrução return para que ela retorne o valor armazenado na matriz em vez de dois índices:

```csharp
// Note that this won't compile. 
// Method declaration indicates ref return,
// but return statement specifies a value return.
public static ref int Find2(int[,] matrix, Func<int, bool> predicate)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
        for (int j = 0; j < matrix.GetLength(1); j++)
            if (predicate(matrix[i, j]))
                return matrix[i, j];
    throw new InvalidOperationException("Not found");
}
```

Quando você declara que um método retorna uma variável `ref`, você também deve adicionar a palavra-chave `ref` a cada instrução return. Isso indica o retorno pela referência e ajuda os desenvolvedores lendo o código posteriormente a lembrarem que o método retorna pela referência:

[!code-csharp[FindReturningRef](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#22_FindReturningRef "Find returning by reference")]

Agora que o método retorna uma referência para o valor inteiro na matriz, você precisa modificar onde ele é chamado.  A declaração `var` significa que `valItem` é agora um `int` em vez de uma tupla:

[!code-csharp[AssignRefReturnToValue](../../../samples/snippets/csharp/new-in-7/program.cs#23_AssignRefReturnToValue "Assign ref return to value")]

A segunda instrução `WriteLine` no exemplo acima imprime o valor `42`, não `24`. A variável `valItem` é um `int`, não um `ref int`. A palavra-chave `var` permite que o compilador especifique o tipo, mas não adiciona implicitamente o modificador `ref`. Em vez disso, o valor referenciado pelo `ref return` é *copiado* para a variável no lado esquerdo da atribuição. A variável não é um local de `ref`.

Para obter o resultado desejado, você precisa adicionar o modificador `ref` à declaração de variável local para tornar a variável em uma referência quando o valor retornado é uma referência:

[!code-csharp[AssignRefReturn](../../../samples/snippets/csharp/new-in-7/program.cs#24_AssignRefReturn "Assign ref return")]

Agora, a segunda instrução `WriteLine` no exemplo acima imprimirá o valor `24`, indicando que o armazenamento da matriz foi modificado. A variável local foi declarada com um modificador `ref` e ele levará um retorno de `ref`. Você deve inicializar uma variável `ref` quando ela é declarada, não é possível dividir a declaração e a inicialização.

A linguagem C# tem outras três regras que protegem contra o uso indevido de locais e retornos de `ref`:

* Não é possível atribuir um valor retornado do método padrão a uma variável local de `ref`.
    - Isso proíbe que instruções como `ref int i = sequence.Count();`
* Você não pode retornar um `ref` para uma variável cujo tempo de vida não ultrapassa a execução do método.
    - Isso significa que você não pode retornar uma referência a uma variável local ou uma variável com escopo semelhante.
* O locais e retornos de `ref` não podem ser usados com métodos assíncronos.
    - O compilador não consegue saber se a variável referenciada foi definida com o valor final quando o método assíncrono retorna.

A adição de locais de ref e retornos de ref habilita algoritmos que são mais eficientes evitando copiar valores ou executar operações de desreferenciamento várias vezes. 

## <a name="local-functions"></a>Funções locais

Muitos designs para classes incluem métodos que são chamados de apenas um local. Esses métodos privados adicionais mantêm cada método pequeno e focado. No entanto, eles podem tornar mais difícil de entender uma classe ao lê-lo pela primeira vez. Esses métodos devem ser compreendidos fora do contexto do local de chamada único.

Para esses designs, as *funções locais* permitem que você declare métodos dentro do contexto de outro método. Isso faz com que seja mais fácil para os leitores da classe verem que o método local é chamado apenas do contexto em que ele está declarado.

Há dois casos de uso muito comuns para funções locais: métodos iteradores públicos e métodos assíncronos públicos. Ambos os tipos de métodos de geram código que relata os erros mais tarde do que os programadores podem esperar. No caso de métodos iteradores, todas as exceções são observadas apenas ao chamar o código que enumera a sequência retornada. No caso de métodos assíncronos, todas as exceções são observadas apenas quando a `Task` retornada é aguardada.

Vamos começar com um método iterador:

[!code-csharp[IteratorMethod](../../../samples/snippets/csharp/new-in-7/Iterator.cs#25_IteratorMethod "Iterator method")]

Examine o código abaixo que chama o método iterador incorretamente:

[!code-csharp[CallIteratorMethod](../../../samples/snippets/csharp/new-in-7/program.cs#26_CallIteratorMethod "Call iterator method")]

A exceção é lançada quando `resultSet` é iterado, não quando `resultSet` é criado.
Neste exemplo independente, a maioria dos desenvolvedores pode diagnosticar o problema rapidamente. No entanto, em bases de código maiores, o código que cria um iterador geralmente não é tão próximo do código que enumera o resultado. Você pode refatorar o código para que o método público valide todos os argumentos e um método particular gere a enumeração:

[!code-csharp[IteratorMethodRefactored](../../../samples/snippets/csharp/new-in-7/Iterator.cs#27_IteratorMethodRefactored "Iterator method refactored")]

Esta versão refatorada lançará exceções imediatamente porque o método público não é um método iterador, apenas o método privado usa a sintaxe `yield return`. No entanto, existem problemas potenciais com a refatoração. O método privado deve ser chamado apenas do método de interface pública, pois, caso contrário, todas as validações de argumento são ignoradas.
Os leitores da classe devem descobrir esse fato lendo a classe inteira e pesquisando por todas as outras referências ao método `alphabetSubsetImplementation`.

Você pode tornar essa intenção de design mais clara declarando o `alphabetSubsetImplementation` como uma função local dentro do método de API pública:

[!code-csharp[22_IteratorMethodLocal](../../../samples/snippets/csharp/new-in-7/Iterator.cs#28_IteratorMethodLocal "Iterator method with local function")]

A versão acima deixa claro que o método local é referenciado somente no contexto do método externo. As regras para funções locais também garantem que um desenvolvedor não possa acidentalmente chamar a função local de outro local na classe e ignorar a validação de argumento.

A mesma técnica pode ser empregada com métodos `async` para garantir que as exceções decorrentes da validação de argumento sejam lançadas antes de o trabalho assíncrono começar:

[!code-csharp[TaskExample](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

> [!NOTE]
> Alguns dos designs com suporte pelas funções locais também podem ser feitos usando *expressões lambda*. Os interessados podem [ler mais sobre as diferenças](../local-functions-vs-lambdas.md)

## <a name="more-expression-bodied-members"></a>Mais membros aptos para expressão

O C# 6 introduziu [membros aptos para expressão](csharp-6.md#expression-bodied-function-members) para funções de membro e propriedades somente leitura. O C# 7.0 expande os membros permitidos que podem ser implementados como expressões. No C# 7.0, você pode implementar *construtores*, *finalizadores* e acessadores `get` e `set` em *propriedades* e *indexadores*. O código a seguir mostra exemplos de cada um:

[!code-csharp[ExpressionBodiedMembers](../../../samples/snippets/csharp/new-in-7/expressionmembers.cs#36_ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Este exemplo não precisa de um finalizador, mas ele é mostrado para demonstrar a sintaxe. Você não deve implementar um finalizador em sua classe a menos que seja necessário para liberar recursos não gerenciados. Você também deve considerar o uso da classe <xref:System.Runtime.InteropServices.SafeHandle> em vez de gerenciar recursos não gerenciados diretamente.

Esses novos locais para membros aptos para expressão representam uma etapa importante para a linguagem C#: esses recursos foram implementados por membros da comunidade trabalhando no projeto [Roslyn](https://github.com/dotnet/Roslyn) de software livre.

## <a name="throw-expressions"></a>Expressões throw

No C#, `throw` sempre foi uma instrução. Como `throw` é uma instrução, não uma expressão, havia constructos C# em que não era possível usá-la. Eles incluíam expressões condicionais, expressões de união nulas e algumas expressões lambda. A adição de membros aptos para expressão inclui mais locais em que as expressões `throw` seriam úteis. Para que você possa escrever qualquer um desses constructos, o C# 7.0 apresenta *expressões throw*.

A sintaxe é a mesma que você sempre usou para instruções `throw`. A única diferença é que agora você pode colocá-los em novas localidades, como em uma expressão condicional:

[!code-csharp[Throw_ExpressionExample](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#37_Throw_ExpressionExample "conditional throw expressions")]

Esse recurso permite usar expressões throw em expressões de inicialização:

[!code-csharp[ThrowInInitialization](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#38_ThrowInInitialization "conditional throw expressions")]

Anteriormente, essas inicializações precisavam estar em um construtor, com as instruções throw no corpo do construtor:


[!code-csharp[ThrowInConstructor](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#39_ThrowInConstructor "throw statements")]

> [!NOTE]
> Ambos os construtores acima farão com que exceções sejam geradas durante a construção de um objeto. Muitas vezes é difícil realizar a recuperação deles.
> Por esse motivo, os designs que lançam exceções durante a construção são desencorajados.

## <a name="generalized-async-return-types"></a>Tipos de retorno assíncrono generalizado

Retornar um objeto `Task` de métodos assíncronos pode introduzir gargalos de desempenho em determinados caminhos. `Task` é um tipo de referência, portanto, usá-lo significa alocar um objeto. Em casos em que um método declarado com o modificador `async` retorna um resultado armazenado em cache ou é concluído de forma síncrona, as alocações extras podem se tornar um custo de tempo significativo em seções críticas de desempenho de código. Ele poderá se tornar muito caro se essas alocações ocorrerem em loops rígidos.

O novo recurso de linguagem significa que os métodos assíncronos podem retornar outros tipos além de `Task`, `Task<T>` e `void`. O tipo retornado ainda deve satisfazer o padrão assíncrono, o que significa que um método `GetAwaiter` deve ser acessível. Como um exemplo concreto, o tipo `ValueTask` foi adicionado ao .NET Framework para usar esse novo recurso de linguagem: 

[!code-csharp[UsingValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#30_UsingValueTask "Using ValueTask")]

> [!NOTE]
> Você precisa adicionar o pacote NuGet [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) para usar o tipo <xref:System.Threading.Tasks.ValueTask%601>.

Uma otimização simples seria usar `ValueTask` em locais em que `Task` seria usado antes. No entanto, se você quiser executar otimizações adicionais manualmente, poderá armazenar em cache os resultados do trabalho assíncrono e reutilizar o resultado em chamadas subsequentes. O struct `ValueTask` tem um construtor com um parâmetro `Task` para que você possa construir um `ValueTask` do valor retornado de qualquer método assíncrono existente:

[!code-csharp[AsyncOptimizedValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#31_AsyncOptimizedValueTask "Return async result or cached value")]
 
Como com todas as recomendações de desempenho, você deve submeter a benchmark as duas versões antes de fazer alterações em grande escala em seu código.

## <a name="numeric-literal-syntax-improvements"></a>Aprimoramentos da sintaxe de literais numéricos

A leitura incorreta das constantes numéricas pode fazer com que seja difícil entender o código ao lê-lo pela primeira vez. Isso ocorre geralmente quando esses números são usados como máscaras de bits ou outros simbólicos em vez de valores numéricos. O C# 7.0 inclui dois novos recursos para facilitar a gravação de números da maneira mais legível possível para o uso pretendido: *literais binários* e *separadores de dígito*.

Para ocasiões em que você estiver criando máscaras de bits ou sempre que uma representação binária de um número torna o código mais legível, escreva esse número em binário:

[!code-csharp[BinaryConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#32_BinaryConstants "Binary constants")]

O `0b` no início da constante indica que o número é escrito como um número binário.

Números binários podem ficar muito longos, portanto, é mais fácil ver os padrões de bit introduzindo o `_` como um separador de dígitos:

[!code-csharp[ThousandSeparators](../../../samples/snippets/csharp/new-in-7/Program.cs#33_ThousandSeparators "Thousands separators")]

O separador de dígitos pode aparecer em qualquer lugar na constante. Para números de base 10, seria comum para usá-lo como um separador de milhar:

[!code-csharp[LargeIntegers](../../../samples/snippets/csharp/new-in-7/Program.cs#34_LargeIntegers "Large integer")]

O separador de dígitos pode ser usado com os tipos `decimal`, `float` e `double`:

[!code-csharp[OtherConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#35_OtherConstants "non-integral constants")]

Juntos, você pode declarar constantes numéricas com muito mais facilidade de leitura.
