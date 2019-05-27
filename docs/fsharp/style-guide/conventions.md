---
title: Convenções de codificação do F#
description: Aprenda diretrizes gerais e expressões ao escrever F# código.
ms.date: 05/14/2018
ms.openlocfilehash: 4b292d0a844a4d9efc79aa865b054b4af2cb68c4
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052795"
---
# <a name="f-coding-conventions"></a>Convenções de codificação do F#

As seguintes convenções são formuladas de experiência trabalhando com grandes F# bases de código. O [cinco princípios bom F# código](index.md#five-principles-of-good-f-code) são a base de cada recomendação. Estão relacionadas com o [ F# diretrizes de design do componente](component-design-guidelines.md), mas são aplicáveis para qualquer F# de código, não apenas componentes, como bibliotecas.

## <a name="organizing-code"></a>Organizando o código

F#recursos de duas maneiras principais de organizar o código: módulos e namespaces. Elas são semelhantes, mas têm as seguintes diferenças:

* Namespaces são compilados como namespaces .NET. Módulos são compilados como classes estáticas.
* Namespaces são sempre de nível superior. Módulos podem ser aninhadas dentro de outros módulos e de alto nível.
* Namespaces podem abranger vários arquivos. Módulos não podem.
* Módulos poderão ser decorados com `[<RequireQualifiedAccess>]` e `[<AutoOpen>]`.

As diretrizes a seguir ajudará você a usá-los para organizar seu código.

### <a name="prefer-namespaces-at-the-top-level"></a>Prefira namespaces no nível superior

Para qualquer código publicamente consumível, namespaces são preferenciais para módulos de nível superior. Como eles são compilados como namespaces .NET, eles são consumíveis do c# com nenhum problema.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

Usando um módulo de nível superior não pode aparecer diferente quando chamado apenas de F#, mas para C# consumidores, os chamadores podem ficar surpreso por ter que qualificar `MyClass` com o `MyCode` módulo.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Aplicar com cuidado `[<AutoOpen>]`

O `[<AutoOpen>]` construção pode poluam o escopo do que está disponível para chamadores, e a resposta para onde algo vêm é "mágica". Geralmente isso não é algo bom. Uma exceção a essa regra é o F# biblioteca principal em si (embora esse fato também é um pouco controverso).

No entanto, ele é uma conveniência, se você tem a funcionalidade de auxiliar para uma API pública que você deseja organizar de separadamente da API pública.

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

Isso lhe dá os detalhes de implementação de separadas corretamente da API pública de uma função sem precisar qualificar totalmente um auxiliar de cada vez que você chamá-lo.

Além disso, expor métodos de extensão e construtores de expressões no nível do namespace pode ser claramente expresso com `[<AutoOpen>]`.

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Use `[<RequireQualifiedAccess>]` sempre que nomes possam entrar em conflito ou você acha que eles ajudam a facilitar a leitura

Adicionando o `[<RequireQualifiedAccess>]` atributo a um módulo indica que o módulo não pode ser aberto e que as referências aos elementos do módulo exigem explícita qualificados acesso. Por exemplo, o `Microsoft.FSharp.Collections.List` módulo tem esse atributo.

Isso é útil quando funções e valores no módulo têm nomes que têm probabilidade de entrar em conflito com nomes em outros módulos. Exigir acesso qualificado pode aumentar muito a manutenção de longo prazo e a capacidade de evolução de uma biblioteca.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Classificação `open` instruções topologicamente

No F#, a ordem dos assuntos de declarações, incluindo com `open` instruções. Isso é diferente do c#, onde o efeito `using` e `using static` é independente da ordenação dessas instruções em um arquivo.

No F#, os elementos abertos em um escopo podem sombrear outras pessoas já está presente. Isso significa que reordenar `open` instruções podem alterar o significado do código. Como resultado, qualquer arbitrário de classificação de todas as `open` instruções (por exemplo, em ordem alfanumérica) geralmente não é recomendado, deixa que você gerar um comportamento diferente que você poderia esperar.

