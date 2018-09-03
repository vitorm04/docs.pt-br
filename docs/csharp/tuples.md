---
title: Tipos de tupla – Guia C#
description: Saiba mais sobre os tipos de tupla nomeadas e sem nome em C#
ms.date: 05/15/2018
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: b0c838791e640c9813005b8a32d009153a794c14
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404308"
---
# <a name="c-tuple-types"></a>Tipos de tupla do C# #

As tuplas do C# são tipos que você define usando uma sintaxe leve. As vantagens incluem sintaxe mais simples, regras para conversões baseadas em números (conhecidas como cardinalidade) e em tipos de elementos, além de regras compatíveis para cópias, testes de igualdade e atribuições. Em contrapartida, as tuplas não oferecem suporte a algumas das expressões orientadas a objeto associadas à herança. Você pode obter uma visão geral na seção sobre [tuplas no artigo Novidades no C# 7.0](whats-new/csharp-7.md#tuples).

Neste artigo, você aprenderá as regras de linguagem que regem as tuplas no C# 7.0 e em versões posteriores, além de diferentes maneiras de usá-las e as diretrizes iniciais para trabalhar com tuplas.

> [!NOTE]
> Os novos recursos de tuplas exigem os tipos <xref:System.ValueTuple>.
> Você deve adicionar o pacote NuGet [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) para usá-lo em plataformas que não incluem os tipos.
>
> Isso é semelhante a outros recursos de linguagem que dependem de tipos entregues no framework. Os exemplos incluem `async` e `await` que dependem da interface `INotifyCompletion`, além do LINQ que depende de `IEnumerable<T>`. No entanto, o mecanismo de entrega está mudando conforme o .NET se torna mais independente de plataforma. O .NET Framework pode não ser enviados sempre na mesma cadência que o compilador de linguagem. Quando novos recursos de linguagem dependerem de novos tipos, esses tipos estarão disponíveis como pacotes do NuGet quando os recursos de linguagem forem enviados. Conforme esses novos tipos são adicionados à API padrão do .NET e fornecidos como parte do framework, o requisito de pacote do NuGet será removido.

Vamos começar com os motivos para adicionar o novo suporte de tupla. Métodos retornam um único objeto. Tuplas permitem que você empacote vários valores nesse único objeto mais facilmente.

O .NET Framework já tem classes `Tuple` genéricas. Essas classes, no entanto, têm duas limitações importantes. Por exemplo, as classes `Tuple` nomearam suas propriedades como `Item1`, `Item2` e assim por diante. Esses nomes não carregam informações semânticas. O uso desses tipos `Tuple` não permite comunicar o significado de cada uma das propriedades. Os novos recursos de linguagem permitem que você declare e use nomes semanticamente significativos para os elementos em uma tupla.

As classes de `Tuple` causam mais problemas de desempenho porque elas são tipos de referência. O uso de um dos tipos `Tuple` significa alocar objetos. Em afunilamentos, alocar muitos objetos pequenos pode ter um impacto mensurável no desempenho do aplicativo. Portanto, o suporte de linguagem para tuplas aproveita os novos structs `ValueTuple`.

Para evitar essas deficiências, você pode criar uma `class` ou um `struct` para carregar vários elementos. Infelizmente, isso significa mais trabalho para você e obscurece a intenção do design. Fazer uma `struct` ou `class` significa que você está definindo um tipo com os dados e comportamento. Muitas vezes, você simplesmente deseja armazenar diversos valores em um único objeto.

Os recursos de linguagem e os structs genéricos `ValueTuple` aplicam a regra de que você não pode adicionar nenhum comportamento (método) a esses tipos de tupla.
Todos os tipos `ValueTuple` são *structs mutáveis*. Cada campo membro é um campo público. Isso os torna muito simples. No entanto, isso significa que as tuplas não devem ser usadas quando a imutabilidade é importante.

As tuplas são contêineres de dados mais simples e mais flexíveis do que os tipos `class` e `struct`. Vamos explorar essas diferenças.

## <a name="named-and-unnamed-tuples"></a>Tuplas nomeadas e sem nome

