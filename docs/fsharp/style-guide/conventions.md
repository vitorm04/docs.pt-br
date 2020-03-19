---
title: Convenções de codificação do F#
description: Aprenda diretrizes gerais e expressões idiomáticas ao escrever o código F# .
ms.date: 01/15/2020
ms.openlocfilehash: 7266211e501bdb52564220781e2347d1aceaf296
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400305"
---
# <a name="f-coding-conventions"></a>Convenções de codificação do F#

As convenções a seguir são formuladas a partir da experiência de trabalhar com grandes bases de código F#. Os [Cinco princípios do bom código F#](index.md#five-principles-of-good-f-code) são a base de cada recomendação. Eles estão relacionados com as diretrizes de [design de componentes F#,](component-design-guidelines.md)mas são aplicáveis para qualquer código F#, não apenas componentes como bibliotecas.

## <a name="organizing-code"></a>Código organizador

F# apresenta duas maneiras principais de organizar código: módulos e namespaces. Estes são semelhantes, mas têm as seguintes diferenças:

* Os namespaces são compilados como namespaces .NET. Os módulos são compilados como classes estáticas.
* Os namespaces são sempre de nível superior. Os módulos podem ser de alto nível e aninhados em outros módulos.
* Os namespaces podem abranger vários arquivos. Módulos não podem.
* Os módulos podem `[<RequireQualifiedAccess>]` ser `[<AutoOpen>]`decorados com e .

As seguintes diretrizes ajudarão você a usá-las para organizar seu código.

### <a name="prefer-namespaces-at-the-top-level"></a>Prefira espaços de nome no nível superior

Para qualquer código de consumo público, os namespaces são preferenciais aos módulos no nível superior. Como eles são compilados como namespaces .NET, eles são consumíveis a partir de C# sem problema.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

O uso de um módulo de nível superior pode não parecer diferente quando chamado apenas de `MyClass` F#, mas para os consumidores C#, os chamadores podem se surpreender por ter que se qualificar com o `MyCode` módulo.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Aplique cuidadosamente`[<AutoOpen>]`

A `[<AutoOpen>]` construção pode poluir o escopo do que está disponível para os chamadores, e a resposta para onde algo vem é "mágica". Isso não é uma coisa boa. Uma exceção a esta regra é a própria Biblioteca Núcleo F# (embora este fato também seja um pouco controverso).

No entanto, é uma conveniência se você tiver funcionalidade de ajudante para uma API pública que você deseja organizar separadamente dessa API pública.

```fsharp
module MyAPI =
    [<AutoOpen>]
    module private Helpers =
        let helper1 x y z =
            ...

    let myFunction1 x =
        let y = ...
        let z = ...

        helper1 x y z
```

Isso permite que você separe os detalhes de implementação da API pública de uma função sem ter que qualificar totalmente um ajudante cada vez que você chamá-lo.

Além disso, expor métodos de extensão e construtores de `[<AutoOpen>]`expressões no nível namespace pode ser claramente expresso com .

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Use `[<RequireQualifiedAccess>]` sempre que os nomes podem entrar em conflito ou você sente que ajuda na legibilidade

Adicionar `[<RequireQualifiedAccess>]` o atributo a um módulo indica que o módulo pode não ser aberto e que as referências aos elementos do módulo requerem acesso qualificado explícito. Por exemplo, `Microsoft.FSharp.Collections.List` o módulo tem esse atributo.

Isso é útil quando funções e valores no módulo têm nomes que provavelmente entrarão em conflito com nomes em outros módulos. Exigir acesso qualificado pode aumentar muito a manutenção e a evolução de uma biblioteca a longo prazo.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Classificar `open` declarações topologicamente

Em F#, a ordem das declarações importa, inclusive com `open` declarações. Isto é diferente de C#, onde o efeito `using` e `using static` é independente da ordenação dessas declarações em um arquivo.

Em F#, elementos abertos em um escopo podem sombrear outros já presentes. Isso significa que `open` as declarações de reordenação podem alterar o significado do código. Como resultado, qualquer classificação arbitrária `open` de todas as declarações (por exemplo, alfanuméricamente) não é recomendada, para que você não gere um comportamento diferente do que você poderia esperar.

