---
title: Tuplas | Guia de C#
description: Saiba mais sobre os tipos de tupla nomeadas e sem nome em C#
keywords: .NET, .NET Core, C#
author: BillWagner
ms-author: wiwagn
ms.date: 11/23/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f2c81b7e18f36bde5b46c0c6df5c8122cd303931
ms.lasthandoff: 03/13/2017

---

# <a name="c-tuple-types"></a>Tipos de tupla do C# #

As tuplas do C# são tipos definidos usando uma sintaxe simples. As vantagens incluem uma sintaxe mais simples, regras para conversões baseadas no número (conhecidas como "aridade") e tipos de campos e regras consistentes para cópias e atribuições. Como uma compensação, as tuplas não dão suporte a algumas das expressões orientadas a objeto associados à herança. Você pode obter uma visão geral na seção sobre [Tuplas no tópico Novidades no C# 7](csharp-7.md#tuples).

Neste tópico, você aprenderá as regras de linguagem que regem as tuplas no C# 7, diferentes maneiras de usá-las e diretrizes iniciais sobre como trabalhar com tuplas.

> [!NOTE]
> Os novos recursos de tuplas exigem o tipo `System.ValueTuple`. Para o Visual Studio 2017, você deve adicionar o pacote NuGet [System.ValueTuple](https://www.nuget.org/packages/System.ValueTuple/), disponível na Galeria do NuGet.
> Sem esse pacote, você pode receber um erro de compilação semelhante a `error CS8179: Predefined type 'System.ValueTuple``2' is not defined or imported` ou `error CS8137: Cannot define a class or member that utilizes tuples because the compiler required type 'System.Runtime.CompilerServices.TupleElementNamesAttribute' cannot be found.`

Vamos começar com os motivos para adicionar o novo suporte de tupla. Métodos retornam um único objeto. Tuplas permitem que você empacote vários valores nesse único objeto mais facilmente. 

O .NET Framework já tem classes `Tuple` genéricas. Essas classes, no entanto, têm duas limitações importantes. Por exemplo, as classes `Tuple` nomearam seus campos como `Item1`, `Item2` e assim por diante. Esses nomes não carregam informações semânticas. O uso desses tipos `Tuple` não permite comunicar o significado de cada um dos campos. Outra preocupação é que as classes `Tuple` são tipos de referência. O uso de um dos tipos `Tuple` significa alocar objetos. Em caminhos de acesso, isso pode ter um impacto mensurável no desempenho do aplicativo.

Para evitar essas deficiências, você pode criar um `class` ou um `struct` para conter vários campos. Infelizmente, isso significa mais trabalho para você e obscurece a intenção do design. Fazer uma `struct` ou `class` significa que você está definindo um tipo com os dados e comportamento. Muitas vezes, você simplesmente deseja armazenar diversos valores em um único objeto.

Os novos recursos de linguagem para tuplas, combinados com um novo conjunto de classes da estrutura, abordam essas deficiências. Essas novas tuplas usam os novos structs genéricos `ValueTuple`. Como o nome indica, esse tipo é um `struct` em vez de um `class`. Há versões diferentes desse struct para dar suporte a tuplas com diferentes números de campo. O suporte à nova linguagem fornece nomes semânticos para os campos do tipo da tupla, juntamente com recursos para facilitar a construção ou o acesso aos campos da tupla.

Os recursos de linguagem e os structs genéricos `ValueTuple` aplicam a regra de que você não pode adicionar nenhum comportamento (método) a esses tipos de tupla.
Todos os tipos `ValueTuple` são *structs mutáveis*. Cada campo membro é um campo público. Isso os torna muito simples. No entanto, isso significa que as tuplas não devem ser usadas quando a imutabilidade é importante.

As tuplas são contêineres de dados mais simples e mais flexíveis do que os tipos `class` e `struct`. Vamos explorar essas diferenças.

## <a name="named-and-unnamed-tuples"></a>Tuplas nomeadas e sem nome

O struct `ValueTuple` tem campos chamados `Item1`, `Item2`, `Item3` e assim por diante, semelhante às propriedades definidas nos tipos `Tuple` existentes.
Esses nomes são os únicos nomes que você pode usar para *tuplas sem nome*. Quando você não fornece nomes de campo alternativos para uma tupla, cria uma tupla sem nome:

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple "Tupla sem nome")]

