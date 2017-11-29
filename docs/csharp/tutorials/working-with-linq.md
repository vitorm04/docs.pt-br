---
title: Trabalhando com LINQ
description: "Este tutorial ensina a gerar sequências com LINQ, escrever métodos para uso em consultas LINQ e diferenciar entre avaliação lenta e detalhada."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/28/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: ec86c558b9aa9c6269fcf9890978f61a934c081f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-linq"></a>Trabalhando com LINQ

## <a name="introduction"></a>Introdução

Este tutorial ensina vários recursos no .NET Core e da linguagem C#. Você aprenderá:

*   Como gerar sequências com LINQ
*   Como escrever métodos que podem ser facilmente usados em consultas LINQ.
*   Como distinguir entre uma avaliação lenta e uma detalhada.

Você aprenderá essas técnicas ao compilar um aplicativo que demonstra uma das habilidades básicas de qualquer mágico: o [embaralhamento faro](https://en.wikipedia.org/wiki/Faro_shuffle). Em resumo, um embaralhamento faro é uma técnica em que você divide um baralho de cartas exatamente na metade, então as cartas de cada metade são colocadas em ordem aleatória até recriar o conjunto original.

Os mágicos usam essa técnica porque cada carta é fica em um local conhecido após o embaralhamento e a ordem é um padrão de repetição. 

Para nossos propósitos, vamos examinar rapidamente as sequências de manipulação de dados. O aplicativo que você criará construirá um baralho de cartas e, em seguida, executará uma sequência de embaralhamento, sempre gravando a sequência de saída. Você também comparará a ordem atualizada com a ordem original.

Este tutorial tem várias etapas. Após cada etapa, você poderá executar o aplicativo e ver o progresso. Você também poderá ver o [exemplo concluído](https://github.com/dotnet/docs/blob/master/samples/csharp/getting-started/console-linq) no repositório dotnet/docs do GitHub. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Pré-requisitos

Você precisará configurar seu computador para executar o .NET Core. Você encontrará as instruções de instalação na página do [.NET Core](https://www.microsoft.com/net/core). Você pode executar esse aplicativo no Windows, Ubuntu Linux, OS X ou em um contêiner do Docker. Você precisará instalar o editor de código de sua preferência. As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma. No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.

## <a name="create-the-application"></a>Criar o aplicativo

A primeira etapa é criar um novo aplicativo. Abra um prompt de comando e crie um novo diretório para seu aplicativo. Torne ele o diretório atual. Digite o comando `dotnet new console` no prompt de comando. Isso cria os arquivos iniciais de um aplicativo "Olá, Mundo" básico.

Se você nunca usou C# antes, [este tutorial](console-teleprompter.md) explicará a estrutura de um programa C#. Você pode ler e, em seguida, voltar aqui para saber mais sobre o LINQ. 

## <a name="creating-the-data-set"></a>Criando o arquivo de dados

Vamos começar criando um baralho. Você fará isso usando uma consulta LINQ com duas fontes (uma para os quatro naipes, uma para os treze valores). Você combinará essas fontes em um baralho com 52 cartas. Uma instrução `Console.WriteLine` dentro de um loop `foreach` exibe as cartas.

Aqui está a consulta:

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

As várias cláusulas `from` produzem um `SelectMany`, que cria uma única sequência da combinação entre cada elemento na primeira sequência com cada elemento na segunda sequência. A ordem é importante para nossos objetivos. O primeiro elemento na primeira sequência de fonte (naipes) é combinado com cada elemento na segunda sequência (valores). Isso produz todas as treze cartas do primeiro naipe. Esse processo é repetido com cada elemento na primeira sequência (naipes). O resultado final é um baralho ordenado por naipes, seguido pelos valores.

Em seguida, você precisará compilar os métodos Suits() e Ranks(). Vamos começar com um conjunto muito simples de *métodos de iterador* que gera a sequência como um enumerável de cadeias de caracteres:

```csharp
static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

Esses dois métodos utilizam a sintaxe `yield return` para produzir uma sequência à medida que eles são executados. O compilador compila um objeto que implementa `IEnumerable<T>` e gera a sequência de cadeias de caracteres conforme solicitado.

Vá em frente e execute o exemplo que você criou neste momento. Ele exibirá todas as 52 cartas do baralho. Talvez seja muito útil executar esse exemplo em um depurador para observar como os métodos `Suits()` e `Values()` são executados. Você pode ver claramente que cada cadeia de caracteres em cada sequência é gerada apenas conforme o necessário.

![Janela de console mostrando o aplicativo gravando 52 cartas](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a>Manipulando a ordem

Em seguida, vamos criar um método de utilitário que pode executar o embaralhamento. A primeira etapa é dividir o baralho em dois. Os métodos `Take()` e `Skip()` que fazem parte das APIs do LINQ fornecem esse recurso para nós:

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

O método de embaralhamento não existe na biblioteca padrão, portanto você precisará escrever o seu. Esse novo método ilustra várias técnicas que você usará com programas baseados em LINQ. Vamos explicar cada parte do método em etapas.

A assinatura do método cria um *método de extensão*:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

Um método de extensão é um *método estático* de objetivo especial. Você pode ver a adição do modificador `this` no primeiro argumento para o método. Isso significa que você chama o método como se fosse um método de membro do tipo do primeiro argumento.

Os métodos de extensão podem ser declarados somente dentro de classes `static`, então vamos criar uma nova classe estática chamada `extensions` para essa funcionalidade. É necessário adicionar mais métodos de extensão nesse tutorial, e eles serão colocados na mesma classe.

Esta declaração de método também segue um idioma padrão no qual os tipos de entrada e saídas são `IEnumerable<T>`. Essa prática permite que os métodos LINQ sejam encadeados para executar consultas mais complexas.

```csharp
using System.Collections.Generic;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>
            (this IEnumerable<T> first, IEnumerable<T> second)
        {
            // implementation coming.
        }
    }
}
```

Você enumerará as duas sequências de uma vez, intercalando os elementos e criando um objeto.  Escrever um método LINQ que funciona com duas sequências exige que você compreenda como `IEnumerable` funciona.

A interface `IEnumerable` tem um método: `GetEnumerator()`. O objeto retornado por `GetEnumerator()` tem um método para mover para o próximo elemento e uma propriedade que recupera o elemento atual na sequência. Você usará esses dois membros para enumerar a coleção e retornar os elementos. Esse método de Intercalação será um método iterador, portanto, em vez de criar uma coleção e retornar a coleção, você usará a sintaxe `yield return` mostrada acima. 

Aqui está a implementação desse método:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Agora que você escreveu esse método, vá até o método `Main` e embaralhe uma vez:

```csharp
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a>Comparações

Vamos ver quantos embaralhamentos são necessários para colocar o baralho em sua ordem original. Você precisará escrever um método que determina se duas sequências são iguais. Depois de ter esse método, você precisará colocar o código de embaralhamento em um loop e verificar quando a apresentação estiver na ordem.

Escrever um método para determinar se as duas sequências são iguais deve ser simples. É uma estrutura semelhante para o método que você escreveu para embaralhar as cartas. Somente desta vez, em vez de o rendimento retornar cada elemento, você comparará os elementos correspondentes de cada sequência. Quando toda a sequência tiver sido enumerada, se os elementos corresponderem, as sequências serão as mesmas:

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Isso mostra uma segunda linguagem LINQ: métodos de terminal. Eles consideram uma sequência como entrada (ou, neste caso, duas sequências) e retornam um único valor escalar. Esses métodos, quando são usados, sempre são o método final de uma consulta. (Portanto, o nome). 

Você pode ver isso em ação ao usá-lo para determinar quando o baralho está em sua ordem original. Coloque o código de embaralhamento dentro de um loop e pare quando a sequência estiver em sua ordem original, aplicando o método `SequenceEquals()`. Você pode ver que esse sempre será o método final em qualquer consulta, porque ele retorna um valor único em vez de uma sequência:

```csharp
var times = 0;
var shuffle = startingDeck;

do
{
    shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    times++;
} while (!startingDeck.SequenceEquals(shuffle));

Console.WriteLine(times);
```

Execute o exemplo e veja como o baralho é reorganizado em cada embaralhamento até que ele retorne à sua configuração original após 8 iterações.

## <a name="optimizations"></a>Otimizações

O exemplo que você compilou até agora executa um *embaralhamento*, no qual as cartas superiores e inferiores permanecem as mesmas em cada execução. Vamos fazer uma alteração e executar um *embaralhamento completo*, no qual todas as 52 cartas trocam de posição. Para um embaralhamento completo, intercale o baralho para que a primeira carta da metade inferior metade se torna a primeira carta do baralho. Isso significa que a última carta na metade superior torna-se a carta inferior. Isso é apenas uma alteração de uma linha. Atualize a chamada de embaralhamento para alterar a ordem das metades superior e inferior do baralho:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Execute o programa novamente e você verá que leva 52 iterações para o baralho ser reordenado. Você também começará a observar algumas degradações de desempenho graves à medida que o programa continuar a ser executado.

Existem muitas razões para isso. Vamos analisar uma das principais causas: uso ineficiente de *avaliação lenta*.

Consultas LINQ são avaliadas lentamente. As sequências são geradas somente quando os elementos são solicitados. Geralmente, esse é o principal benefício do LINQ. No entanto, em uso como esse programa, isso causa um crescimento exponencial no tempo de execução.

O baralho original foi gerado usando uma consulta LINQ. Cada embaralhamento é gerado executando três consultas LINQ no baralho anterior. Todos eles são executados lentamente. Isso também significa que eles são executados novamente sempre que a sequência é solicitada. Ao obter a 52ª iteração, você estará regenerando o baralho original muitas e muitas vezes. Vamos escrever um log para demonstrar esse comportamento. Em seguida, você poderá corrigir isso.

Este é um método de log que pode ser anexado a qualquer consulta para marcar a consulta executada.

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

Em seguida, instrumente a definição de cada consulta com uma mensagem de log:

```csharp
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        shuffle = shuffle.Skip(26)
            .LogQuery("Bottom Half")
            .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
            .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

Observe que você não precisa fazer o registro sempre que acessar uma consulta. Você faz o registro ao criar a consulta original. O programa ainda leva muito tempo para ser executado, mas agora você pode ver o motivo. Se você cansar de embaralhar externamente com o log ativado, mude de volta para o embaralhamento interno. Você ainda verá os efeitos da avaliação lenta. Em uma execução, ele faz 2592 consultas, incluindo a geração de todos os valores e naipes.

Há uma maneira fácil de atualizar este programa para evitar todas essas execuções. Há métodos LINQ `ToArray()` e `ToList()` que causam a execução da consulta e armazenam os resultados em uma matriz ou lista, respectivamente. Você pode usar estes métodos para armazenar em cache os resultados de dados de uma consulta em vez de executar a consulta de origem novamente.  Acrescente as consultas que geram os baralhos com uma chamada para `ToArray()` e execute a consulta novamente:

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Execute novamente e o embaralhamento interno será de até 30 consultas. Execute novamente com o embaralhamento externo e você verá melhorias semelhantes. (Ele agora executa 162 consultas).

Não interprete incorretamente esse exemplo pensando que todas as consultas devem ser executadas cuidadosamente. Este exemplo é projetado para realçar os casos de uso em que a avaliação lenta pode causar problemas de desempenho. Isso ocorre porque cada nova disposição do baralho de cartas é criada com base na disposição anterior. Usar a avaliação lenta significa que cada nova disposição do baralho é criada do baralho original, até mesmo a execução do código que criou o `startingDeck`. Isso causa uma grande quantidade de trabalho extra. 

Na prática, alguns algoritmos são muito melhores executados usando a avaliação rápida e outros executam muito melhor usando a avaliação lenta. (Em geral, a avaliação lenta é uma opção muito melhor quando a fonte de dados é um processo separado, como um mecanismo de banco de dados. Nesses casos, a avaliação lenta permite que consultas mais complexas executem apenas uma viagem de ida e volta e para o processo de banco de dados.) O LINQ permite uma avaliação lenta e rápida. Meça e escolha a melhor opção.

## <a name="preparing-for-new-features"></a>Preparação para novos recursos

O código que você escreveu para este exemplo é um exemplo de como criar um protótipo simples que faz o trabalho. Isso é uma ótima maneira de explorar um espaço problemático e, para muitos recursos, pode ser a melhor solução permanente. Você terá aproveitado *tipos anônimos* para as cartas e cada carta será representada por cadeias de caracteres.

Os *tipos anônimos* têm muitas vantagens de produtividade. Você não precisa definir uma classe para representar o armazenamento. O compilador gera o tipo para você. O tipo gerado pelo compilador utiliza várias das melhores práticas para objetos de dados simples. Ele é *imutável*, o que significa que nenhuma de suas propriedades pode ser alterada depois que ele for construído. Os tipos anônimos são internos para um assembly, então eles não são vistos como parte da API pública para esse assembly. Os tipos anônimos também contêm uma substituição do método `ToString()` que retorna uma cadeia de caracteres formatada com cada um dos valores.

Os tipos anônimos também têm desvantagens. Eles não têm nomes acessíveis, portanto você não pode usá-los como argumentos ou valores de retorno. Você notará que todos os métodos acima que usaram esses tipos anônimos são métodos genéricos. A substituição de `ToString()` pode não ser o que você deseja à medida que o aplicativo cria mais recursos. 

O exemplo também usa cadeias de caracteres para o naipe e a classificação de cada carta. Isso é bastante ilimitado. O sistema de tipo C# pode nos ajudar a tornar o código melhor, aproveitando tipos `enum` para esses valores.

Comece com os naipes. Este é o momento perfeito para usar um `enum`:

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

O método `Suits()` também altera o tipo e a implementação:

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

Em seguida, faça a mesma alteração com a classificação das cartas:

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

E o método que gera as cartas:

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

Como limpeza final, vamos criar um tipo para representar a carta, em vez de depender de um tipo anônimo. Os tipos anônimos são ótimos para tipos simples e locais, mas, neste exemplo, a carta do jogo é um dos principais conceitos. Ela deve ser de um tipo concreto.

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

Esse tipo usa *propriedades somente leitura autoimplementadas* que são definidas no construtor e não podem ser modificadas. Ele também usa o novo recurso de *interpolação de cadeia de caracteres* que facilita a saída da cadeia de caracteres de formato.

Atualize a consulta que gera o baralho inicial para usar o novo tipo:

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

Compile e execute novamente. A saída é um pouco mais limpa e o código é um pouco mais claro e pode ser estendido mais facilmente.

## <a name="conclusion"></a>Conclusão

Este exemplo mostrou alguns dos métodos usados em LINQ e como criar seus próprios métodos que serão facilmente usados com o código habilitado para LINQ. Ele também mostrou as diferenças entre a avaliação lenta e a rápida e o impacto que a decisão pode ter no desempenho.

Você aprendeu um pouco sobre uma técnica dos mágicos. Os mágicos usam o embaralhamento porque eles podem controlar onde cada carta fica no baralho. Em alguns truques, o mágico escolha uma pessoa para colocar a carta no topo do baralho e embaralha as cartas algumas vezes, sabendo onde a carta escolhida está. Outras ilusões exigem que o baralho esteja disposto de uma determinada maneira. Um mágico fará a disposição do baralho antes de realizar o truque. Em seguida, ele embaralhará as cartas 5 vezes usando uma ordem aleatória interna. No palco, ele pode mostrar como é o embaralhamento e embaralhar mais três vezes e ter o baralho definido exatamente como deseja.