Em vez disso, recomendamos que você os [classifique topologicamente;](https://en.wikipedia.org/wiki/Topological_sorting) ou seja, `open` ordeneisuas instruções na ordem em que _as camadas_ do seu sistema são definidas. Fazer classificação alfanumérica dentro de diferentes camadas topológicas também pode ser considerada.

Como exemplo, aqui está a classificação topológica para o arquivo aPI público do serviço de compilação F#:

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open Microsoft.FSharp.Compiler
open Microsoft.FSharp.Compiler.AbstractIL
open Microsoft.FSharp.Compiler.AbstractIL.Diagnostics
open Microsoft.FSharp.Compiler.AbstractIL.IL
open Microsoft.FSharp.Compiler.AbstractIL.ILBinaryReader
open Microsoft.FSharp.Compiler.AbstractIL.Internal
open Microsoft.FSharp.Compiler.AbstractIL.Internal.Library

open Microsoft.FSharp.Compiler.AccessibilityLogic
open Microsoft.FSharp.Compiler.Ast
open Microsoft.FSharp.Compiler.CompileOps
open Microsoft.FSharp.Compiler.CompileOptions
open Microsoft.FSharp.Compiler.Driver
open Microsoft.FSharp.Compiler.ErrorLogger
open Microsoft.FSharp.Compiler.Infos
open Microsoft.FSharp.Compiler.InfoReader
open Microsoft.FSharp.Compiler.Lexhelp
open Microsoft.FSharp.Compiler.Layout
open Microsoft.FSharp.Compiler.Lib
open Microsoft.FSharp.Compiler.NameResolution
open Microsoft.FSharp.Compiler.PrettyNaming
open Microsoft.FSharp.Compiler.Parser
open Microsoft.FSharp.Compiler.Range
open Microsoft.FSharp.Compiler.Tast
open Microsoft.FSharp.Compiler.Tastops
open Microsoft.FSharp.Compiler.TcGlobals
open Microsoft.FSharp.Compiler.TypeChecker
open Microsoft.FSharp.Compiler.SourceCodeServices.SymbolHelpers

open Internal.Utilities
open Internal.Utilities.Collections
```

Observe que uma linha rompe camadas topológicas, com cada camada sendo classificada alfanumérica depois. Isso organiza o código de forma limpa sem acidentalmente sombrear valores.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Use classes para conter valores que tenham efeitos colaterais

Há muitas vezes em que a inicialização de um valor pode ter efeitos colaterais, como instanciar um contexto para um banco de dados ou outro recurso remoto. É tentador inicializar tais coisas em um módulo e usá-las em funções subseqüentes:

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/{your name}/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

Esta é freqüentemente uma má idéia por algumas razões:

Primeiro, a configuração do aplicativo `dep1` é `dep2`empurrada para a base de código com e . Isso é difícil de manter em bases de código maiores.

Em segundo lugar, os dados inicializados estáticamente não devem incluir valores que não são seguros para threads se o próprio componente usar vários segmentos. Isto é claramente violado por `dep3`.

Finalmente, a inicialização do módulo compila-se em um construtor estático para toda a unidade de compilação. Se ocorrer algum erro na inicialização de valor let-bound `TypeInitializationException` nesse módulo, ele se manifesta como um cache a toda a vida útil do aplicativo. Isso pode ser difícil de diagnosticar. Geralmente há uma exceção interna que você pode tentar argumentar, mas se não houver, então não há como dizer qual é a causa raiz.

Em vez disso, basta usar uma classe simples para manter dependências:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Isso permite o seguinte:

1. Empurrando qualquer estado dependente fora da própria API.
2. A configuração agora pode ser feita fora da API.
3. Erros na inicialização de valores dependentes `TypeInitializationException`não são susceptíveis de se manifestar como um .
4. A API agora é mais fácil de testar.

## <a name="error-management"></a>Gerenciamento de erros

O gerenciamento de erros em sistemas grandes é um esforço complexo e nuances, e não há balas de prata para garantir que seus sistemas sejam tolerantes a falhas e se comportem bem. As seguintes diretrizes devem oferecer orientação para navegar neste espaço difícil.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Representar casos de erro e estado ilegal em tipos intrínsecos ao seu domínio

Com [sindicatos discriminados,](../language-reference/discriminated-unions.md)F# lhe dá a capacidade de representar o estado de programa defeituoso em seu sistema de tipo. Por exemplo: 

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

Neste caso, existem três maneiras conhecidas de que sacar dinheiro de uma conta bancária pode falhar. Cada caso de erro é representado no tipo e, portanto, pode ser tratado com segurança durante todo o programa.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Em geral, se você pode modelar as diferentes maneiras que algo pode **falhar** em seu domínio, então o código de manipulação de erros não é mais tratado como algo que você deve lidar, além do fluxo regular do programa. É simplesmente uma parte do fluxo normal do programa, e não considerado **excepcional.** Há dois benefícios primários para isso:

1. É mais fácil de manter à medida que seu domínio muda com o tempo.
2. Os casos de erro são mais fáceis de fazer o teste unitário.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Use exceções quando erros não podem ser representados com tipos

Nem todos os erros podem ser representados em um domínio de problemas. Esses tipos de falhas são *excepcionais* na natureza, daí a capacidade de aumentar e capturar exceções em F#.

Primeiro, recomenda-se que você leia as [Diretrizes de Design de Exceção](../../standard/design-guidelines/exceptions.md). Estes também são aplicáveis a F#.

Os principais construtos disponíveis em F# para fins de levantar exceções devem ser considerados na seguinte ordem de preferência:

| Função | Sintaxe | Finalidade |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Levanta `System.ArgumentNullException` um com o nome de argumento especificado. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Levanta `System.ArgumentException` um com um nome de argumento e mensagem especificados. |
| `invalidOp` | `invalidOp "message"` | Levanta `System.InvalidOperationException` um com a mensagem especificada. |
|`raise`| `raise (ExceptionType("message"))` | Mecanismo de uso geral para lançar exceções. |
| `failwith` | `failwith "message"` | Levanta `System.Exception` um com a mensagem especificada. |
| `failwithf` | `failwithf "format string" argForFormatString` | Levanta `System.Exception` um com uma mensagem determinada pela seqüência de formato e suas entradas. |

Use `nullArg` `invalidArg` , `invalidOp` e como `ArgumentNullException`mecanismo `ArgumentException` `InvalidOperationException` para lançar , e quando apropriado.

As `failwith` `failwithf` funções devem ser geralmente evitadas porque `Exception` elevam o tipo de base, não uma exceção específica. De acordo com as [Diretrizes de Design de Exceção,](../../standard/design-guidelines/exceptions.md)você deseja aumentar as exceções mais específicas quando puder.

### <a name="using-exception-handling-syntax"></a>Usando sintaxe de manipulação de exceções

F# suporta padrões `try...with` de exceção através da sintaxe:

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Conciliar funcionalidades para executar em face de uma exceção com correspondência de padrões pode ser um pouco complicado se você deseja manter o código limpo. Uma dessas maneiras de lidar com isso é usar [padrões ativos](../language-reference/active-patterns.md) como um meio de agrupar a funcionalidade em torno de um caso de erro com uma exceção em si. Por exemplo, você pode estar consumindo uma API que, quando lança uma exceção, inclui informações valiosas nos metadados de exceção. Desembrulhar um valor útil no corpo da exceção capturada dentro do Active Pattern e devolver esse valor pode ser útil em algumas situações.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Não use o manuseio de erros monádicos para substituir exceções

As exceções são vistas como um tabu na programação funcional. De fato, exceções violam a pureza, por isso é seguro considerá-las não muito funcionais. No entanto, isso ignora a realidade de onde o código deve ser executado, e que erros de tempo de execução podem ocorrer. Em geral, escreva código supondo que a maioria das coisas não são puras nem totais, para minimizar surpresas desagradáveis.

É importante considerar os seguintes pontos fortes/aspectos centrais das Exceções no que diz respeito à sua relevância e adequação no ecossistema de runtime e cross-language da .NET como um todo:

1. Eles contêm informações detalhadas de diagnóstico, o que é muito útil ao depurar um problema.
2. Eles são bem compreendidos pelo tempo de execução e outros idiomas .NET.
3. Eles podem reduzir caldeiras significativas quando comparados com o código que sai do seu caminho para *evitar* exceções, implementando algum subconjunto de sua semântica em uma base ad-hoc.

Este terceiro ponto é crítico. Para operações complexas não triviais, não usar exceções pode resultar em lidar com estruturas como esta:

```fsharp
Result<Result<MyType, string>, string list>
```

O que pode facilmente levar a um código frágil, como a correspondência de padrões em erros "digitados por stringly":

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Além disso, pode ser tentador engolir qualquer exceção no desejo de uma função "simples" que retorne um tipo "mais agradável":

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Infelizmente, `tryReadAllText` pode lançar inúmeras exceções com base na miríade de coisas que podem acontecer em um sistema de arquivos, e este código descarta qualquer informação sobre o que pode realmente estar dando errado em seu ambiente. Se você substituir esse código por um tipo de resultado, então você voltará à análise de mensagem de erro "digitada por stringly":

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Ok
    with e -> Error e.Message

let r = tryReadAllText "path-to-file"
match r with
| Ok text -> ...
| Error e ->
    if e.Contains "uh oh, here we go again..." then ...
    else ...
```

E colocar o objeto `Error` de exceção em si na construtora apenas força você a lidar adequadamente com o tipo de exceção no local de chamada e não na função. Fazer isso efetivamente cria exceções verificadas, que são notoriamente pouco divertidas de lidar como um chamador de uma API.

Uma boa alternativa aos exemplos acima é pegar exceções *específicas* e devolver um valor significativo no contexto dessa exceção. Se você `tryReadAllText` modificar a função `None` da seguinte forma, tem mais significado:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Em vez de funcionar como um catch-all, esta função agora lidará adequadamente com o caso quando um arquivo não foi encontrado e atribuirá esse significado a um retorno. Esse valor de retorno pode ser mapeado para esse caso de erro, sem descartar nenhuma informação contextual ou forçar os chamadores a lidar com um caso que pode não ser relevante nesse ponto do código.

Tipos como `Result<'Success, 'Error>` são apropriados para operações básicas onde não estão aninhados, e os tipos opcionais F# são perfeitos para representar quando algo pode retornar *algo* ou *nada*. No entanto, eles não substituem exceções e não devem ser usados na tentativa de substituir as exceções. Em vez disso, eles devem ser aplicados criteriosamente para abordar aspectos específicos da política de gerenciamento de erros e exceções de maneiras direcionadas.

## <a name="partial-application-and-point-free-programming"></a>Aplicação parcial e programação sem pontos

F# suporta aplicação parcial e, portanto, várias maneiras de programar em um estilo sem pontos. Isso pode ser benéfico para a reutilização de código dentro de um módulo ou para a implementação de algo, mas não é algo para expor publicamente. Em geral, a programação sem pontos não é uma virtude em si mesma, e pode adicionar uma barreira cognitiva significativa para pessoas que não estão imersas no estilo.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Não use aplicação parcial e currying em APIs públicas

Com pouca exceção, o uso de aplicação parcial em APIs públicas pode ser confuso para os consumidores. Normalmente, `let`valores vinculados no código F# são **valores,** não **valores de função**. Misturar valores e valores de função pode resultar em salvar um pequeno número de linhas de código em `>>` troca de um pouco de sobrecarga cognitiva, especialmente se combinado com operadores como para compor funções.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Considere as implicações de ferramentação para programação sem pontos

As funções curriculares não rotulam seus argumentos. Isso tem implicações de ferramentas. Considere as duas funções a seguir:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Ambas são funções `funcWithApplication` válidas, mas é uma função curricular. Quando você paira sobre seus tipos em um editor, você vê isso:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

No site de chamadas, dicas de ferramentas em ferramentas como o Visual `string` `int` Studio não lhe darão informações significativas sobre o que os tipos e de entrada realmente representam.

Se você encontrar um `funcWithApplication` código sem pontos como esse é consumível publicamente, é recomendável fazer uma expansão completa para que as ferramentas possam captar nomes significativos para argumentos.

Além disso, depurar código sem pontos pode ser desafiador, se não impossível. As ferramentas de depuração dependem de `let` valores vinculados a nomes (por exemplo, vinculações) para que você possa inspecionar valores intermediários no meio da execução. Quando seu código não tem valores para inspecionar, não há nada para depurar. No futuro, as ferramentas de depuração podem evoluir para sintetizar esses valores com base em caminhos executados anteriormente, mas não é uma boa ideia proteger suas apostas em *possíveis* funcionalidades de depuração.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Considere a aplicação parcial como uma técnica para reduzir a caldeira interna

Em contraste com o ponto anterior, a aplicação parcial é uma ferramenta maravilhosa para reduzir a caldeira dentro de uma aplicação ou os internos mais profundos de uma API. Pode ser útil para a unidade testar a implementação de APIs mais complicadas, onde caldeira sao muitas vezes uma dor para lidar. Por exemplo, o código a seguir mostra como você pode realizar o que a maioria das estruturas de zombaria lhe dão sem ter uma dependência externa de tal estrutura e ter que aprender uma API medida relacionada.

Por exemplo, considere a seguinte topografia de solução:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj`pode expor códigos como:

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

O teste `Transactions.doTransaction` `ImplementationLogic.Tests.fsproj` unitário é fácil:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

Aplicar parcialmente `doTransaction` com um objeto de contexto zombando permite que você chame a função em todos os testes da unidade sem precisar construir um contexto zombado cada vez:

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member _.TheFirstMember() = ...
        member _.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

Esta técnica não deve ser universalmente aplicada a toda a sua base de código, mas é uma boa maneira de reduzir a caldeira para internos complicados e testes unitários desses internos.

## <a name="access-control"></a>Controle de acesso

F# tem várias opções para controle de [acesso,](../language-reference/access-control.md)herdadas do que está disponível no tempo de execução .NET. Estes não são apenas utilizáveis para tipos - você pode usá-los para funções, também.

* Prefira`public` não-tipos e membros até que você precise que eles sejam consumíveis publicamente. Isso também minimiza o que os consumidores acasalam.
* Esforce-se para manter `private`todas as funcionalidades de ajudante.
* Considere o `[<AutoOpen>]` uso em um módulo privado de funções auxiliares se elas se tornarem numerosas.

## <a name="type-inference-and-generics"></a>Inferência de tipo e genéricos

A inferência de digitação pode salvá-lo de digitar um monte de caldeira. E a generalização automática no compilador F# pode ajudá-lo a escrever códigos mais genéricos com quase nenhum esforço extra de sua parte. No entanto, essas características não são universalmente boas.

* Considere rotular nomes de argumentos com tipos explícitos em APIs públicas e não confie em inferência de tipo para isso.

    A razão para isso é que **você** deve estar no controle da forma de sua API, não do compilador. Embora o compilador possa fazer um bom trabalho em inferir tipos para você, é possível ter a forma de sua mudança de API se os internos em que ele se baseia ter mudado de tipo. Isso pode ser o que você quer, mas quase certamente resultará em uma mudança de API que os consumidores a jusante terão que lidar. Em vez disso, se você controlar explicitamente a forma de sua API pública, então você pode controlar essas mudanças quebrando. Em termos DDD, isso pode ser considerado como uma camada anticorrupção.

* Considere dar um nome significativo aos seus argumentos genéricos.

    A menos que você esteja escrevendo códigos verdadeiramente genéricos que não são específicos para um domínio específico, um nome significativo pode ajudar outros programadores a entender o domínio em que estão trabalhando. Por exemplo, um parâmetro `'Document` de tipo nomeado no contexto de interagir com um banco de dados de documentos deixa mais claro que tipos de documentos genéricos podem ser aceitos pela função ou membro com quem você está trabalhando.

* Considere nomear parâmetros de tipo genéricos com PascalCase.

    Esta é a maneira geral de fazer as coisas em .NET, por isso é recomendável que você use PascalCase em vez de snake_case ou camelCase.

Finalmente, a generalização automática nem sempre é um benefício para as pessoas que são novas no F# ou em uma grande base de código. Há sobrecarga cognitiva no uso de componentes que são genéricos. Além disso, se as funções automaticamente generalizadas não forem usadas com diferentes tipos de entrada (muito menos se elas forem destinadas a ser usadas como tal), então não há nenhum benefício real para eles serem genéricos naquele momento. Sempre considere se o código que você está escrevendo realmente se beneficiará de ser genérico.

## <a name="performance"></a>Desempenho

### <a name="prefer-structs-for-small-data-types"></a>Prefira estruturas para pequenos tipos de dados

O uso de estruturas (também chamadas tipos de valor) pode muitas vezes resultar em maior desempenho para algum código, porque normalmente evita a alocação de objetos. No entanto, as estruturas nem sempre são um botão "ir mais rápido": se o tamanho dos dados em uma estrutura exceder 16 bytes, copiar os dados pode muitas vezes resultar em mais tempo de CPU gastar do que usar um tipo de referência.

Para determinar se você deve usar uma estrutura, considere as seguintes condições:

- Se o tamanho de seus dados for de 16 bytes ou menor.
- Se é provável que você tenha muitos desses tipos de dados residentes na memória em um programa em execução.

Se a primeira condição se aplicar, você deve geralmente usar uma estrutura. Se ambos se aplicam, você deve quase sempre usar uma estrutura. Pode haver alguns casos em que as condições anteriores se aplicam, mas usar uma estrutura não é melhor ou pior do que usar um tipo de referência, mas é provável que sejam raros. É importante sempre medir quando se faz mudanças como esta, porém, e não operar em suposição ou intuição.

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a>Prefira tuplas de estrutura ao agrupar pequenos tipos de valor

Considere as duas funções a seguir:

```fsharp
let rec runWithTuple t offset times =
    let offsetValues x y z offset =
        (x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let (x, y, z) = t
        let r = offsetValues x y z offset
        runWithTuple r offset (times - 1)

let rec runWithStructTuple t offset times =
    let offsetValues x y z offset =
        struct(x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let struct(x, y, z) = t
        let r = offsetValues x y z offset
        runWithStructTuple r offset (times - 1)
```

Quando você faz benchmark dessas funções com uma ferramenta de benchmarking `runWithStructTuple` estatístico como [benchmarkDotNet,](https://benchmarkdotnet.org/)você verá que a função que usa tuplas de estrutura é 40% mais rápida e não aloca memória.

No entanto, esses resultados nem sempre serão o caso em seu próprio código. Se você marcar `inline`uma função como , código que usa tuplas de referência pode obter algumas otimizações adicionais, ou código que alocaria poderia simplesmente ser otimizado. Você deve sempre medir resultados sempre que o desempenho estiver em causa, e nunca operar com base em suposição ou intuição.

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a>Prefira registros de estruturaquando o tipo de dados é pequeno

A regra de ouro descrita anteriormente também vale para [os tipos de registro F#](../language-reference/records.md). Considere os seguintes tipos de dados e funções que os processam:

```fsharp
type Point = { X: float; Y: float; Z: float }

[<Struct>]
type SPoint = { X: float; Y: float; Z: float }

let rec processPoint (p: Point) offset times =
    let inline offsetValues (p: Point) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processPoint r offset (times - 1)

let rec processStructPoint (p: SPoint) offset times =
    let inline offsetValues (p: SPoint) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processStructPoint r offset (times - 1)
```

Isso é semelhante ao código tuplo anterior, mas desta vez o exemplo usa registros e uma função interna inforrada.

Quando você faz benchmark dessas funções com uma ferramenta de benchmarking `processStructPoint` estatístico como [benchmarkDotNet,](https://benchmarkdotnet.org/)você verá que é quase 60% mais rápido e não aloca nada no heap gerenciado.

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a>Prefira struct sindicatos discriminados quando o tipo de dados é pequeno

As observações anteriores sobre o desempenho com tuplas e registros de estrutura também são para [F# Sindicatos Discriminados](../language-reference/discriminated-unions.md). Considere o código a seguir:

```fsharp
    type Name = Name of string

    [<Struct>]
    type SName = SName of string

    let reverseName (Name s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> Name

    let structReverseName (SName s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> SName
```

É comum definir unis unionhas discriminadas como esta para modelagem de domínio. Quando você faz benchmark dessas funções com uma ferramenta de benchmarking `structReverseName` estatístico como [benchmarkDotNet,](https://benchmarkdotnet.org/)você verá que é cerca de 25% mais rápido do que `reverseName` para pequenas strings. Para cordas grandes, ambos executam quase o mesmo. Então, neste caso, é sempre preferível usar uma estrutura. Como mencionado anteriormente, sempre meça e não opere em pressupostos ou intuições.

Embora o exemplo anterior mostrasse que uma União Discriminada de estruturação produziu melhor desempenho, é comum ter sindicatos discriminados maiores ao modelar um domínio. Tipos de dados maiores como esse podem não funcionar tão bem se forem estruturas dependendo das operações neles, já que mais cópias podem estar envolvidas.

### <a name="functional-programming-and-mutation"></a>Programação funcional e mutação

Os valores f# são imutáveis por padrão, o que permite evitar certas classes de bugs (especialmente aqueles que envolvem concorrência e paralelismo). No entanto, em certos casos, a fim de obter a eficiência ideal (ou mesmo razoável) do tempo de execução ou alocações de memória, um período de trabalho pode ser melhor implementado usando mutação de estado no local. Isso é possível em uma base opt-in com F# com a `mutable` palavra-chave.

O `mutable` uso de em F# pode se sentir em desacordo com a pureza funcional. Isso é compreensível, mas a pureza funcional em todos os lugares pode estar em desacordo com as metas de desempenho. Um compromisso é encapsular mutação de tal forma que os chamadores não precisam se preocupar com o que acontece quando eles chamam uma função. Isso permite que você escreva uma interface funcional sobre uma implementação baseada em mutação para código crítico de desempenho.

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Envoltório código mutável em interfaces imutáveis

Com a transparência referencial como meta, é fundamental escrever código que não exponha o submundo das funções críticas ao desempenho. Por exemplo, o código `Array.contains` a seguir implementa a função na biblioteca principal F#:

```fsharp
[<CompiledName("Contains")>]
let inline contains value (array:'T[]) =
    checkNonNull "array" array
    let mutable state = false
    let mutable i = 0
    while not state && i < array.Length do
        state <- value = array.[i]
        i <- i + 1
    state
```

Chamar essa função várias vezes não altera a matriz subjacente, nem exige que você mantenha qualquer estado mutável em consumi-la. É referencialmente transparente, embora quase todas as linhas de código dentro dele use mutação.

#### <a name="consider-encapsulating-mutable-data-in-classes"></a>Considere encapsular dados mutáveis nas classes

O exemplo anterior usou uma única função para encapsular operações usando dados mutáveis. Isso nem sempre é suficiente para conjuntos de dados mais complexos. Considere os seguintes conjuntos de funções:

```fsharp
open System.Collections.Generic

let addToClosureTable (key, value) (t: Dictionary<_,_>) =
    if not (t.ContainsKey(key)) then
        t.Add(key, value)
    else
        t.[key] <- value

let closureTableCount (t: Dictionary<_,_>) = t.Count

let closureTableContains (key, value) (t: Dictionary<_, HashSet<_>>) =
    match t.TryGetValue(key) with
    | (true, v) -> v.Equals(value)
    | (false, _) -> false
```

Este código é performante, mas expõe a estrutura de dados baseada em mutação que os chamadores são responsáveis pela manutenção. Isso pode ser embrulhado dentro de uma classe sem membros subjacentes que possam mudar:

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member _.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member _.Count = t.Count

    member _.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

`Closure1Table`encapsula a estrutura de dados baseada em mutação subjacente, não forçando os chamadores a manter a estrutura de dados subjacente. As classes são uma maneira poderosa de encapsular dados e rotinas que são baseadas em mutação sem expor os detalhes aos chamadores.

#### <a name="prefer-let-mutable-to-reference-cells"></a>Prefira `let mutable` as células de referência

As células de referência são uma forma de representar a referência a um valor e não ao valor em si. Embora possam ser usados para código crítico de desempenho, eles não são recomendados. Considere o exemplo a seguir:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

O uso de uma célula de referência agora "polui" todo o código subseqüente com a desreferência e rereferência dos dados subjacentes. Em vez `let mutable`disso, considere:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Além do único ponto de mutação no meio da expressão lambda, todos os outros códigos `acc` que tocam podem `let`fazê-lo de uma maneira que não é diferente do uso de um valor imutável normal. Isso tornará mais fácil mudar com o tempo.

## <a name="object-programming"></a>Programação de objetos

F# tem suporte total para objetos e conceitos orientados a objetos (OO). Embora muitos conceitos de OO sejam poderosos e úteis, nem todos eles são ideais para usar. As listas a seguir oferecem orientações sobre categorias de recursos oO em um alto nível.

**Considere usar esses recursos em muitas situações:**

* Notação de`x.Length`dot ()
* Membros de instância
* Construtores implícitos
* Membros estáticos
* Notação do`arr.[x]`indexador ( )
* Argumentos nomeados e opcionais
* Implementações de interfaces e interfaces

**Não alcance esses recursos primeiro, mas aplique-os criteriosamente quando eles são convenientes para resolver um problema:**

* Sobrecarga de método
* Dados mutáveis encapsulados
* Operadores em tipos
* Propriedades automáticas
* Implementação `IDisposable` e`IEnumerable`
* Tipo extensões
* Eventos
* Structs
* Delega
* Enums

**Geralmente evite esses recursos, a menos que você deve usá-los:**

* Hierarquias de tipo baseadas em herança e herança de implementação
* Nulos e`Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Prefira composição em vez de herança

[Composição sobre herança](https://en.wikipedia.org/wiki/Composition_over_inheritance) é um idioma de longa data que o bom código F# pode aderir. O princípio fundamental é que você não deve expor uma classe base e forçar os chamadores a herdar dessa classe base para obter funcionalidade.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Use expressões de objeto para implementar interfaces se você não precisar de uma classe

[Expressões de objeto](../language-reference/object-expressions.md) permitem que você implemente interfaces em tempo real, vinculando a interface implementada a um valor sem precisar fazê-lo dentro de uma classe. Isso é conveniente, especialmente se você _só_ precisa implementar a interface e não tem necessidade de uma aula completa.

Por exemplo, aqui está o código que é executado em [Ionide](http://ionide.io/) para fornecer uma ação de `open` correção de código se você adicionou um símbolo para o qual você não tem uma declaração:

```fsharp
    let private createProvider () =
        { new CodeActionProvider with
            member this.provideCodeActions(doc, range, context, ct) =
                let diagnostics = context.diagnostics
                let diagnostic = diagnostics |> Seq.tryFind (fun d -> d.message.Contains "Unused open statement")
                let res =
                    match diagnostic with
                    | None -> [||]
                    | Some d ->
                        let line = doc.lineAt d.range.start.line
                        let cmd = createEmpty<Command>
                        cmd.title <- "Remove unused open"
                        cmd.command <- "fsharp.unusedOpenFix"
                        cmd.arguments <- Some ([| doc |> unbox; line.range |> unbox; |] |> ResizeArray)
                        [|cmd |]
                res
                |> ResizeArray
                |> U2.Case1
        }
```

Como não há necessidade de uma aula ao interagir com a API visual studio code, as Expressões de Objeto são uma ferramenta ideal para isso. Eles também são valiosos para testes unitários, quando você quer stub out uma interface com rotinas de teste de uma maneira ad hoc.

## <a name="consider-type-abbreviations-to-shorten-signatures"></a>Considere abreviaturas de tipo para encurtar assinaturas

[Abreviaturas de tipo](../language-reference/type-abbreviations.md) são uma maneira conveniente de atribuir um rótulo a outro tipo, como uma assinatura de função ou um tipo mais complexo. Por exemplo, o alias a seguir atribui um rótulo ao necessário para definir uma computação com [CNTK](https://docs.microsoft.com/cognitive-toolkit/), uma biblioteca de aprendizado profundo:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

O `Computation` nome é uma maneira conveniente de denotar qualquer função que corresponda à assinatura que está aliando. Usar abreviaturas de tipo como esta é conveniente e permite um código mais sucinto.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Evite usar abreviaturas de tipo para representar seu domínio

Embora abreviaturas de tipo sejam convenientes para dar um nome para funcionar assinaturas, elas podem ser confusas ao abreviar outros tipos. Considere esta abreviação:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Isso pode ser confuso de várias maneiras:

* `BufferSize`não é uma abstração; é apenas outro nome para um inteiro.
* Se `BufferSize` for exposto em uma API pública, pode ser facilmente `int`mal interpretado para significar mais do que apenas . Geralmente, os tipos de domínio têm vários atributos para eles e não são tipos primitivos como `int`. Essa abreviação viola essa suposição.
* O invólucro de `BufferSize` (PascalCase) implica que este tipo contém mais dados.
* Este alias não oferece maior clareza em comparação com o fornecimento de um argumento nomeado para uma função.
* A abreviação não se manifestará em IL compilado; é apenas um inteiro e este alias é uma compilação-tempo de construção.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

Em resumo, a armadilha com abreviaturas de tipo é que **elas não** são abstrações sobre os tipos que estão abreviando. No exemplo anterior, `BufferSize` é `int` apenas um as coberturas, sem dados `int` adicionais, nem quaisquer benefícios do sistema do tipo além do que já tem.

Uma abordagem alternativa para usar abreviaturas de tipo para representar um domínio é usar sindicatos discriminados em caso único. A amostra anterior pode ser modelada da seguinte forma:

```fsharp
type BufferSize = BufferSize of int
```

Se você escrever código que opera `BufferSize` em termos e seu valor subjacente, você precisa construir um em vez de passar em qualquer inteiro arbitrário:

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

Isso reduz a probabilidade de passar erroneamente um `send` inteiro arbitrário `BufferSize` para a função, porque o chamador deve construir um tipo para envolver um valor antes de chamar a função.