No entanto, quando você inicializa uma tupla, pode usar novos recursos de linguagem que fornecem nomes melhores para cada campo. Fazer isso cria uma *tupla nomeada*.
As tuplas nomeadas ainda têm campos chamados `Item1`, `Item2`, `Item3` e assim por diante.
Mas também têm sinônimos para qualquer um desses campos que você tenha nomeado.
Você cria uma tupla nomeada especificando os nomes de cada campo. Uma maneira é especificar os nomes como parte da inicialização da tupla:

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "Tupla com nome")]

Esses sinônimos são manipulados pelo compilador e pela linguagem para que você possa usar as tuplas nomeadas de forma eficaz. Os editores e IDEs podem ler esses nomes semânticos usando APIs Roslyn. Isso permite que você faça referência aos campos de uma tupla nomeada por esses nomes semânticos em qualquer lugar no mesmo assembly. O compilador substitui os nomes que você definiu com equivalentes `Item*` ao gerar a saída compilada. A MSIL (Microsoft Intermediate Language) compilada não inclui os nomes que você atribuiu a esses campos. 

O compilador deve comunicar esses nomes que você criou para tuplas retornadas de métodos públicos ou propriedades. Nesses casos, o compilador adiciona um atributo `TupleElementNames` no método. Este atributo contém uma lista `TransformNames` que contém os nomes fornecidos para cada um dos campos na tupla. 

> [!NOTE]
> Ferramentas de desenvolvimento, como o Visual Studio, também leem esses metadados e fornecem IntelliSense e outros recursos usando os nomes de campo de metadados.

É importante entender esses conceitos básicos subjacentes das novas tuplas e do tipo `ValueTuple` para entender as regras para atribuir tuplas nomeadas entre si.

## <a name="assignment-and-tuples"></a>Atribuição e tuplas

A linguagem dá suporte à atribuição entre tipos de tupla que têm o mesmo número de campos e os mesmos tipos de cada um desses campos. Esses tipos devem ser correspondências exatas de tempo de compilação. Outras conversões não são consideradas para atribuições. Vamos examinar os tipos de atribuições que são permitidos entre tipos de tupla.

Considere estas variáveis usadas nos exemplos a seguir:

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "Criação de variável")]

As primeiras duas variáveis, `unnamed` e `anonymous`, não têm nomes semânticos fornecidos para os campos. Os nomes de campo são `Item1` e `Item2`.
As duas últimas variáveis, `named` e `differentName`, têm nomes semânticos fornecidos para os campos. Observe que essas duas tuplas têm nomes diferentes para os campos.

Todas essas quatro tuplas têm o mesmo número de campos (chamados de ‘aridades’) e os tipos desses campos são idênticos. Portanto, todas essas atribuições funcionam:

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "Atribuição de variável")]

Observe que os nomes das tuplas não são atribuídos. Os valores dos campos são atribuídos na ordem dos campos na tupla.

As tuplas de diferentes tipos ou números de campos não são atribuíveis:

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Tuplas como valores retornados do método

Um dos usos mais comuns de tuplas é como um valor retornado do método. Vamos examinar um exemplo. Considere este método que calcula o desvio padrão para uma sequência de números:

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "Calcular desvio padrão")]

> [!NOTE]
> Esses exemplos calculam o desvio padrão de exemplo não corrigido.
> A fórmula do desvio padrão de exemplo corrigida dividiria a soma das diferenças da média ao quadrado por (N-1) em vez de N, como o método de extensão `Average` faz. Consulte um texto sobre estatísticas para obter mais detalhes sobre as diferenças entre essas fórmulas para desvio padrão.