Em vez disso, é recomendável que você classificar [topologicamente](https://en.wikipedia.org/wiki/Topological_sorting); ou seja, solicitar sua `open` instruções na ordem em que _camadas_ do seu sistema são definidos. Fazendo alfanumérico de classificação em diferentes camadas topológicas também pode ser considerado.

Por exemplo, aqui está a classificação topológica para o F# arquivo de API pública do compilador serviço:

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

Observe que uma quebra de linha separa topológicas camadas, com cada camada que está sendo classificada em ordem alfanumérica posteriormente. Isso organiza o código corretamente sem acidentalmente sombreamento valores.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Classes de uso para armazenar valores que têm efeitos colaterais

Há muitas vezes quando a inicialização de um valor pode ter efeitos colaterais, como criar uma instância de um contexto para um banco de dados ou outro recurso remoto. É tentador para inicializar essas coisas em um módulo e usá-lo em funções subsequentes:

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

Isso frequentemente é uma má ideia por alguns motivos:

Em primeiro lugar, a configuração de aplicativo é empurrada para a base de código com `dep1` e `dep2`. Isso é difícil de manter em bases de código maiores.

Segundo, inicializados estaticamente dados não devem incluir valores que não são thread-safe se seu componente em si usará vários threads. Isso é claramente violado por `dep3`.

Por fim, a inicialização do módulo compila em um construtor estático para a unidade de compilação inteiro. Se ocorrer algum erro na inicialização do valor de associação let nesse módulo, ele se manifesta como um `TypeInitializationException` , em seguida, que é armazenado em cache para o tempo de vida inteiro do aplicativo. Isso pode ser difícil de diagnosticar. Normalmente, há uma exceção interna que você pode tentar justificar, mas se não houver, em seguida, não há nenhuma informar o que é a causa raiz.

Em vez disso, use apenas uma classe simples para manter as dependências:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Isso permite que o seguinte:

1. Enviar por push qualquer estado dependente fora da API propriamente dita.
2. Configuração agora pode ser feita fora da API.
3. Erros na inicialização para valores dependentes não provavelmente se manifestar como um `TypeInitializationException`.
4. A API agora é mais fácil de testar.

## <a name="error-management"></a>Gerenciamento de erros

Gerenciamento de erros em sistemas de grande porte é um empreendimento sutil e complexo, e não há nenhum silver marcadores garantir que seus sistemas são tolerantes a falhas e se comportam bem. As diretrizes a seguir devem oferecer diretrizes esse espaço difíceis de navegar.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Representam os casos de erro e o estado ilegal em tipos intrínsecos ao seu domínio

Com o [uniões discriminadas](../language-reference/discriminated-unions.md), F# lhe dá a capacidade para representar o estado do programa com defeito no seu sistema de tipo. Por exemplo:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

Nesse caso, há três maneiras conhecidas que pode falhar, retirando dinheiro de uma conta bancária. Cada caso de erro é representado no tipo e pode, portanto, ser tratado com segurança em todo o programa.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Em geral, se você pode modelar as diferentes maneiras de que algo pode **falhar** em seu domínio, em seguida, código de tratamento de erro é não mais tratado como algo que você deve lidar com além do fluxo de programa regular. Ele é simplesmente uma parte do fluxo normal do programa e não é considerado **excepcionais**. Há duas vantagens principais para isso:

1. Ele é mais fácil manter seu domínio que as alterações ao longo do tempo.
2. Casos de erro são mais fáceis de teste de unidade.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Use as exceções quando erros não podem ser representados com tipos

Nem todos os erros podem ser representados em um domínio do problema. Esses tipos de falhas são *excepcionais* por natureza, portanto, a capacidade de gerar e capturar exceções em F#.

Primeiro, é recomendável que você leia as [diretrizes de Design de exceção](../../standard/design-guidelines/exceptions.md). Eles também são aplicáveis a F#.

A principal constrói disponíveis no F# para fins de geração de exceções devem ser considerados na seguinte ordem de preferência:

| Função | Sintaxe | Finalidade |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Gera um `System.ArgumentNullException` com o nome do argumento especificado. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Gera um `System.ArgumentException` com uma mensagem e o nome do argumento especificado. |
| `invalidOp` | `invalidOp "message"` | Gera um `System.InvalidOperationException` com a mensagem especificada. |
|`raise`| `raise (ExceptionType("message"))` | Mecanismo de propósito geral para lançar exceções. |
| `failwith` | `failwith "message"` | Gera um `System.Exception` com a mensagem especificada. |
| `failwithf` | `failwithf "format string" argForFormatString` | Gera um `System.Exception` com uma mensagem determinada pela cadeia de caracteres de formato e suas entradas. |

Use `nullArg`, `invalidArg` e `invalidOp` como o mecanismo para lançar `ArgumentNullException`, `ArgumentException` e `InvalidOperationException` quando apropriado.

O `failwith` e `failwithf` funções geralmente devem ser evitadas porque eles geram a base de `Exception` digitar, não uma exceção específica. De acordo o [diretrizes de Design de exceção](../../standard/design-guidelines/exceptions.md), ao acionar exceções mais específicas, quando possível.

### <a name="using-exception-handling-syntax"></a>Usando a sintaxe de manipulação de exceção

F#dá suporte a padrões de exceção por meio de `try...with` sintaxe:

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Reconciliar funcionalidade para executar diante de uma exceção com correspondência de padrão pode ser um pouco complicada, se você quiser manter o código limpo. Uma forma de lidar com isso é usar [padrões ativos](../language-reference/active-patterns.md) como um meio para funcionalidade de grupos ao redor de um caso de erro com uma exceção em si. Por exemplo, você pode consumir uma API que, quando ele gera uma exceção, inclui informações valiosas nos metadados de exceção. Um valor útil no corpo da exceção capturada dentro do padrão ativo o desempacotamento e retornando a que valor pode ser útil em algumas situações.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Não use monadic tratamento de erros para substituir as exceções

As exceções são vistas como um pouco um tabu em programação funcional. Na verdade, as exceções violam a pureza, portanto, é seguro considerá-las não é funcional. No entanto, isso ignora a realidade de qual código deve ser executado e que podem ocorrer erros de tempo de execução. Em geral, escreva o código na suposição de que a maioria das coisas não são puro nem total, para minimizar surpresas desagradáveis.

É importante considerar os seguintes pontos fortes/aspectos principais de exceções em relação à sua relevância e adequação no tempo de execução do .NET e o ecossistema de idioma como um todo:

1. Elas contêm informações detalhadas de diagnóstico, que é muito útil ao depurar um problema.
2. Eles são bem compreendidos, o tempo de execução e outras linguagens .NET.
3. Eles podem reduzir clichês significativos quando comparados com o código que sai do seu caminho para *evitar* exceções com a implementação de algum subconjunto dos seu semântica em uma base ad hoc.

Neste terceiro ponto é essencial. Para operações complexas não triviais, Falha ao usar exceções pode resultar em lidar com estruturas como este:

```fsharp
Result<Result<MyType, string>, string list>
```

Que pode facilmente levar a um código frágil, como correspondência de padrão em erros de "stringly tipificou":

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Além disso, pode ser tentador para se fazer qualquer exceção no desejo de uma função "simples" que retorna um tipo de "melhor":

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Infelizmente, `tryReadAllText` pode acionar diversas exceções com base em uma infinidade de coisas que podem ocorrer em um sistema de arquivos e, em seguida, esse código imediatamente descarta todas as informações sobre o que pode realmente estar errado em seu ambiente. Se você substituir esse código com um tipo de resultado, você estará para análise de mensagem de erro "stringly tipificou":

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

E colocar o próprio objeto de exceção no `Error` construtor apenas força você a lidar adequadamente com o tipo de exceção no site de chamada em vez de na função. Isso efetivamente cria exceções verificadas, o que são notoriamente unfun lidar com que um chamador de uma API.

Uma boa alternativa para os exemplos acima é capturar *específico* exceções e retorne um valor significativo no contexto de tal exceção. Se você modificar a `tryReadAllText` funcionam da seguinte maneira, `None` tem mais significado:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Em vez de funcionar como um catch-all, essa função agora manipulará corretamente o caso quando um arquivo não foi encontrado e atribuir esse significado para um retorno. Esse valor de retorno pode mapear para esse caso de erro, ao mesmo tempo não descartando todas as informações contextuais ou forçar os chamadores para lidar com um caso que pode não ser relevante nesse ponto no código.

Tipos, como `Result<'Success, 'Error>` são apropriados para operações básicas em que não estão aninhados, e F# tipos opcionais são perfeitos para que representa quando algo poderia retornar *algo* ou *nada*. Eles não são uma substituição para exceções, no entanto e não devem ser usados em uma tentativa de substituir as exceções. Em vez disso, eles devem ser aplicados criteriosamente para aspectos específicos do endereço de exceção e a política de gerenciamento de erro de maneiras de destino.

## <a name="partial-application-and-point-free-programming"></a>Aplicativo parcial e livre de ponto de programação

F#dá suporte a aplicativo parcial e, assim, várias maneiras de programar em um estilo livre de ponto. Isso pode ser benéfico para reutilização de código dentro de um módulo ou a implementação de algo, mas geralmente não é algo para expor publicamente. Em geral, livre de ponto de programação não é uma virtude por si só e pode adicionar uma barreira cognitiva significativa para as pessoas que não são imersos no estilo.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Não usar o aplicativo parcial e currying em APIs públicas

Com poucas exceções, o uso do aplicativo parcial em APIs públicas pode confundir os consumidores. Geralmente, `let`-associado valores em F# são de código **valores**, e não **valores de função**. Misturando valores e os valores de função pode resultar em Salvar um pequeno número de linhas de código em troca de uma grande quantidade de sobrecarga cognitiva, especialmente se combinado com operadores como `>>` a composição de funções.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Considere as implicações de ferramentas para a programação livre de ponto

Funções curried rotula seus argumentos. Isso tem implicações de ferramentas. Considere as duas funções a seguir:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Ambos são funções válidas, mas `funcWithApplication` é uma função na forma curried. Quando você focaliza em seus tipos em um editor, você verá isso:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

No site de chamada, as dicas de ferramenta em ferramentas como o Visual Studio não dará informações significativas sobre o que o `string` e `int` , na verdade, representam tipos de entrada.

Se você encontrar livre de ponto de código como `funcWithApplication` que é consumível publicamente, é recomendável fazer uma expansão de η completa para que as ferramentas podem escolher até diante nomes significativos para os argumentos.

Além disso, livre de ponto de código de depuração pode ser um desafio, se não impossível. Ferramentas de depuração contam com os valores associados a nomes (por exemplo, `let` associações) para que você possa inspecionar midway valores intermediários por meio da execução. Quando seu código não tem valores para inspecionar, não há nada para depurar. No futuro, as ferramentas de depuração podem evoluir para sintetizar esses valores com base nos caminhos executados anteriormente, mas não é uma boa ideia restringir as suas apostas *potencial* funcionalidade de depuração.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Considere a aplicação parcial como uma técnica para reduzir clichês interno

Em contraste com o ponto anterior, o aplicativo parcial é uma ferramenta excelente para reduzir o clichê dentro de um aplicativo ou os recursos internos de mais de uma API. Ele pode ser útil para a implementação das APIs mais complicadas, onde o clichê geralmente é um problema para lidar com teste de unidade. Por exemplo, o código a seguir mostra como é possível realizar quais estruturas de simulação mais lhe sem colocar uma dependência externa em uma estrutura e ter que aprender um relacionados bespoke API.

Por exemplo, considere a topografia de solução a seguir:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` pode expor o código como:

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

Teste de unidade `Transactions.doTransaction` em `ImplementationLogic.Tests.fspoj` é fácil:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

Aplicando parcialmente `doTransaction` com um contexto de simulação o objeto permite que você chame a função em todos os seus testes de unidade sem a necessidade de construir um contexto fictício cada vez:

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member __.TheFirstMember() = ...
        member __.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

Essa técnica não deve ser universalmente aplicada a toda sua base de código, mas é uma boa maneira de reduzir clichês para internals complicadas e os recursos internos de teste de unidade.

## <a name="access-control"></a>Controle de acesso

F#tem várias opções para [controle de acesso](../language-reference/access-control.md), herdados do que está disponível no tempo de execução .NET. Esses não são apenas pode ser usados para tipos – você pode usá-los para funções, muito.

* Prefira não -`public` tipos e membros até que você precisa deles para ser consumível publicamente. Isso minimiza também que alguns consumidores para.
* Tente manter todas as funcionalidades de auxiliar `private`.
* Considere o uso de `[<AutoOpen>]` em um módulo privado de funções auxiliares se tornarem vários.

## <a name="type-inference-and-generics"></a>Inferência de tipo e genéricos

Inferência de tipo pode economizar muito texto clichê de digitando. E generalização automática no F# compilador pode ajudá-lo a escrever mais códigos genéricos com quase nenhum esforço extra da sua parte. No entanto, esses recursos não estão universalmente boas.

* Considere a rotulagem de nomes de argumentos com tipos explícitos em APIs públicas e não dependem de inferência de tipo para isso.

    A razão para isso é que **você** deve estar no controle da forma de sua API, não o compilador. Embora o compilador pode fazer um bom trabalho ao inferir tipos para você, é possível ter a forma de sua alteração de API se os componentes internos que ele se baseia em alterou tipos. Isso pode ser o que você deseja, mas certamente, isso resultará em uma alteração de API significativa que os consumidores de downstream, em seguida, terá que lidar com. Em vez disso, se você controlar explicitamente a forma de sua API pública, você pode controlar essas alterações significativas. Em termos DDD, isso pode ser pensado como uma camada anticorrupção.

* É recomendável atribuir um nome significativo para seus argumentos genéricos.

    A menos que você está escrevendo código realmente genérico que não é específico para um domínio específico, um nome significativo pode ajudar outros programadores Noções básicas sobre o domínio em que eles estão trabalhando. Por exemplo, um parâmetro de tipo denominado `'Document` no contexto de interagir com um documento de banco de dados torna mais clara de que tipos de documento genérico podem ser aceitos pela função ou membro que você está trabalhando.

* Considere nomear os parâmetros de tipo genérico com PascalCase.

    Essa é a maneira geral para fazer coisas no .NET, portanto, é recomendável que você use PascalCase, em vez de snake_case ou camelCase.

Por fim, generalização automática nem sempre é uma vantagem para as pessoas que são novas no F# ou uma grande base de código. Há sobrecarga cognitiva usando componentes que são genéricos. Além disso, se automaticamente generalizadas funções não são usadas com diferentes tipos de entrada (apenas se eles se destinam a ser usada como tal, let), então não há nenhum benefício real para eles sendo genérico nesse ponto no tempo. Sempre considere se você estiver escrevendo código realmente beneficiarão de genérico.

## <a name="performance"></a>Desempenho

F#os valores são imutáveis por padrão, o que permite que você evite determinadas classes de bug (especialmente os que envolvem simultaneidade e paralelismo). No entanto, em alguns casos, para alcançar eficiência ideal (ou até mesmo razoável) de tempo de execução ou alocações de memória, um intervalo de trabalho pode melhor ser implementado usando in loco mutação do estado. Isso é possível em uma base de aceitação com F# com o `mutable` palavra-chave.

No entanto, usar `mutable` em F# pode parecer conflitante com a pureza funcional. Isso é bom, se você ajustar a pureza para as suas expectativas [transparência referencial](https://en.wikipedia.org/wiki/Referential_transparency). Transparência referencial - não pureza - é a meta final ao escrever F# funções. Isso permite que você escreva uma interface funcional ao longo de uma implementação baseada em mutação para o código crítico de desempenho.

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Encapsule o código mutável em interfaces imutáveis

Com transparência referencial como um objetivo, é essencial para escrever um código que não expõe o underbelly mutável das funções críticas de desempenho. Por exemplo, o código a seguir implementa o `Array.contains` funcionar a F# biblioteca principal:

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

Chamar essa função várias vezes não altera a matriz subjacente, nem exigem manter qualquer estado mutável em consumi-las. Ele é referencialmente transparente, mesmo que quase todas as linhas de código dentro dele usa mutação.

### <a name="consider-encapsulating-mutable-data-in-classes"></a>Considere o encapsulamento de dados mutáveis em classes

O exemplo anterior usou uma única função para encapsular operações usando dados mutáveis. Isso nem sempre é suficiente para a mais complexos conjuntos de dados. Considere os seguintes conjuntos de funções:

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

Esse código é o alto desempenho, mas ele expõe a estrutura de dados com base em mutação que os chamadores são responsáveis por manter. Isso pode ser encapsulado dentro de uma classe sem membros subjacentes que podem ser alterados:

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member __.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member __.Count = t.Count

    member __.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

`Closure1Table` encapsula a estrutura de dados com base em mutação subjacente, assim, sem forçar os chamadores para manter a estrutura de dados subjacente. Classes são uma maneira eficiente para encapsular dados e rotinas que são baseados em mutação sem expor os detalhes para os chamadores.

### <a name="prefer-let-mutable-to-reference-cells"></a>Prefira `let mutable` às células de referência

Células de referência são uma forma de representar a referência a um valor, em vez do valor em si. Embora possam ser usados para o código crítico de desempenho, eles geralmente não são recomendados. Considere o exemplo a seguir:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

O uso de uma célula de referência "polui" todo o código subsequente com a necessidade de cancelar a referência e referenciar novamente os dados subjacentes. Em vez disso, considere `let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

O ponto único de mutação no meio da expressão lambda, além de todos os outros códigos que envolve `acc` pode ser feito de forma que não é diferente para o uso de um normal `let`-valor imutável de limite. Isso tornará mais fácil alterar ao longo do tempo.

## <a name="object-programming"></a>Programação de objeto

F#tem suporte completo para objetos e orientada a objeto (OO) conceitos. Embora muitos conceitos OO sejam poderoso e útil, nem todos eles são ideais para uso. As listas a seguir oferecem orientação sobre categorias de recursos OO em um alto nível.

**Considere o uso desses recursos em muitas situações:**

* A notação de ponto (`x.Length`)
* Membros de instância
* Construtores implícitos
* Membros estáticos
* Notação do indexador (`arr.[x]`)
* Argumentos nomeados e opcionais
* Interfaces e implementações de interface

**Não alcançam primeiro para esses recursos, mas aplicá-las com cuidado quando eles são convenientes resolver um problema:**

* Sobrecarga de método
* Dados mutáveis encapsulados
* Operadores em tipos
* Propriedades automáticas
* Implementando `IDisposable` e `IEnumerable`
* Extensões de tipo
* Eventos
* Structs
* Delegados
* Enums

**Evite a esses recursos, a menos que você deve usá-los:**

* Hierarquias de herança com base no tipo e herança de implementação
* Valores nulos e `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Preferir a composição em vez de herança

[Composição em vez de herança](https://en.wikipedia.org/wiki/Composition_over_inheritance) é uma linguagem duradoura bom F# código pode aderir a. O princípio fundamental é que você não deve expor uma classe base e forçar os chamadores herdar da classe base para obter a funcionalidade.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Usar expressões de objeto para implementar interfaces, se você não precisa de uma classe

[Expressões de objeto](../language-reference/object-expressions.md) permitem que você implemente as interfaces em tempo real, associação a interface implementada como um valor sem a necessidade de fazer isso dentro de uma classe. Isso é conveniente, especialmente se você _apenas_ precisa implementar a interface e não precisa de uma classe completa.

Por exemplo, aqui está o código que é executado no [Ionide](http://ionide.io/) para fornecer uma ação de correção de código se você adicionou um símbolo que você não tiver um `open` instrução para:

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

Como não há nenhuma necessidade de uma classe ao interagir com a API de código do Visual Studio, expressões de objeto são uma ferramenta ideal para isso. Eles também são importantes para testes de unidade, quando você deseja criar um stub de uma interface com rotinas de teste de maneira ad hoc.

## <a name="type-abbreviations"></a>Abreviações de tipo

[Abreviações de tipo](../language-reference/type-abbreviations.md) são uma maneira conveniente de atribuir um rótulo para outro tipo, como uma assinatura de função ou um tipo mais complexo. Por exemplo, o alias a seguir atribui um rótulo para o que é necessário definir uma computação com [CNTK](https://docs.microsoft.com/cognitive-toolkit/), uma biblioteca de aprendizado profundo:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

O `Computation` nome é uma maneira conveniente para indicar qualquer função que corresponda à assinatura é um alias. Usar abreviações de tipo, como isso é conveniente e permite que o código mais sucinto.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Evitar o uso de abreviações de tipo para representar seu domínio

Apesar de abreviações de tipo são convenientes para dar um nome para assinaturas de função, eles podem ser confusos quando abreviando outros tipos. Considere essa abreviação:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Isso pode ser confuso de várias maneiras:

* `BufferSize` não é uma abstração; ele é apenas outro nome de um número inteiro.
* Se `BufferSize` é exposto em uma API pública, ele pode facilmente ser interpretados incorretamente para significar mais do que apenas `int`. Em geral, os tipos de domínio tem vários atributos para eles e não são tipos primitivos como `int`. Essa abreviação viola essa suposição.
* O uso de maiusculas e minúsculas de `BufferSize` (PascalCase) indica que esse tipo armazena mais dados.
* Este alias não oferece maior clareza, em comparação com o fornecimento de um argumento nomeado para uma função.
* A abreviação não se manifestará IL compilado; ele é um inteiro e esse alias é um constructo de tempo de compilação.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

Em resumo, as armadilhas com as abreviações de tipo são que eles sejam **não** abstrações sobre os tipos que eles são abreviando. No exemplo anterior, `BufferSize` é apenas um `int` nos bastidores, com nenhum dado adicional, nem todos os benefícios do sistema de tipo, além de quais `int` já tem.
