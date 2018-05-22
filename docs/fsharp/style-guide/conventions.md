---
title: 'Convenções de codificação do F #'
description: 'Saiba mais idiomas e as diretrizes gerais ao escrever código F #.'
ms.date: 05/14/2018
ms.openlocfilehash: d1f47f821887dabcdbc5d9406e90213fe8fafda5
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2018
---
# <a name="f-coding-conventions"></a>Convenções de codificação do F #

As seguintes convenções são formuladas com experiência de trabalhar com grandes F # bases de código. O [cinco princípios de código F # bom](index.md#five-principles-of-good-f-code) são a base de cada recomendação. Estão relacionadas a [diretrizes de design do componente F #](component-design-guidelines.md), mas são aplicáveis a qualquer código F #, não apenas componentes, como bibliotecas.

## <a name="organizing-code"></a>Organização de código

F # apresenta duas maneiras principais de organizar código: módulos e namespaces. Elas são semelhantes, mas têm as seguintes diferenças:

* Namespaces são compilados como namespaces .NET. Módulos são compilados como classes estáticas.
* Namespaces são sempre de nível superior. Módulos podem ser aninhada dentro de outros módulos e de alto nível.
* Namespaces podem abranger vários arquivos. Módulos não podem.
* Os módulos podem ser decorados com `[<RequireQualifiedAccess>]` e `[<AutoOpen>]`.

As diretrizes a seguir ajudará você a usá-las para organizar seu código.

### <a name="prefer-namespaces-at-the-top-level"></a>Preferir namespaces no nível superior

Para qualquer código publicamente consumível, namespaces são preferenciais para módulos no nível superior. Como eles são compilados como namespaces .NET, eles são consumíveis a partir de c# com nenhum problema.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

Usando um módulo de nível superior não pode ser diferente quando chamado apenas de F #, mas para c# consumidores, os chamadores podem surpreso por ter que qualificar `MyClass` com o `MyCode` módulo.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Aplicar cuidadosamente `[<AutoOpen>]`

O `[<AutoOpen>]` construção pode poluir o escopo do que está disponível a chamadores e a resposta para onde algo vêm é "magic". Isso geralmente não é bom. Uma exceção a essa regra é a biblioteca principal do F # em si (embora esse fato também é um pouco controverso).

No entanto, é uma conveniência se você tem funcionalidade auxiliar para uma API pública que você deseja organizar separadamente dessa API pública.

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

Isso lhe permite detalhes de implementação de separado corretamente na API pública de uma função sem ter que qualificar totalmente um auxiliar de cada vez que você chamá-lo.

Além disso, expor métodos de extensão e construtores de expressões no nível do namespace pode ser organizado expresso com `[<AutoOpen>]`.

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Use `[<RequireQualifiedAccess>]` sempre que os nomes podem entrar em conflito, ou se você achar ajuda com legibilidade

Adicionando o `[<RequireQualifiedAccess>]` atributo para um módulo indica que o módulo não pode ser aberto e que as referências aos elementos do módulo exigem explícita qualificado acesso. Por exemplo, o `Microsoft.FSharp.Collections.List` módulo tem esse atributo.

Isso é útil quando funções e os valores no módulo têm nomes que possam entrar em conflito com nomes em outros módulos. Exigir acesso qualificado pode aumentar significativamente a facilidade de manutenção de longo prazo e evolvability de uma biblioteca.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Classificação `open` instruções topologicamente

Em F #, a ordem das declarações é importante, inclusive com `open` instruções. Isso é diferente de c#, onde o efeito de `using` e `using static` é independente da ordenação dessas instruções em um arquivo.

Em F #, porque podem ser sombra de elementos abertos em um escopo de outras pessoas já está presente. Isso significa que a reordenação `open` instruções podem alterar o significado do código. Como resultado, a classificação de ordem alfanumérica (ou pseudorandomly) geralmente não é recomendada, fim de que você gerar um comportamento diferente que você esperava.