Isso segue a fórmula típica para o desvio padrão. Ela produz a resposta correta, mas é uma implementação muito ineficiente. Esse método enumera a sequência de duas vezes: uma vez para produzir a média e uma vez para produzir a média do quadrado da diferença da média.
(Lembre-se de que consultas LINQ são avaliadas lentamente, então o cálculo das diferenças da média e a média dessas diferenças compõem apenas uma enumeração.)

Há uma alternativa fórmula que calcula o desvio padrão usando apenas uma enumeração da sequência.  Esse cálculo produz dois valores conforme enumera a sequência: a soma de todos os itens na sequência e a soma de cada valor ao quadrado:

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "Calcular o desvio padrão usando a soma dos quadrados")]

Essa versão enumera a sequência exatamente uma vez. Mas, não é um código muito reutilizável. Conforme você continua a trabalhar, descobrirá que muitos cálculos estatísticos diferentes usam o número de itens na sequência, a soma da sequência e a soma dos quadrados da sequência. Vamos refatorar esse método e escrever um método utilitário que produz todos esses três valores.

É aqui que as tuplas são muito úteis. 

Vamos atualizar esse método para que os três valores calculados durante a enumeração sejam armazenados em uma tupla. Isso cria essa versão:

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "Refatorar para usar tuplas")]

O suporte à refatoração do Visual Studio torna fácil extrair a funcionalidade para as estatísticas principais em um método privado. Isso fornece a você um método `private static` que retorna o tipo de tupla com os três valores de `Sum`, `SumOfSquares` e `Count`:

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "Após extrair o método utilitário")]
 
A linguagem permite algumas opções adicionais que podem ser usadas se você desejar fazer algumas edições rápidas manualmente. Primeiro, você pode usar a declaração `var` para inicializar o resultado da tupla da chamada do método `ComputeSumAndSumOfSquares`. Você também pode criar três variáveis discretas dentro do método `ComputeSumAndSumOfSquares`. A versão final está abaixo:

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "Após a limpeza final")]

Esta versão final pode ser usada para qualquer método que precise desses três valores ou qualquer subconjunto deles.

A linguagem dá suporte a outras opções no gerenciamento dos nomes dos campos nesses métodos de retorno de tupla.

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

Você deve tratar os campos dessa tupla como `Item1`, `Item2` e `Item3`.
É recomendável que você forneça nomes semânticos para os campos de tuplas retornados dos métodos.

Outra expressão em que as tuplas podem ser muito úteis é quando você estiver criando consultas LINQ em que o resultado final é uma projeção que contém algumas, mas não todas, das propriedades dos objetos sendo selecionados.

Tradicionalmente, você poderia projetar os resultados da consulta em uma sequência de objetos que eram um tipo anônimo. Isso apresentava muitas limitações, principalmente porque os tipos anônimos não poderiam ser nomeados de forma conveniente no tipo de retorno de um método. Alternativas usando `object` ou `dynamic` como o tipo de resultado acompanham os custos de desempenho significativos.

Retornar uma sequência de um tipo de tupla é fácil e os nomes e tipos desses campos estão disponíveis no tempo de compilação e por meio de ferramentas de IDE.
Por exemplo, imagine um aplicativo de tarefas. Você pode definir uma classe semelhante à seguinte para representar uma única entrada na lista de tarefas:

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "Item de tarefa")]

Seus aplicativos móveis podem dar suporte a um formato compacto dos itens de tarefas atuais que exibem apenas o título. Essa consulta LINQ faria uma projeção que inclui somente a ID e o título. Um método que retorna uma sequência de tuplas expressa esse design muito bem:

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "Consulta retornando uma tupla")]

A tupla nomeada pode ser parte da assinatura. Ela permite que o compilador e as ferramentas de IDE forneçam verificações estáticas de que você está usando o resultado corretamente. A tupla nomeada também contém as informações de tipo estático, portanto, não há necessidade de usar recursos caros de tempo de execução como reflexão ou associação dinâmica para trabalhar com os resultados.

