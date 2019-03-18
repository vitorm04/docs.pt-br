---
title: Novidades no C# 8.0 – Guia do C#
description: Obtenha uma visão geral dos novos recursos disponíveis no C# 8.0. Este artigo foi atualizado com a versão prévia 2.
ms.date: 02/12/2019
ms.openlocfilehash: 23197a051109d6c6c22c8855e3772cf4f824264c
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "57843927"
---
# <a name="whats-new-in-c-80"></a>Novidades no C# 8.0

Há vários aprimoramentos na linguagem C# que você já pode experimentar na versão prévia 2. Os novos recursos adicionados na versão prévia 2 são:

- [Aprimoramentos de correspondência de padrões](#more-patterns-in-more-places):
  * [Expressões Switch](#switch-expressions)
  * [Padrões da propriedade](#property-patterns)
  * [Padrões de tupla](#tuple-patterns)
  * [Padrões posicionais](#positional-patterns)
- [Declarações using](#using-declarations)
- [Funções locais estáticas](#static-local-functions)
- [Estruturas ref descartáveis](#disposable-ref-structs)

Os recursos de linguagem a seguir apareceram pela primeira vez no C# 8.0 versão prévia 1:

- [Tipos de referência nula](#nullable-reference-types)
- [Fluxos assíncronos](#asynchronous-streams)
- [Índices e intervalos](#indices-and-ranges)

> [!NOTE]
> Este artigo foi atualizado pela última vez para o C# 8.0 versão prévia 2.

O restante deste artigo descreve rapidamente esses recursos. Quando houver artigos detalhados disponíveis, forneceremos links para esses tutoriais e visões gerais.

## <a name="more-patterns-in-more-places"></a>Mais padrões em mais partes

Com a **correspondência de padrões**, você recebe ferramentas para fornecer funcionalidades dependentes da forma em tipos de dados relacionados, mas diferentes. O C# 7.0 introduziu uma sintaxe para padrões de tipo e padrões de constante usando a expressão [`is`](../language-reference/keywords/is.md) e a instrução [`switch`](../language-reference/keywords/switch.md). Esses recursos representaram os primeiros passos em direção ao suporte a paradigmas de programação, em que os dados e a funcionalidade vivem separados. À medida que o setor se aproxima mais de microsserviços e de outras arquiteturas baseadas em nuvem, outras ferramentas de linguagem de tornam necessárias.

O C# 8.0 expande esse vocabulário, para que você possa usar mais expressões de padrão em mais partes do seu código. Considere esses recursos quando seus dados e funcionalidades estiverem separados. Considere a correspondência de padrões quando seus algoritmos dependerem de um fato diferente do tipo de tempo de execução de um objeto. Essas técnicas fornecem outra maneira de expressar designs.

Além dos novos padrões em novas partes, o C# 8.0 adiciona **padrões recursivos**. O resultado de qualquer expressão padrão é uma expressão. Um padrão recursivo é simplesmente uma expressão padrão aplicada à saída de outra expressão padrão.

### <a name="switch-expressions"></a>Expressões switch

Frequentemente, uma instrução [`switch`](../language-reference/keywords/switch.md) produz um valor em cada um de seus blocos `case`. As **expressões switch** permitem que você use a sintaxe de expressão mais concisa. Há menos palavras-chave `case` e `break` repetidas, e menos chaves.  Por exemplo, considere a enumeração a seguir que lista as cores do arco-íris:

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Green,
    Blue,
    Indigo,
    Violet
}
```

Você poderia converter um valor `Rainbow` em valores RGB usando o seguinte método que contém uma expressão switch:

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Green  => new RGBColor(0x00, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

Há vários aprimoramentos de sintaxe aqui:

- A variável vem antes da palavra-chave `switch`. A ordem diferente facilita distinguir visualmente a expressão switch da instrução switch.
- Os elementos `case` e `:` são substituídos por `=>`. É mais conciso e intuitivo.
- O caso `default` é substituído por um descarte `_`.
- Os corpos são expressões, não instruções.

Compare isso com o código equivalente usando a instrução clássica `switch`:

```csharp
public static RGBColor FromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Green:
            return new RGBColor(0x00, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

### <a name="property-patterns"></a>Padrões da propriedade

O **padrão da propriedade** permite que você compare as propriedades do objeto examinado. Considere um site de comércio eletrônico que deve calcular o imposto da venda com base no endereço do comprador. Esse cálculo não é uma responsabilidade principal de uma classe `Address`. Ele mudará ao longo do tempo, provavelmente com mais frequência do que as alterações de formato de endereço. O valor do imposto depende da propriedade `State` do endereço. O método a seguir usa o padrão de propriedade para calcular o imposto da venda de acordo com o endereço e o preço:

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

A correspondência de padrão cria uma sintaxe concisa para expressar esse algoritmo.

### <a name="tuple-patterns"></a>Padrões de tupla

Alguns algoritmos dependem de várias entradas. **Padrões de tupla** permitem que você alterne com base em vários valores, expressadas como uma [tupla](../tuples.md).  O código a seguir mostra uma expressão de comutador para o jogo *pedra, papel, tesoura*:

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
```

As mensagens indicam o vencedor. O caso de descarte representa três combinações para empates ou outras entradas de texto.

### <a name="positional-patterns"></a>Padrões posicionais

Alguns tipos incluem um método `Deconstruct` que desconstrói suas propriedades em variáveis discretas. Quando um método `Deconstruct` é acessível, você pode usar **padrões posicionais** para inspecionar as propriedades do objeto e usar essas propriedades para um padrão.  Considere a seguinte classe `Point`, que inclui um método `Deconstruct` para criar variáveis discretas para `X` e `Y`:

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

O método a seguir usa o **padrão posicional** para extrair os valores de `x` e `y`. Em seguida, usa uma cláusula `when` para determinar o quadrante do ponto:

```csharp
static string Quadrant(Point p) => p switch
{
    (0, 0) => "origin",
    (var x, var y) when x > 0 && y > 0 => "Quadrant 1",
    (var x, var y) when x < 0 && y > 0 => "Quadrant 2",
    (var x, var y) when x < 0 && y < 0 => "Quadrant 3",
    (var x, var y) when x > 0 && y < 0 => "Quadrant 4",
    (var x, var y) => "on a border",
    _ => "unknown"
};
```

O padrão de descarte na switch anterior encontra a correspondência quando `x` ou `y`, mas não ambos, for 0. Uma expressão switch deve produzir um valor ou lançar uma exceção. Se não houver correspondência em nenhum dos casos, a expressão switch gerará uma exceção. O compilador gerará um aviso se você não cobrir todos os casos possíveis em sua expressão switch.

## <a name="using-declarations"></a>Declarações using

Uma **declaração using** é uma declaração de variável precedida pela palavra-chave `using`. Ele informa ao compilador que a variável que está sendo declarada deve ser descartada ao final do escopo delimitador. Por exemplo, considere o seguinte código que grava um arquivo de texto:

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        // If the line doesn't contain the word 'Second', write the line to the file.
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

No exemplo anterior, o arquivo é descartado quando a chave de fechamento do método é atingida. Esse é o final do escopo no qual `file` é declarado. O código anterior é equivalente ao código a seguir usando as [instruções using](../language-reference/keywords/using-statement.md) clássicas:


```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            // If the line doesn't contain the word 'Second', write the line to the file.
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

No exemplo anterior, o arquivo é descartado quando a chave de fechamento associada à instrução `using` é atingida.

Em ambos os casos, o compilador gera a chamada para `Dispose()`. O compilador gera um erro se a expressão na instrução using não for descartável.

## <a name="static-local-functions"></a>Funções locais estáticas

Agora você pode adicionar o modificador `static` para funções locais a fim de garantir que essa função local não capture (faça referência) às variáveis no escopo delimitador. Isso gera `CS8421`, "Uma função local estática não pode conter uma referência a <variable>". 

Considere o código a seguir. A função local `LocalFunction` acessa a variável `y`, declarada no escopo delimitador (o método `M`). Portanto, `LocalFunction` não pode ser declarada com o modificador `static`:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

O código a seguir contém uma função local estática. Ela pode ser estática porque não acesse as variáveis no escopo delimitador:

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>Estruturas ref descartáveis

Uma `struct` declarada com o modificador `ref` não pode implementar quaisquer interfaces e, portanto, não pode implementar <xref:System.IDisposable>. Portanto, para permitir que uma `ref struct` seja descartada, ela deve ter um método `void Dispose()` acessível. Isso também se aplica às declarações `readonly ref struct`.

## <a name="nullable-reference-types"></a>Tipos de referência anuláveis

Dentro de um contexto de anotação anulável, qualquer variável de um tipo de referência é considerado um **tipo de referência não anulável**. Se você quiser indicar que uma variável pode ser nula, acrescente o nome do tipo com o `?` para declarar a variável como um **tipo de referência anulável**.

Para tipos de referência não anuláveis, o compilador usa a análise de fluxo para garantir que as variáveis locais sejam inicializadas como um valor não nulo quando declaradas. Os campos devem ser inicializados durante a construção. O compilador gera um aviso se a variável não for definida por uma chamada para qualquer um dos construtores disponíveis ou por um inicializador. Além disso, os tipos de referência não anuláveis não podem receber um valor que possa ser nulo.

Os tipos de referência anuláveis não são verificados para garantir que não tenham sido atribuídos ou inicializados como nulos. No entanto, o compilador usa a análise de fluxo para garantir que qualquer variável de um tipo de referência anulável passe por verificação com relação a um nulo antes de ser acessada ou atribuída a um tipo de referência não anulável.

Saiba mais sobre o recurso na visão geral sobre [Tipos de referência anuláveis](../nullable-references.md). Experimente-o em um novo aplicativo neste [tutorial de tipos de referência anuláveis](../tutorials/nullable-reference-types.md). Saiba mais sobre as etapas para migrar uma base de códigos existente para usar tipos de referência anuláveis no [tutorial sobre como migrar um aplicativo para usar tipos de referência anuláveis](../tutorials/upgrade-to-nullable-references.md).

## <a name="asynchronous-streams"></a>Fluxos assíncronos

A partir do C# 8.0, você pode criar e consumir fluxos de forma assíncrona. Um método que retorna um fluxo assíncrono tem três propriedades:

1. Ele é declarado com o modificador `async`.
1. Ela retorna um <xref:System.Collections.Generic.IAsyncEnumerable%601>.
1. O método contém instruções `yield return` para retornar elementos sucessivos no fluxo assíncrono.

O consumo de um fluxo assíncrono exige que você adicione a palavra-chave `await` antes da palavra-chave `foreach` quando você enumera os elementos do fluxo. A adição da palavra-chave `await` exige o método que enumera o fluxo assíncrono seja declarado com o modificador `async` e retorne um tipo permitido para um método `async`. Normalmente, isso significa retornar um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. Também pode ser <xref:System.Threading.Tasks.ValueTask> ou <xref:System.Threading.Tasks.ValueTask%601>. Um método pode consumir e produzir um fluxo assíncrono, o que significa que retornaria um <xref:System.Collections.Generic.IAsyncEnumerable%601>. O código a seguir gera uma sequência de 0 a 19, esperando 100 ms entre a geração de cada número:

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

Você enumeraria a sequência usando a instrução `await foreach`:

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Experimente você mesmo os fluxos assíncronos em nosso tutorial sobre como [criar e consumir fluxos assíncronos](../tutorials/generate-consume-asynchronous-stream.md).

## <a name="indices-and-ranges"></a>Índices e intervalos

Intervalos e índices fornecem uma sintaxe sucinta para especificar subintervalos em uma matriz, <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.

Você pode especificar um índice **do final**. Especifique **do final** usando o operador `^`. Você está familiarizado com `array[2]` significando o elemento "2 desde o início". Agora, `array[^2]` significa o elemento "2 desde o final". O índice `^0` significa "final", ou o índice que segue o último elemento.

Você pode especificar um **intervalo** com o **operador de intervalo**: `..`. Por exemplo, `0..^0` especifica todo o intervalo da matriz: 0 desde o início até, mas não incluindo, 0 do final. Qualquer operando pode usar "desde o início" ou "desde o final". Além disso, qualquer operando pode ser omitido. Os padrões são `0` para o índice de início, e `^0` para o índice final.

Vamos analisar alguns exemplos. Considere a matriz a seguir, anotada com seu índice do início e do final:

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};
```

O índice de cada elemento reforça o conceito de "do início" e "do final", e que os intervalos excluem o fim do intervalo. O "início" de toda a matriz é o primeiro elemento. O "final" de toda a matriz ocorre *após* o último elemento.

Recupere a última palavra com o índice `^1`:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

O código a seguir cria um subintervalo com as palavras "quick", "brown" e "fox". Ele inclui `words[1]` até `words[3]`. O elemento `words[4]` não está no intervalo.

```csharp
var quickBrownFox = words[1..4];
```

O código a seguir cria um subintervalo com "lazy" e "dog". Ele inclui `words[^2]` e `words[^1]`. O índice final `words[^0]` não está incluído:

```csharp
var lazyDog = words[^2..^0];
```

Os exemplos a seguir criam intervalos abertos para o início, fim ou ambos:

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the, "lazy" and "dog"
```

Você também pode declarar intervalos como variáveis:

```csharp
Range phrase = 1..4;
```

Em seguida, o intervalo pode ser usado dentro dos caracteres `[` e `]`:

```csharp
var text = words[phrase];
```