Em vez disso, recomendamos que você classificar [topologicamente](https://en.wikipedia.org/wiki/Topological_sorting); ou seja, solicitar sua `open` instruções na ordem em que _camadas_ do sistema são definidos. Fazendo alfanumérico de classificação em diferentes camadas topológicas também pode ser considerado.

Por exemplo, aqui está a classificação topológicas do F # compilador serviço público API arquivo:

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

Observe que uma quebra de linha separa topológicas camadas, com cada camada que estão sendo classificada ordem alfanumérica posteriormente. Isso organiza corretamente código sem sombreamento acidentalmente valores.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Usar classes para conter valores que têm efeitos colaterais

Há muitas vezes quando a inicialização de um valor pode ter efeitos colaterais, como criar uma instância de um contexto para um banco de dados ou outro recurso remoto. É tentador inicializar itens em um módulo e usá-lo em funções subsequentes:

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

Isso geralmente é uma boa ideia por alguns motivos:

Primeiro, a configuração de aplicativo é empurrada para a base de código com `dep1` e `dep2`. Isso é difícil de manter em bases de código maior.

Dados estaticamente inicializados segundo não devem incluir valores que não são thread-safe se o componente se usar vários threads. Isso é claramente violado por `dep3`.

Por fim, inicialização do módulo compila em um construtor estático para a unidade de compilação inteira. Se ocorrer algum erro na inicialização do valor de limite permitem em que o módulo, ele se manifesta como um `TypeInitializationException` , em seguida, que é armazenado em cache para todo o tempo de vida do aplicativo. Isso pode ser difícil diagnosticar. Normalmente, não há uma exceção interna que você pode tentar argumentar sobre, mas se não houver, em seguida, não há nenhum informando o que é a causa raiz.

Em vez disso, use apenas uma classe simples para manter dependências:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Isso permite que o seguinte:

1. Enviar por push qualquer estado dependente fora a própria API.
2. Configuração agora pode ser feita fora da API.
3. Erros na inicialização para valores dependentes não são provavelmente manifeste como um `TypeInitializationException`.
4. A API agora é mais fácil de testar.

## <a name="error-management"></a>Gerenciamento de erros

Gerenciamento de erro em grandes sistemas é um desafio complexo e sutis e não há nenhum prata marcadores garantir que seus sistemas são tolerantes a falhas e se comportam bem. As diretrizes a seguir devem oferecer diretrizes navegar neste espaço difícil.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Representam os casos de erro e o estado inválido em tipos intrínsecos ao seu domínio

Com [uniões discriminada](../language-reference/discriminated-unions.md), F # oferece a capacidade de representar o estado do programa defeituoso no seu sistema de tipo. Por exemplo:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

Nesse caso, há três maneiras de conhecidos retirando dinheiro de uma conta bancária pode falhar. Cada caso de erro é representado no tipo e pode, portanto, ser tratado com segurança em todo o programa.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Em geral, se você pode modelar as diferentes maneiras que algo pode **falha** em seu domínio, em seguida, código de tratamento de erros é não mais tratados como algo que você deve lidar com além de fluxo normal do programa. Ele é simplesmente uma parte do fluxo normal do programa e não é considerado **excepcional**. Há duas vantagens principais para isso:

1. É mais fácil de manter como seu domínio é alterado ao longo do tempo.
2. Casos de erro são mais fáceis de teste de unidade.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Usar exceções quando erros não podem ser representados com tipos

Nem todos os erros podem ser representados em um domínio do problema. Esses tipos de falhas são *excepcional* por natureza, portanto, a capacidade de gerar e capturar exceções em F #.

Primeiro, é recomendável que você leia o [diretrizes de Design de exceção](../../standard/design-guidelines/exceptions.md). Eles também são aplicáveis para F #.

As principais construções disponíveis em F # para fins de gerar exceções devem ser consideradas na seguinte ordem de preferência:

| Função | Sintaxe | Finalidade |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Gera um `System.ArgumentNullException` com o nome do argumento especificado. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Gera um `System.ArgumentException` com uma mensagem e o nome do argumento especificado. |
| `invalidOp` | `invalidOp "message"` | Gera um `System.InvalidOperationException` com a mensagem especificada. |
|`raise`| `raise (ExceptionType("message"))` | Mecanismo de finalidade geral para lançar exceções. |
| `failwith` | `failwith "message"` | Gera um `System.Exception` com a mensagem especificada. |
| `failwithf` | `failwithf "format string" argForFormatString` | Gera um `System.Exception` com uma mensagem determinada, a cadeia de caracteres de formato e suas entradas. |

Use `nullArg`, `invalidArg` e `invalidOp` como o mecanismo para lançar `ArgumentNullException`, `ArgumentException` e `InvalidOperationException` quando apropriado.

O `failwith` e `failwithf` funções geralmente devem ser evitadas porque elas geram a base de `Exception` de tipo não é uma exceção específica. Conforme o [diretrizes de Design de exceção](../../standard/design-guidelines/exceptions.md), você deseja gerar exceções mais específicas, quando possível.

### <a name="using-exception-handling-syntax"></a>Usando a sintaxe de manipulação de exceção

F # oferece suporte a padrões de exceção por meio de `try...with` sintaxe:

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Reconciliar funcionalidade para executar caso ocorra uma exceção com a correspondência de padrão pode ser um pouco difícil, se você deseja manter o código de limpeza. Um modo para lidar com isso é usar [padrões ativos](../language-reference/active-patterns.md) como um meio de funcionalidade de grupos ao redor de um caso de erro com uma exceção em si. Por exemplo, você pode consumir uma API que, quando ele lança uma exceção, inclui informações importantes nos metadados de exceção. Um valor útil no corpo da exceção capturada dentro do padrão ativo o desempacotamento e retornando que o valor pode ser útil em algumas situações.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Não use monadic tratamento de erros para substituir as exceções

Exceções são vistas como um pouco um tabu em programação funcional. Na verdade, exceções violam pureza, portanto, é seguro considerar não é funcional. No entanto, isso ignora a realidade de qual código deve ser executado e que podem ocorrer erros de tempo de execução. Em geral, grave o código na suposição de que a maioria das tarefas são puro nem total, para minimizar as surpresas desagradáveis.

É importante considerar os seguintes pontos fortes/aspectos principais de exceções em relação à sua relevância e conveniência no tempo de execução do .NET e o ecossistema de qualquer idioma como um todo:

1. Elas contêm informações de diagnóstico detalhadas, que é muito útil ao depurar um problema.
2. Eles são bem compreendidos pelo tempo de execução e outras linguagens .NET.
3. Eles podem reduzir boilerplate significativa em comparação com o código que sai do seu caminho para *evitar* exceções implementando algum subconjunto dos seu semântica em uma base ad hoc.

Esse terceiro ponto é crítico. Para operações complexas não triviais, não use exceções pode resultar em lidar com estruturas como este:

```fsharp
Result<Result<MyType, string>, string list>
```

Facilmente, que pode levar a código frágil como padrões coincidentes em erros de "stringly digitado":

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Além disso, ele pode ser tentador assimilar qualquer exceção no desejo de uma função "simples" que retorna um tipo de "melhor":

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Infelizmente, `tryReadAllText` pode gerar várias exceções com base em uma infinidade de coisas que podem acontecer em um sistema de arquivos e, em seguida, esse código imediatamente descarta todas as informações sobre o que pode ser entrar errado em seu ambiente. Se você substituir esse código com um tipo de resultado, você está para análise de mensagem de erro "stringly digitado":

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

E colocar o próprio objeto de exceção no `Error` construtor apenas força lidar corretamente com o tipo de exceção no site de chamada em vez de na função. Isso efetivamente cria exceções verificadas, que são notoriamente unfun lidar com como um chamador de uma API.

É uma boa alternativa para os exemplos anteriores capturar *específico* exceções e retornar um valor significativo no contexto dessa exceção. Se você modificar o `tryReadAllText` funciona da seguinte maneira `None` tem um significado mais:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Em vez de funcionar como uma pega-tudo, essa função agora manipulará corretamente o caso quando um arquivo não foi encontrado e atribuir esse significado para retornar. Esse valor de retorno pode mapear para esse caso de erro, enquanto não descartar todas as informações contextuais ou forçar os chamadores para lidar com uma situação que não pode ser relevante nesse ponto no código.

Tipos, como `Result<'Success, 'Error>` são apropriadas para operações básicas de onde eles não são aninhados, e tipos F # opcionais são perfeitos para representar quando algo foi devolva *algo* ou *nada*. Eles não são uma substituição para exceções, porém e não devem ser usados em uma tentativa de substituir exceções. Em vez disso, eles devem ser aplicados criteriosamente para aspectos específicos de endereço de exceção e a política de gerenciamento de erro de maneiras de destino.

## <a name="partial-application-and-point-free-programming"></a>Aplicativo parcial e livre de ponto de programação

F # oferece suporte a aplicativo parcial e, assim, várias formas de programa em um estilo livre de ponto. Isso pode ser útil para reutilização de código dentro de um módulo ou a implementação de algo, mas geralmente não é algo para expor publicamente. Em geral, livre de ponto de programação não é um porque, por si só e pode adicionar uma barreira cognitiva significativa para as pessoas que não tenha o estilo.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Não usar o aplicativo parcial e currying em APIs públicas

Com poucas exceções, o uso do aplicativo parcial em APIs públicas pode confundir os consumidores. Normalmente, `let`-são valores de limite no código F # **valores**, não **valores de função**. Combinação de valores e valores de função juntos pode resultar em Salvar um pequeno número de linhas de código em troca de uma grande quantidade de sobrecarga cognitiva, especialmente se combinado com operadores, como `>>` para compor funções.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Considere as implicações de ferramentas para liberar o ponto de programação

Funções na forma curried não rótulo seus argumentos. Isso tem implicações de ferramentas. Considere as duas funções a seguir:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Ambos são funções válidas, mas `funcWithApplication` é uma função na forma curried. Quando você focaliza seus tipos em um editor, você verá:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

No site de chamada, dicas de ferramenta em ferramentas como o Visual Studio não fornecerá informações significativas sobre o que o `string` e `int` realmente representam tipos de entrada.

Se você encontrar livre de ponto de código como `funcWithApplication` que é consumível publicamente, é recomendável fazer uma expansão de η completa para que as ferramentas podem escolher até diante nomes significativos para argumentos.

Além disso, depurando livre de ponto de código pode ser um desafio, se não impossível. Ferramentas de depuração contam com os valores associados aos nomes (por exemplo, `let` associações) para que você pode inspecionar o Centro de valores intermediários por meio da execução. Quando seu código não tem valores para inspecionar, não há nada para depurar. No futuro, as ferramentas de depuração podem evoluir para sintetizar esses valores com base em caminhos executados anteriormente, mas não é uma boa ideia para restringir suas opções em *potencial* funcionalidades de depuração.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Considere a possibilidade de aplicativo parcial como uma técnica para reduzir boilerplate interno

Em contraste com o ponto anterior, o aplicativo parcial é uma ferramenta bons para reduzir boilerplate dentro de um aplicativo ou os recursos internos de mais de uma API. Ele pode ser útil para a implementação das APIs mais complicado, onde boilerplate geralmente é um problema para lidar com teste de unidade. Por exemplo, o código a seguir mostra como é possível realizar quais estruturas fictícias mais proporcionam sem colocar uma dependência externa em tal estrutura e aprender um relacionados bespoke API.

Por exemplo, considere a topografia de solução a seguir:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` pode expor o código, como:

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

Aplicando parcialmente `doTransaction` com um contexto de simulação o objeto permite que você chame a função em todos os testes de unidade sem a necessidade de construir um contexto fictícios cada vez:

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

Essa técnica não deve ser aplicada universalmente a sua base de código inteiro, mas é uma boa maneira de reduzir clichê para operações internas complicadas e os recursos internos de teste de unidade.

## <a name="access-control"></a>Controle de acesso

F # tem várias opções para [controle de acesso](../language-reference/access-control.md), herdado do que está disponível no tempo de execução .NET. Eles não são úteis apenas para tipos de-você pode usá-los para funções, muito.

* Preferir não`public` tipos e membros até que você precisa para ser consumível publicamente. Isso também minimiza que alguns consumidores para
* Tentar manter todas as funcionalidades de auxiliar `private`.
* Considere o uso de `[<AutoOpen>]` em um módulo privado de funções auxiliares se eles se tornarem vários.

## <a name="type-inference-and-generics"></a>Inferência de tipo e genéricos

Inferência de tipo pode salvar da digitação muita boilerplate. E generalização automática no compilador F # pode ajudá-lo a escrever mais códigos genéricos com quase nenhum esforço adicional de sua parte. No entanto, esses recursos não são bons universalmente.

* Considere a rotulagem de nomes de argumentos com tipos explícitos em APIs públicas e não dependem de inferência de tipo para isso.

    A razão para isso é que **você** devem estar no controle da forma de sua API, não o compilador. Embora o compilador pode fazer um bom trabalho em inferindo tipos para você, é possível ter a forma de sua alteração de API se os componentes internos depende alterou tipos. Isso pode ser o que você deseja, mas provavelmente resultará em uma alteração de API de quebra que os consumidores de downstream terá de lidar com. Em vez disso, se você controlar a forma de sua API pública explicitamente, você pode controlar essas alterações significativas. Em termos DDD, isso pode ser pensado como uma camada contra dano.

* É recomendável atribuir um nome significativo para seus argumentos genéricos.

    A menos que você está escrevendo código realmente genérico que não é específico para um domínio específico, um nome significativo pode ajudar outros programadores Noções básicas sobre o domínio que está trabalhando. Por exemplo, um parâmetro de tipo denominado `'Document` no contexto de interagir com um documento de banco de dados torna mais claro de que tipos de documento genérico podem ser aceito para a função ou um membro que você está trabalhando com.

* Considere a possibilidade de nomenclatura de parâmetros de tipo genérico com PascalCase.

    Essa é a maneira geral para fazer coisas no .NET, portanto, é recomendável que você use PascalCase em vez de snake_case ou camelCase.

Por fim, generalização automática nem sempre é um recurso para as pessoas que são novos para F # ou uma grande base de código. Há sobrecarga cognitiva usando componentes genéricos. Além disso, se automaticamente generalizadas funções não são usadas com diferentes tipos de entrada (permitem apenas se eles se destinam a ser usada como tal), não há nenhum benefício real-los sendo genérico no momento. Sempre considere se o código que você está escrevendo realmente se beneficiam sendo genérico.

## <a name="performance"></a>Desempenho

Valores de F # são imutáveis por padrão, o que permite que você evite determinadas classes de bugs (especialmente as que envolvem simultaneidade e paralelismo). No entanto, em alguns casos, para obter eficiência ideal (ou até mesmo razoável) de tempo de execução ou as alocações de memória, um intervalo de trabalho pode melhor ser implementado usando mutação no local do estado. Isso é possível em uma base de aceitação com F # com o `mutable` palavra-chave.

No entanto, usar `mutable` em F # podem achar acordo pureza funcional. Isso é bom, se você ajustar as expectativas de pureza para [transparência referencial](https://en.wikipedia.org/wiki/Referential_transparency). Transparência referencial - não pureza - é o objetivo final ao escrever funções F #. Isso permite que você escreva uma interface funcional em uma implementação baseada em mutação para código crítico de desempenho.

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Encapsular um código mutável interfaces imutáveis

Com transparência referencial como uma meta, é essencial para escrever código que não expõe o underbelly mutável de funções críticas de desempenho. Por exemplo, o código a seguir implementa a `Array.contains` função na biblioteca F # principais:

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

Chamar essa função várias vezes alterará a matriz subjacente nem exigem manter qualquer estado mutável no consumi-las. É origem transparente, mesmo que quase todas as linhas de código em seu usa mutação.

### <a name="consider-encapsulating-mutable-data-in-classes"></a>Considere a possibilidade de encapsulamento de dados mutável em classes

O exemplo anterior usado uma única função para encapsular operações usando dados mutável. Isso sempre não é suficiente para mais conjuntos de dados. Considere os seguintes conjuntos de funções:

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

Esse código é funcional, mas expõe a estrutura de dados com base em mutação que os chamadores são responsáveis por manter. Isso pode ser encapsulado dentro de uma classe com não membros subjacentes que pode alterar:

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

`Closure1Table` encapsula a estrutura de dados com base em mutação subjacente, assim, não forçar chamadores para manter a estrutura de dados subjacente. Classes são uma maneira eficiente para encapsular dados e rotinas que são baseados em mutação sem expor os detalhes para chamadores.

### <a name="prefer-let-mutable-to-reference-cells"></a>Preferir `let mutable` às células de referência

As células de referência são uma forma de representar a referência a um valor em vez do próprio valor. Embora possam ser usados para código crítico em termos de desempenho, eles geralmente não são recomendados. Considere o exemplo a seguir:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

O uso de uma célula de referência "polui" todo o código subsequente com precisar cancelar e referenciar novamente os dados subjacentes. Em vez disso, considere a possibilidade de `let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

O ponto único de mutação no meio da expressão lambda, além de todos os outros códigos toca `acc` pode fazer isso de forma que não é diferente para o uso de um normal `let`-valor imutável associada. Isso tornará mais fácil mudar ao longo do tempo.

## <a name="object-programming"></a>Objeto de programação

F # tem total suporte para objetos e conceitos (OO) e orientada a objeto. Embora muitos conceitos OO são úteis e eficientes, nem todos eles são ideais para uso. As listas a seguir oferecem orientação sobre categorias de recursos OO em um alto nível.

**Considere o uso desses recursos em muitas situações:**

* A notação de ponto (`x.Length`)
* Membros de instância
* Construtores implícita
* Membros estáticos
* Notação de indexador (`arr.[x]`)
* Argumentos nomeados e opcionais
* Interfaces e implementações de interface

**Não acessar esses recursos pela primeira vez, mas aplicá-las cuidado quando for convenientes resolver um problema:**

* Sobrecarga de método
* Dados mutáveis encapsulados
* Operadores em tipos
* Propriedades automática
* Implementando `IDisposable` e `IEnumerable`
* Extensões de tipo
* Eventos
* Structs
* Delegados
* Enums

**Em geral, evite esses recursos, a menos que você deve usá-los:**

* Hierarquias de herança com base no tipo e a implementação de herança
* Valores nulos e `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Prefira a herança de composição

[Composição de herança](https://en.wikipedia.org/wiki/Composition_over_inheritance) é um idioma longa pode cumprir bom código F #. O princípio fundamental é que você não deve expor uma classe base e forçar os chamadores herdam da classe base para obter funcionalidade.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Usar expressões de objeto para implementar interfaces se não precisar de uma classe

[Expressões de objeto](../language-reference/object-expressions.md) permitem que você implemente as interfaces em tempo real, associação a interface implementada como um valor sem a necessidade de fazer isso dentro de uma classe. Isso é prático, especialmente se você _somente_ precisa implementar a interface e não precisam de uma classe completa.

Por exemplo, aqui está o código que é executado em [Ionide](http://ionide.io/) para fornecer uma ação de correção de código, se você tiver adicionado um símbolo que você não tem um `open` instrução para:

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

Como não é necessário para uma classe ao interagir com a API de código do Visual Studio, expressões de objeto são uma ferramenta ideal para isso. Eles também são úteis para teste de unidade, quando você quiser stub em uma interface com rotinas de teste de maneira ad hoc.

## <a name="type-abbreviations"></a>Abreviações de tipo

[Abreviações de tipo](../language-reference/type-abbreviations.md) são uma maneira conveniente para atribuir um rótulo para outro tipo, como uma assinatura de função ou um tipo mais complexo. Por exemplo, o alias a seguir atribui um rótulo para o que é necessário definir uma computação com [CNTK](https://www.microsoft.com/cognitive-toolkit/), um profundo aprendizado biblioteca:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

O `Computation` nome é uma maneira conveniente para indicar qualquer função que corresponda à assinatura que é um alias. Usando abreviações de tipo como isso é conveniente e permite que o código mais sucinto.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Evite usar abreviações de tipo para representar seu domínio

Embora as abreviações de tipo são convenientes para dar um nome para assinaturas de função, eles podem ser confusos quando abreviando outros tipos. Considere esta abreviação:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Isso pode ser confuso de várias maneiras:

* `BufferSize` não é uma abstração; ele é apenas outro nome de um número inteiro.
* Se `BufferSize` é exposto em uma API pública, ele pode facilmente ser interpretados incorretamente significa mais do que apenas `int`. Em geral, os tipos de domínio tem vários atributos a eles e não são tipos primitivos como `int`. Esta abreviação viola essa suposição.
* O uso de maiusculas e minúsculas de `BufferSize` (PascalCase) indica que esse tipo armazena mais dados.
* Este alias não oferece maior clareza, em comparação com o fornecimento de um argumento nomeado para uma função.
* A abreviação não será manifesto em IL compilado; ele é apenas um inteiro e esse alias é uma construção de tempo de compilação.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

Em resumo, as armadilhas com abreviações de tipo são que eles são **não** abstrações sobre os tipos que são abreviando. No exemplo anterior, `BufferSize` é apenas um `int` nos bastidores, com nenhum dado adicionais nem qualquer benefícios do sistema de tipo, além de quais `int` já tem.