## <a name="deconstruction"></a>Desconstrução

Você pode descompactar todos os itens em uma tupla *desconstruindo* a tupla retornada por um método. Há duas abordagens diferentes para desconstruir tuplas.  Primeiro, você pode declarar explicitamente o tipo de cada campo dentro de parênteses para criar variáveis discretas para cada um dos campos na tupla:

[!code-csharp[Desconstruir](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "Desconstruir")]

Você também pode declarar variáveis de tipo implícito para cada campo em uma tupla usando a palavra-chave `var` fora dos parênteses:

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Desconstruir para var")]

Também é válido usar a palavra-chave `var` com qualquer uma ou todas as declarações de variável dentro dos parênteses. 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```
Observe que você não pode usar um tipo específico fora dos parênteses, mesmo se todos os campos na tupla tiverem o mesmo tipo.

### <a name="deconstring-user-defined-types"></a>Desconstruindo tipos definidos por usuário

Qualquer tipo de tupla pode ser desconstruído, conforme mostrado acima. Também é fácil habilitar a desconstrução em qualquer tipo definido pelo usuário (classes, structs ou até mesmo interfaces).

O autor do tipo pode definir um ou mais métodos `Deconstruct` que atribuem valores a qualquer número de variáveis `out` que representam os elementos de dados que compõem o tipo. Por exemplo, o tipo `Person` a seguir define um método `Deconstruct` que desconstrói um objeto person nos campos representando o nome e o sobrenome:

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "Tipo com um método deconstruct")]

O método deconstruct permite a atribuição de um `Person` para duas cadeias de caracteres, representando as propriedades `FirstName` e `LastName`:

[!code-csharp[Desconstruir tipo](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "Desconstruir um tipo de classe")]

Você pode habilitar a desconstrução mesmo para os tipos que você não criou.
O método `Deconstruct` pode ser um método de extensão que retira do pacote os membros de dados acessíveis de um objeto. O exemplo a seguir mostra um tipo `Student`, derivado do tipo `Person` e um método de extensão que desconstrói um `Student` em três variáveis, representando a `FirstName`, a `LastName` e a `GPA`:

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "Tipo com um método de extensão deconstruct")]

Um objeto `Student` agora tem dois métodos `Deconstruct` acessíveis: o método de extensão declarado para tipos `Student` e o membro do tipo `Person`. Ambos estão no escopo e isso permite que um `Student` seja desconstruído em duas ou três variáveis.
Se você atribuir um aluno a três variáveis, o nome, o sobrenome e a GPA são retornados. Se você atribuir um aluno a duas variáveis, apenas o nome e o sobrenome serão retornados.

[!code-csharp[Método de extensão deconstruct](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "Desconstruir um tipo de classe usando um método de extensão")]

Você deve tomar muito cuidado ao definir vários métodos `Deconstruct` em uma classe ou hierarquia de classes. Vários métodos `Deconstruct` que têm o mesmo número de parâmetros `out` podem causar ambiguidades rapidamente. Os chamadores podem não conseguir chamar facilmente o método `Deconstruct` desejado.

Neste exemplo, há uma chance mínima de uma chamada ambígua porque o método `Deconstruct` para `Person` tem dois parâmetros de saída e o método `Deconstruct` para `Student` tem três.

## <a name="conclusion"></a>Conclusão 

O novo suporte de linguagem e biblioteca para tuplas nomeadas torna muito mais fácil trabalhar com designs que usam estruturas de dados que armazenam vários campos, mas não definem comportamento, como as classes e os structs fazem. É fácil e sucinto usar tuplas para esses tipos. Você obtém todos os benefícios da verificação de tipo estático, sem precisar criar tipos usando a sintaxe de `class` ou de `struct` mais detalhada. Mesmo assim, elas são mais úteis para métodos utilitários que são `private` ou `internal`. Crie tipos definidos pelo usuário, tipos `class` ou `struct`, quando seus métodos públicos retornam um valor que tem vários campos.