O struct `ValueTuple` tem campos nomeados `Item1`, `Item2`, `Item3` e assim por diante, semelhante às propriedades definidas nos tipos de `Tuple` existentes.
Esses nomes são os únicos nomes que você pode usar para *tuplas sem nome*. Quando você não fornece nomes de campo alternativos para uma tupla, cria uma tupla sem nome:

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

A tupla no exemplo anterior foi inicializada usando constantes literais e não terá nomes de elemento criados usando as *projeções de nome de campo de tupla* no C# 7.1.

No entanto, quando você inicializa uma tupla, pode usar novos recursos de linguagem que fornecem nomes melhores para cada campo. Fazer isso cria uma *tupla nomeada*.
As tuplas nomeadas ainda têm elementos chamados `Item1`, `Item2`, `Item3` e assim por diante.
Mas também têm sinônimos para qualquer um desses elementos que você tenha nomeado.
Você cria uma tupla nomeada especificando os nomes de cada elemento. Uma maneira é especificar os nomes como parte da inicialização da tupla:

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "Named tuple")]

Esses sinônimos são manipulados pelo compilador e pela linguagem para que você possa usar as tuplas nomeadas de forma eficaz. Os editores e IDEs podem ler esses nomes semânticos usando APIs Roslyn. É possível fazer referência aos elementos de uma tupla nomeada com nomes semânticos em qualquer lugar no mesmo assembly. O compilador substitui os nomes que você definiu com equivalentes `Item*` ao gerar a saída compilada. A MSIL (Microsoft Intermediate Language) compilada não inclui os nomes que você atribuiu a esses elementos.

Começando com o C# 7.1, os nomes de campo para uma tupla podem ser fornecidos por meio das variáveis usadas para inicializar a tupla. Isso é conhecido como **[inicializadores de projeção de tupla](#tuple-projection-initializers)**. O código a seguir cria uma tupla denominada `accumulation` com elementos `count` (um inteiro) e `sum` (um duplo).

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectedTupleNames "Named tuple")]

O compilador deve comunicar esses nomes que você criou para tuplas retornadas de métodos públicos ou propriedades. Nesses casos, o compilador adiciona um atributo <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> no método. Esse atributo contém uma propriedade de lista <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> que inclui os nomes dados a cada um desses elementos na tupla.

> [!NOTE]
> Ferramentas de desenvolvimento, como o Visual Studio, também leem esses metadados e fornecem IntelliSense e outros recursos usando os nomes de campo de metadados.

É importante entender esses conceitos básicos subjacentes das novas tuplas e do tipo `ValueTuple` para entender as regras para atribuir tuplas nomeadas entre si.

## <a name="tuple-projection-initializers"></a>Inicializadores de projeção de tupla

Em geral, os inicializadores de projeção de tupla funcionam com o uso dos nomes de campo ou de variáveis do lado direito de uma instrução de inicialização de tupla.
Se for fornecido um nome explícito, ele terá precedência sobre qualquer nome projetado. Por exemplo, no seguinte inicializador, os elementos são `explicitFieldOne` e `explicitFieldTwo`, não `localVariableOne` e `localVariableTwo`:

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

Para qualquer campo em que um nome explícito não for fornecido, será projetado um nome implícito aplicável. Não há nenhum requisito para fornecer nomes semânticos, explícita ou implicitamente. O inicializador a seguir terá nomes de campo `Item1`, cujo valor é `42` e `stringContent`, cujo valor é "A resposta para tudo":

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#MixedTuple "mixed tuple")]

Há duas condições nas quais os possíveis nomes de campos não são projetados no campo da tupla:

1. Quando o possível nome é um nome de tupla reservado. Os exemplos incluem `Item3`, `ToString`. ou `Rest`.
1. Quando o possível nome é uma duplicata de outro nome de campo de tupla, seja explícito ou implícito.

Essas condições evitam a ambiguidade. Esses nomes causariam ambiguidade se fossem usados como nomes de campo em uma tupla. Nenhuma dessas condições causa erros de tempo de compilação. Em vez disso, os elementos sem nomes projetados não terão nomes semânticos projetados para eles.  Os exemplos a seguir demonstram essas condições:

[!code-csharp[Ambiguity](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

Essas situações não causam erros de compilador porque essa seria uma alteração significativa nos códigos escritos com C# 7.0, em que as projeções de nome de campo de tupla não estavam disponíveis.

## <a name="equality-and-tuples"></a>Igualdade e tuplas

Começando com o C# 7.3, os tipos de tupla oferecem suporte aos operadores `==` e `!=`. Esses operadores comparam cada membro do argumento da esquerda com cada membro do argumento da direita na ordem. Essas comparações são de curto-circuito. O operador `==` interromperá a avaliação de membros assim que um par não for igual. O operador `!=` interromperá a avaliação de membros assim que um par for igual. O código a seguir exemplifica o uso de `==`, mas todas as regras de comparação se aplicam a `!=`. O exemplo de código a seguir mostra uma comparação de igualdade de dois pares de inteiros:

[!code-csharp[TupleEquality](../../samples/snippets/csharp/tuples/tuples/program.cs#Equality "Testing tuples for equality")]

Há várias regras que tornam os testes de igualdade de tuplas mais convenientes. A igualdade de tupla executa [conversões lifted](language-reference/language-specification/index.md) se uma das tuplas for uma tupla que permite valor nulo, conforme mostrado no código a seguir:


[!code-csharp[NullableTupleEquality](../../samples/snippets/csharp/tuples/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

A igualdade de tupla também executa conversões implícitas em cada membro de ambas as tuplas. Esses incluem conversões lifted, conversões widening ou outras conversões implícitas. Os exemplos a seguir mostram que um inteiro de uma tupla 2 pode ser comparado a um longo de tupla 2 devido à conversão implícita do inteiro para um longo:

[!code-csharp[SnippetMemberConversions](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

Os nomes dos membros da tupla não participam em testes de igualdade. No entanto, se um dos operandos for uma tupla literal com nomes explícitos, o compilador gera o aviso CS8383 caso os nomes não correspondam aos nomes do outro operando.
No caso em que ambos os operandos são literais de tupla, o aviso é no operando à direita, conforme mostrado no exemplo a seguir:

[!code-csharp[MemberNames](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

Por fim, as tuplas podem conter tuplas aninhadas. A igualdade de tupla compara a "forma" de cada operando por meio de tuplas aninhadas, conforme mostrado no exemplo a seguir:

[!code-csharp[NestedTuples](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

## <a name="assignment-and-tuples"></a>Atribuição e tuplas

A linguagem oferece suporte à atribuição entre tipos de tuplas que têm o mesmo número de elementos, em que cada elemento do lado direito pode ser convertido implicitamente em seu elemento correspondente do lado esquerdo. Outras conversões não são consideradas para atribuições. Vamos examinar os tipos de atribuições que são permitidos entre tipos de tupla.

Considere estas variáveis usadas nos exemplos a seguir:

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "Variable creation")]

As primeiras duas variáveis, `unnamed` e `anonymous`, não têm nomes semânticos fornecidos para os elementos. Os nomes de campo são `Item1` e `Item2`.
As duas últimas variáveis, `named` e `differentName`, têm nomes semânticos fornecidos para os elementos. Estas duas tuplas têm nomes diferentes para os elementos.

Todas essas quatro tuplas têm o mesmo número de elementos (chamados de "cardinalidade") e os tipos desses elementos são idênticos. Portanto, todas essas atribuições funcionam:

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "Variable assignment")]

Observe que os nomes das tuplas não são atribuídos. Os valores dos elementos são atribuídos na ordem dos elementos na tupla.

As tuplas com tipos ou números de elementos diferentes não são atribuíveis:

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Tuplas como valores retornados do método

Um dos usos mais comuns de tuplas é como um valor retornado do método. Vamos examinar um exemplo. Considere este método que calcula o desvio padrão para uma sequência de números:

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> Esses exemplos calculam o desvio padrão de exemplo não corrigido.
> A fórmula do desvio padrão de exemplo corrigida dividiria a soma das diferenças da média ao quadrado por (N-1) em vez de N, como o método de extensão `Average` faz. Consulte um texto sobre estatísticas para obter mais detalhes sobre as diferenças entre essas fórmulas para desvio padrão.

O código anterior segue a fórmula típica para o desvio padrão. Ele produz a resposta correta, mas é uma implementação ineficiente. Esse método enumera a sequência de duas vezes: uma vez para produzir a média e uma vez para produzir a média do quadrado da diferença da média.
(Lembre-se de que consultas LINQ são avaliadas lentamente, então o cálculo das diferenças da média e a média dessas diferenças compõem apenas uma enumeração.)

Há uma alternativa fórmula que calcula o desvio padrão usando apenas uma enumeração da sequência.  Esse cálculo produz dois valores conforme enumera a sequência: a soma de todos os itens na sequência e a soma de cada valor ao quadrado:

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

Essa versão enumera a sequência exatamente uma vez. Mas não é um código reutilizável. Conforme você continua a trabalhar, descobrirá que muitos cálculos estatísticos diferentes usam o número de itens na sequência, a soma da sequência e a soma dos quadrados da sequência. Vamos refatorar esse método e escrever um método utilitário que produz todos esses três valores. Todos os três valores podem retornar como uma tupla.

Vamos atualizar esse método para que os três valores calculados durante a enumeração sejam armazenados em uma tupla. Isso cria essa versão:

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

O suporte à refatoração do Visual Studio facilita a extração da funcionalidade para as estatísticas principais em um método privado. Isso fornece a você um método `private static` que retorna o tipo de tupla com os três valores de `Sum`, `SumOfSquares` e `Count`:

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]
 
A linguagem permite algumas opções adicionais que podem ser usadas se você desejar fazer algumas edições rápidas manualmente. Primeiro, você pode usar a declaração `var` para inicializar o resultado da tupla da chamada do método `ComputeSumAndSumOfSquares`. Você também pode criar três variáveis discretas dentro do método `ComputeSumAndSumOfSquares`. A versão final é mostrada no código a seguir:

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

Esta versão final pode ser usada para qualquer método que precise desses três valores ou qualquer subconjunto deles.

A linguagem dá suporte a outras opções no gerenciamento dos nomes dos elementos nesses métodos de retorno de tupla.

Você pode remover os nomes de campo da declaração de valor retornado e retornar uma tupla sem nome:

```csharp
private static (double, double, int) ComputeSumAndSumOfSquares(IEnumerable<double> sequence)
{
    double sum = 0;
    double sumOfSquares = 0;
    int count = 0;

    foreach (var item in sequence)
    {
        count++;
        sum += item;
        sumOfSquares += item * item;
    }

    return (sum, sumOfSquares, count);
}
```

Os campos nesta tupla são nomeados `Item1`, `Item2` e `Item3`.
É recomendável que você forneça nomes semânticos para os elementos de tuplas retornados dos métodos.

Outra linguagem em que as tuplas podem ser úteis é quando você estiver criando consultas LINQ. O resultado final projetado geralmente contém algumas, mas não todas, propriedades dos objetos que estão sendo selecionados.

Tradicionalmente, você poderia projetar os resultados da consulta em uma sequência de objetos que eram um tipo anônimo. Isso apresentava muitas limitações, principalmente porque os tipos anônimos não poderiam ser nomeados de forma conveniente no tipo de retorno de um método. Alternativas usando `object` ou `dynamic` como o tipo de resultado acompanham os custos de desempenho significativos.

Retornar uma sequência de um tipo de tupla é fácil e os nomes e tipos desses elementos estão disponíveis no tempo de compilação e por meio de ferramentas de IDE.
Por exemplo, imagine um aplicativo de tarefas. Você pode definir uma classe semelhante à seguinte para representar uma única entrada na lista de tarefas:

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

Seus aplicativos móveis podem dar suporte a um formato compacto dos itens de tarefas atuais que exibem apenas o título. Essa consulta LINQ faria uma projeção que inclui somente a ID e o título. Um método que retorna uma sequência de tuplas expressa bem esse design:

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> No C# 7.1, as projeções de tupla permitem criar tuplas nomeadas usando elementos, de maneira semelhante à nomeação de propriedade nos tipos anônimos. No código acima, a instrução `select` na projeção de consulta cria uma tupla que tem elementos `ID` e `Title`.

A tupla nomeada pode ser parte da assinatura. Ela permite que o compilador e as ferramentas de IDE forneçam verificações estáticas de que você está usando o resultado corretamente. A tupla nomeada também contém as informações de tipo estático, portanto, não há necessidade de usar recursos caros de tempo de execução como reflexão ou associação dinâmica para trabalhar com os resultados.

## <a name="deconstruction"></a>Desconstrução

Você pode descompactar todos os itens em uma tupla *desconstruindo* a tupla retornada por um método. Há três abordagens diferentes para desconstruir tuplas.  Primeiro, você pode declarar explicitamente o tipo de cada campo dentro de parênteses para criar variáveis discretas para cada um dos elementos na tupla:

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

Você também pode declarar variáveis de tipo implícito para cada campo em uma tupla usando a palavra-chave `var` fora dos parênteses:

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

Também é válido usar a palavra-chave `var` com qualquer uma ou todas as declarações de variável dentro dos parênteses. 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

Você não poderá usar um tipo específico fora dos parênteses, mesmo se todos os campos na tupla tiverem o mesmo tipo.

Você também pode desconstruir tuplas com declarações existentes:

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
>  Você não pode combinar as declarações existentes com as declarações dentro dos parênteses. Por exemplo, o seguinte não é permitido: `(var x, y) = MyMethod();`. Isso gera o erro CS8184 porque *x* está declarado dentro dos parênteses e *y* já foi declarado em outro lugar.

### <a name="deconstructing-user-defined-types"></a>Desconstruindo tipos definidos pelo usuário

Qualquer tipo de tupla pode ser desconstruído, conforme mostrado acima. Também é fácil habilitar a desconstrução em qualquer tipo definido pelo usuário (classes, structs ou até mesmo interfaces).

O autor do tipo pode definir um ou mais métodos `Deconstruct` que atribuem valores a qualquer número de variáveis `out` que representam os elementos de dados que compõem o tipo. Por exemplo, o tipo `Person` a seguir define um método `Deconstruct` que desconstrói um objeto person nos elementos representando o nome e o sobrenome:

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

O método deconstruct permite a atribuição de um `Person` para duas cadeias de caracteres, representando as propriedades `FirstName` e `LastName`:

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

Você pode habilitar a desconstrução mesmo para os tipos que você não criou.
O método `Deconstruct` pode ser um método de extensão que retira do pacote os membros de dados acessíveis de um objeto. O exemplo a seguir mostra um tipo `Student`, derivado do tipo `Person` e um método de extensão que desconstrói um `Student` em três variáveis, representando a `FirstName`, a `LastName` e a `GPA`:

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

Um objeto `Student` agora tem dois métodos `Deconstruct` acessíveis: o método de extensão declarado para tipos `Student` e o membro do tipo `Person`. Ambos estão no escopo e isso permite que um `Student` seja desconstruído em duas ou três variáveis.
Se você atribuir um aluno a três variáveis, o nome, o sobrenome e a GPA serão retornados. Se você atribuir um aluno a duas variáveis, apenas o nome e o sobrenome serão retornados.

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

Você deve tomar cuidado ao definir vários métodos `Deconstruct` em uma classe ou hierarquia de classes. Vários métodos `Deconstruct` que têm o mesmo número de parâmetros `out` podem causar ambiguidades rapidamente. Os chamadores podem não conseguir chamar facilmente o método `Deconstruct` desejado.

Neste exemplo, há uma chance mínima de uma chamada ambígua porque o método `Deconstruct` para `Person` tem dois parâmetros de saída e o método `Deconstruct` para `Student` tem três.

Os operadores de desconstrução não participam do teste de igualdade. O exemplo a seguir gera o erro do compilador CS0019:

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

O método `Deconstruct` pôde converter o objeto`Person` `p` em uma tupla que contém duas cadeias de caracteres, mas não é aplicável no contexto de testes de igualdade.

## <a name="conclusion"></a>Conclusão 

O novo suporte de linguagem e biblioteca para tuplas nomeadas torna muito mais fácil trabalhar com designs que usam estruturas de dados que armazenam vários elementos, mas não definem comportamento, como as classes e os structs fazem. É fácil e sucinto usar tuplas para esses tipos. Você obtém todos os benefícios da verificação de tipo estático, sem precisar criar tipos usando a sintaxe de `class` ou de `struct` mais detalhada. Mesmo assim, elas são mais úteis para métodos utilitários que são `private` ou `internal`. Cria tipos definidos pelo usuário, tipos `class` ou `struct`, quando seus métodos públicos retornam um valor que tem vários elementos.
