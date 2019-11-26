---
title: Convenções de codificação do F#
description: Aprenda as diretrizes gerais e os idiomas ao F# escrever código.
ms.date: 11/04/2019
ms.openlocfilehash: 60eff6392d71caa54eeb438f2f6ba9db910f1bc1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978219"
---
# <a name="f-coding-conventions"></a>Convenções de codificação do F#

As convenções a seguir são formuladas de experiência de trabalho F# com grandes bases de código. Os [cinco princípios de um F# bom código](index.md#five-principles-of-good-f-code) são a base de cada recomendação. Eles estão relacionados às [ F# diretrizes de design de componentes](component-design-guidelines.md), mas são aplicáveis a qualquer F# código, não apenas a componentes como bibliotecas.

## <a name="organizing-code"></a>Organizando o código

F#apresenta duas maneiras principais de organizar código: módulos e namespaces. Eles são semelhantes, mas têm as seguintes diferenças:

* Os namespaces são compilados como namespaces .NET. Os módulos são compilados como classes estáticas.
* Os namespaces são sempre de nível superior. Os módulos podem ser de nível superior e aninhados dentro de outros módulos.
* Os namespaces podem abranger vários arquivos. Os módulos não podem.
* Os módulos podem ser decorados com `[<RequireQualifiedAccess>]` e `[<AutoOpen>]`.

As diretrizes a seguir ajudarão você a usá-las para organizar seu código.

### <a name="prefer-namespaces-at-the-top-level"></a>Preferir namespaces no nível superior

Para qualquer código de consumo publicamente, os namespaces são preferenciais aos módulos no nível superior. Como eles são compilados como namespaces do .NET, eles são consumíveis de C# sem problemas.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

Usar um módulo de nível superior pode não aparecer diferente quando chamado apenas de F#, mas para C# consumidores, os chamadores podem ficar surpresos ao se qualificar`MyClass`com o módulo`MyCode`.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Aplicar cuidadosamente `[<AutoOpen>]`

A construção de `[<AutoOpen>]` pode poluir o escopo do que está disponível para os chamadores e a resposta para onde algo vem é "mágica". Isso geralmente não é algo bom. Uma exceção a essa regra é a F# própria biblioteca principal (embora esse fato também seja um pouco controverso).

No entanto, é uma conveniência se você tiver a funcionalidade auxiliar para uma API pública que você deseja organizar separadamente dessa API pública.

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

Isso permite que você separe de forma limpa os detalhes de implementação da API pública de uma função sem precisar qualificar totalmente um auxiliar cada vez que chamá-lo.

Além disso, a exposição de métodos de extensão e construtores de expressão no nível de namespace pode ser expressamente expressa com `[<AutoOpen>]`.

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Use `[<RequireQualifiedAccess>]` sempre que os nomes puderem entrar em conflito ou se você achar que ele ajuda na legibilidade

Adicionar o atributo `[<RequireQualifiedAccess>]` a um módulo indica que o módulo pode não estar aberto e que as referências aos elementos do módulo exigem acesso qualificado explícito. Por exemplo, o módulo `Microsoft.FSharp.Collections.List` tem esse atributo.

Isso é útil quando as funções e os valores no módulo têm nomes que provavelmente estão em conflito com nomes em outros módulos. Exigir acesso qualificado pode aumentar muito a manutenção e o evolucionabilidade de longo prazo de uma biblioteca.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Classificar instruções de `open` topologicamente

No F#, a ordem das declarações é importante, incluindo com `open`instruções. Isso é diferente C#de, onde o efeito de`using`e`using static`é independente da ordenação dessas instruções em um arquivo.

No F#, os elementos abertos em um escopo podem sombrear outros já presentes. Isso significa que reordenar `open` instruções poderia alterar o significado do código. Como resultado, qualquer classificação arbitrária de todas as instruções de `open` (por exemplo, alfanuméricamente) geralmente não é recomendada, última você gera um comportamento diferente que você pode esperar.

Em vez disso, recomendamos que você os classifique [topologicamente](https://en.wikipedia.org/wiki/Topological_sorting); ou seja, ordene suas instruções de `open` na ordem em que as _camadas_ do seu sistema estão definidas. A classificação alfanumérica em diferentes camadas de topológica também pode ser considerada.

Como exemplo, aqui está a classificação topológica para o arquivo F# de API pública do serviço de compilador:

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

Observe que uma quebra de linha separa as camadas topológica, com cada camada sendo classificada alfanuméricamente depois. Isso organiza corretamente o código sem sombrear valores de forma acidental.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Usar classes para conter valores que têm efeitos colaterais

Há muitas ocasiões em que a inicialização de um valor pode ter efeitos colaterais, como instanciar um contexto para um banco de dados ou outro recurso remoto. É tentador inicializar essas coisas em um módulo e usá-las em funções subsequentes:

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

Geralmente, essa é uma má ideia por alguns motivos:

Primeiro, a configuração do aplicativo é enviada por push para a base de código com `dep1` e `dep2`. Isso é difícil de ser mantido em bases de código maiores.

Segundo, os dados inicializados estaticamente não devem incluir valores que não sejam thread-safe se o seu componente usar vários threads. Isso é claramente violado por `dep3`.

Por fim, a inicialização do módulo é compilada em um construtor estático para toda a unidade de compilação. Se ocorrer algum erro na inicialização de valor de Let associado nesse módulo, ele será manifestado como um `TypeInitializationException` que, em seguida, é armazenado em cache durante todo o tempo de vida do aplicativo. Isso pode ser difícil de diagnosticar. Normalmente, há uma exceção interna com a qual você pode tentar se deparar, mas se não houver, não há nenhum informando qual é a causa raiz.

Em vez disso, basta usar uma classe simples para manter as dependências:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Isso permite o seguinte:

1. Enviar por push qualquer estado dependente fora da própria API.
2. Agora, a configuração pode ser feita fora da API.
3. Erros na inicialização de valores dependentes provavelmente não serão manifestados como um `TypeInitializationException`.
4. Agora, a API é mais fácil de testar.

## <a name="error-management"></a>Gerenciamento de erros

O gerenciamento de erros em sistemas grandes é um esforço complexo e nuance, e não há nenhum marcador prata para garantir que seus sistemas sejam tolerantes a falhas e se comporte bem. As diretrizes a seguir devem oferecer orientações para navegar nesse espaço difícil.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Representar casos de erro e estado ilegal em tipos intrínsecos ao seu domínio

Com [uniões discriminadas](../language-reference/discriminated-unions.md), F# o oferece a capacidade de representar o estado do programa com falha em seu sistema de tipos. Por exemplo:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

Nesse caso, há três maneiras conhecidas de retirar dinheiro de uma conta bancária. Cada caso de erro é representado no tipo e, portanto, pode ser tratado com segurança em todo o programa.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

Em geral, se você puder modelar as diferentes maneiras pelas quais algo pode **falhar** em seu domínio, o código de tratamento de erros não será mais tratado como algo com o qual você deve lidar, além do fluxo de programa normal. Ele é simplesmente parte do fluxo normal do programa e não é considerado **excepcional**. Há dois benefícios principais para isso:

1. É mais fácil de manter à medida que seu domínio muda ao longo do tempo.
2. Casos de erro são mais fáceis de testar unidade.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Usar exceções quando erros não puderem ser representados com tipos

Nem todos os erros podem ser representados em um domínio com problema. Esses tipos de falhas são *excepcionais* por natureza, portanto, a capacidade de gerar e capturar exceções no F#.

Primeiro, é recomendável que você leia as [diretrizes de design de exceção](../../standard/design-guidelines/exceptions.md). Elas também são aplicáveis ao F#.

As principais construções disponíveis no F# para fins de geração de exceções devem ser consideradas na seguinte ordem de preferência:

| Função | Sintaxe | Finalidade |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Gera um `System.ArgumentNullException` com o nome do argumento especificado. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Gera um `System.ArgumentException` com um nome de argumento e uma mensagem especificados. |
| `invalidOp` | `invalidOp "message"` | Gera um `System.InvalidOperationException` com a mensagem especificada. |
|`raise`| `raise (ExceptionType("message"))` | Mecanismo de finalidade geral para lançar exceções. |
| `failwith` | `failwith "message"` | Gera um `System.Exception` com a mensagem especificada. |
| `failwithf` | `failwithf "format string" argForFormatString` | Gera um `System.Exception` com uma mensagem determinada pela cadeia de caracteres de formato e suas entradas. |

Use `nullArg`, `invalidArg` e `invalidOp` como mecanismo para gerar `ArgumentNullException`, `ArgumentException` e `InvalidOperationException` quando apropriado.

As funções `failwith` e `failwithf` geralmente devem ser evitadas porque geram o tipo de `Exception` base, não uma exceção específica. De acordo com as [diretrizes de design de exceção](../../standard/design-guidelines/exceptions.md), você deseja gerar exceções mais específicas quando puder.

### <a name="using-exception-handling-syntax"></a>Usando a sintaxe de tratamento de exceção

F#dá suporte a padrões de exceção por meio da sintaxe de`try...with`:

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

A reconciliação da funcionalidade a ser executada diante de uma exceção com correspondência de padrões pode ser um pouco complicada se você quiser manter a limpeza do código. Uma forma de lidar com isso é usar [padrões ativos](../language-reference/active-patterns.md) como um meio de agrupar a funcionalidade em torno de um caso de erro com uma exceção em si. Por exemplo, você pode estar consumindo uma API que, quando ela gera uma exceção, inclui informações valiosas nos metadados de exceção. Desencapsular um valor útil no corpo da exceção capturada dentro do padrão ativo e retornar esse valor pode ser útil em algumas situações.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Não use o tratamento de erros monadic para substituir exceções

As exceções são vistas como um pouco da na programação funcional. Na verdade, as exceções violam a pureza, portanto, é seguro considerá-las não muito funcionais. No entanto, isso ignora a realidade de onde o código deve ser executado e que podem ocorrer erros de tempo de execução. Em geral, escreva o código na suposição de que a maioria das coisas não é pura nem total, para minimizar surpresas desagradáveis.

É importante considerar os seguintes pontos fortes/aspectos principais de exceções em relação à sua relevância e à sua adequação no tempo de execução do .NET e no ecossistema entre linguagens como um todo:

1. Eles contêm informações detalhadas de diagnóstico, o que é muito útil ao depurar um problema.
2. Eles são bem compreendidos pelo tempo de execução e por outras linguagens .NET.
3. Eles podem reduzir um timbre significativo em comparação com o código que sai do seu caminho para *evitar* exceções implementando algum subconjunto de sua semântica em uma base ad hoc.

Esse terceiro ponto é crítico. Para operações complexas não triviais, a falha ao usar exceções pode resultar em lidar com estruturas como esta:

```fsharp
Result<Result<MyType, string>, string list>
```

Que pode facilmente levar a um código frágil como correspondência de padrões em erros de "tipo de cadeia de caracteres":

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

Além disso, pode ser tentador assimilar qualquer exceção no desejo de uma função "simples" que retorna um tipo "interessante":

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Infelizmente, `tryReadAllText` pode lançar várias exceções com base na infinidade de coisas que podem ocorrer em um sistema de arquivos, e esse código descarta as informações sobre o que pode realmente estar errado em seu ambiente. Se você substituir esse código por um tipo de resultado, você voltará à análise da mensagem de erro "tipo de cadeia de caracteres":

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

E colocar o objeto de exceção em si no construtor de `Error` apenas força você a lidar corretamente com o tipo de exceção no site de chamada em vez de na função. Fazer isso efetivamente cria exceções marcadas, que são notoriamente unfun para lidar como um chamador de uma API.

Uma boa alternativa para os exemplos acima é capturar exceções *específicas* e retornar um valor significativo no contexto dessa exceção. Se você modificar a função `tryReadAllText` da seguinte maneira, `None` terá mais significado:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Em vez de funcionar como um problema, essa função agora tratará corretamente o caso quando um arquivo não foi encontrado e atribuirá esse significado a um retorno. Esse valor de retorno pode mapear para esse caso de erro, sem descartar nenhuma informação contextual ou forçar os chamadores a lidar com um caso que pode não ser relevante nesse ponto no código.

Tipos como `Result<'Success, 'Error>` são apropriados para operações básicas em que não estão aninhados e F# tipos opcionais são perfeitos para representar quando algo poderia retornar *algo* ou *nada*. Eles não são uma substituição de exceções, porém, e não devem ser usados em uma tentativa de substituir exceções. Em vez disso, eles devem ser aplicados criteriosamente para abordar aspectos específicos da política de gerenciamento de erros e exceções de formas direcionadas.

## <a name="partial-application-and-point-free-programming"></a>Aplicativo parcial e programação sem ponto

F#dá suporte a aplicativos parciais e, portanto, várias maneiras de programar em um estilo sem ponto. Isso pode ser benéfico para a reutilização de código dentro de um módulo ou a implementação de algo, mas geralmente não é algo a ser exposto publicamente. Em geral, a programação sem ponto não é uma questão em si própria e pode adicionar uma barreira cognitiva significativa para pessoas que não estão imersos no estilo.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>Não use aplicativos parciais e currying em APIs públicas

Com pouca exceção, o uso de aplicativos parciais em APIs públicas pode ser confuso para os consumidores. Normalmente, valores associados a `let`no F# código são **valores**, não **valores de função**. Misturar valores e valores de função pode resultar em salvar um pequeno número de linhas de código no Exchange para uma grande sobrecarga de cognitiva, especialmente se combinado com operadores como `>>` para compor funções.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Considere as implicações de ferramentas para a programação sem ponto

As funções na forma curried não rotulam seus argumentos. Isso tem implicações de ferramentas. Considere as duas funções a seguir:

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Ambas são funções válidas, mas `funcWithApplication` é uma função na forma curried. Ao passar o mouse sobre seus tipos em um editor, você verá:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

No local de chamada, as dicas de ferramenta em ferramentas como o Visual Studio não fornecerão informações significativas sobre o que a `string` e `int` tipos de entrada realmente representam.

Se você encontrar um código sem ponto como `funcWithApplication` que é publicamente consumível, é recomendável fazer uma η completa para que as ferramentas possam escolher nomes significativos para os argumentos.

Além disso, a depuração de código sem ponto pode ser desafiadora, se não impossível. As ferramentas de depuração dependem de valores associados aos nomes (por exemplo, associações de `let`) para que você possa inspecionar valores intermediários no centro por meio da execução. Quando seu código não tem valores a serem inspecionados, não há nada a ser depurado. No futuro, as ferramentas de depuração podem evoluir para resumir esses valores com base em caminhos executados anteriormente, mas não é uma boa ideia envolver suas opções em *potencial* funcionalidade de depuração.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Considere o aplicativo parcial como uma técnica para reduzir o timbre interno

Em contraste com o ponto anterior, o aplicativo parcial é uma excelente ferramenta para reduzir o texto clichê dentro de um aplicativo ou os detalhes internos de uma API. Pode ser útil para o teste de unidade da implementação de APIs mais complicadas, em que o clichê é muitas vezes um problema para lidar. Por exemplo, o código a seguir mostra como você pode realizar o que a maioria das estruturas fictícias fornece sem tirar uma dependência externa de tal estrutura e ter que aprender uma API do bespoke relacionada.

Por exemplo, considere a topografia de solução a seguir:

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` pode expor código como:

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

O teste de unidade `Transactions.doTransaction` no `ImplementationLogic.Tests.fsproj` é fácil:

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

A aplicação parcial de `doTransaction` com um objeto de contexto fictício permite chamar a função em todos os testes de unidade sem a necessidade de construir um contexto fictício a cada vez:

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

Essa técnica não deve ser aplicada universalmente a toda a base de código, mas é uma boa maneira de reduzir o texto clichê para os internos complicados e os testes de unidade desses elementos internos.

## <a name="access-control"></a>Controle de acesso

F#tem várias opções para o [controle de acesso](../language-reference/access-control.md), herdadas do que está disponível no tempo de execução do .net. Eles não são apenas utilizáveis para tipos – você também pode usá-los para funções.

* Prefira tipos e membros não`public` até que você precise que eles sejam publicamente consumíveis. Isso também minimiza o que os consumidores desejam.
* Busque para manter toda a funcionalidade auxiliar `private`.
* Considere o uso de `[<AutoOpen>]` em um módulo particular de funções auxiliares se eles se tornarem numerosos.

## <a name="type-inference-and-generics"></a>Inferência de tipos e genéricos

A inferência de tipos pode evitar que você digite muita clichê. E a F# generalização automática no compilador pode ajudá-lo a escrever código mais genérico com quase nenhum esforço extra de sua parte. No entanto, esses recursos não são universalmente bons.

* Considere rotular nomes de argumentos com tipos explícitos em APIs públicas e não confie na inferência de tipos para isso.

    O motivo disso é que **você** deve estar no controle da forma de sua API, não do compilador. Embora o compilador possa fazer um bom trabalho em tipos informativos, é possível que a forma da sua API seja alterada se os internos dos quais ele depende tiverem tipos alterados. Isso pode ser o que você deseja, mas certamente resultará em uma alteração de API de interrupção com a qual os consumidores de downstream terão que lidar. Em vez disso, se você controlar explicitamente a forma de sua API pública, poderá controlar essas alterações significativas. Em termos de DDD, isso pode ser considerado uma camada anticorrupção.

* Considere fornecer um nome significativo para seus argumentos genéricos.

    A menos que você esteja escrevendo um código verdadeiramente genérico que não seja específico de um determinado domínio, um nome significativo pode ajudar outros programadores a compreender o domínio no qual estão trabalhando. Por exemplo, um parâmetro de tipo chamado `'Document` no contexto de interação com um banco de dados de documento torna mais claro que os tipos de documento genéricos podem ser aceitos pela função ou pelo membro com o qual você está trabalhando.

* Considere nomear parâmetros de tipo genérico com PascalCase.

    Essa é a maneira geral de fazer coisas no .NET, portanto, é recomendável que você use PascalCase em vez de snake_case ou camelCase.

Por fim, a F# generalização automática nem sempre é uma benefício para pessoas que são novas ou uma base de código grande. Há uma sobrecarga cognitiva no uso de componentes genéricos. Além disso, se as funções generalizadas automaticamente não forem usadas com tipos de entrada diferentes (independentemente de se destinarem a serem usadas como tal), não há nenhum benefício real para eles serem genéricos nesse ponto no tempo. Sempre considere se o código que você está escrevendo realmente se beneficiará de ser genérico.

## <a name="performance"></a>Desempenho

F#os valores são imutáveis por padrão, o que permite que você evite determinadas classes de bugs (especialmente aqueles que envolvem simultaneidade e paralelismo). No entanto, em determinados casos, para obter eficiência ideal (ou até mesmo razoável) de tempo de execução ou alocações de memória, um intervalo de trabalho pode ser melhor implementado usando a mutação in-loco do estado. Isso é possível em uma base opcional com F# a palavra-chave`mutable`.

No entanto, o uso F# de `mutable` no pode sentir a probabilidade de uma pureza funcional. Isso é bom, se você ajustar as expectativas de pureza para [transparência referencial](https://en.wikipedia.org/wiki/Referential_transparency). Transparência referencial-não pureza – é a meta final ao escrever F# funções. Isso permite que você escreva uma interface funcional em uma implementação baseada em mutação para código crítico de desempenho.

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Encapsular código mutável em interfaces imutáveis

Com a transparência referencial como meta, é essencial escrever um código que não exponha a Underbelly mutável de funções de desempenho crítico. Por exemplo, o código a seguir implementa a função `Array.contains` na F# biblioteca principal:

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

Chamar essa função várias vezes não altera a matriz subjacente, nem requer que você mantenha qualquer estado mutável ao consumi-la. Ele é transparevelmente transparente, embora quase todas as linhas de código dentro dele usem mutação.

### <a name="consider-encapsulating-mutable-data-in-classes"></a>Considere o encapsulamento de dados mutáveis em classes

O exemplo anterior usava uma única função para encapsular operações usando dados mutáveis. Isso nem sempre é suficiente para conjuntos de dados mais complexos. Considere os seguintes conjuntos de funções:

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

Esse código é de alto desempenho, mas expõe a estrutura de dados baseada em mutação que os chamadores são responsáveis por manter. Isso pode ser encapsulado dentro de uma classe sem Membros subjacentes que podem ser alterados:

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

`Closure1Table` encapsula a estrutura de dados baseada em mutação subjacente, impedindo que os chamadores mantenham a estrutura de dados subjacente. As classes são uma maneira eficiente de encapsular dados e rotinas com base em mutação sem expor os detalhes aos chamadores.

### <a name="prefer-let-mutable-to-reference-cells"></a>Preferir `let mutable` para fazer referência a células

As células de referência são uma maneira de representar a referência a um valor em vez do próprio valor. Embora eles possam ser usados para código de desempenho crítico, geralmente não são recomendados. Considere o exemplo a seguir:

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

O uso de uma célula de referência agora "polui" todos os códigos subsequentes com a falta de desreferenciar e rereferenciar os dados subjacentes. Em vez disso, considere `let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Além do ponto único de mutação no meio da expressão lambda, todo o outro código que toca `acc` pode fazer isso de uma maneira que não seja diferente do uso de um valor normal de ligação de `let`. Isso facilitará a alteração com o passar do tempo.

## <a name="object-programming"></a>Programação de objeto

F#tem suporte completo para objetos e conceitos orientados a objeto (OO). Embora muitos conceitos de OO sejam poderosos e úteis, nem todos eles são ideais para uso. As listas a seguir oferecem orientação sobre as categorias de recursos do OO em um alto nível.

**Considere o uso desses recursos em muitas situações:**

* Notação de ponto (`x.Length`)
* Membros da instância
* Construtores implícitos
* Membros estáticos
* Notação do indexador (`arr.[x]`)
* Argumentos nomeados e opcionais
* Interfaces e implementações de interface

**Não alcance esses recursos primeiro, mas os aplica criteriosamente quando é conveniente resolver um problema:**

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

**Geralmente, evite esses recursos, a menos que você precise usá-los:**

* Hierarquias de tipos baseadas em herança e herança de implementação
* Nulos e `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Preferir composição sobre herança

A [composição sobre herança](https://en.wikipedia.org/wiki/Composition_over_inheritance) é um idioma muito positivo que o F# bom código pode aderir. O princípio fundamental é que você não deve expor uma classe base e forçar chamadores a herdar dessa classe base para obter a funcionalidade.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Use expressões de objeto para implementar interfaces se você não precisar de uma classe

As [expressões de objeto](../language-reference/object-expressions.md) permitem que você implemente interfaces dinamicamente, associando a interface implementada a um valor sem precisar fazer isso dentro de uma classe. Isso é conveniente, especialmente se você _só_ precisa implementar a interface e não precisa de uma classe completa.

Por exemplo, aqui está o código que é executado no [Ionide](http://ionide.io/) para fornecer uma ação de correção de código se você adicionou um símbolo que você não tem uma instrução `open` para:

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

Como não há necessidade de uma classe ao interagir com a API de Visual Studio Code, as expressões de objeto são uma ferramenta ideal para isso. Eles também são valiosos para testes de unidade, quando você deseja stub de uma interface com rotinas de teste de maneira ad hoc.

## <a name="consider-type-abbreviations-to-shorten-signatures"></a>Considere abreviações de tipo para diminuir as assinaturas

As [abreviações de tipo](../language-reference/type-abbreviations.md) são uma maneira conveniente de atribuir um rótulo a outro tipo, como uma assinatura de função ou um tipo mais complexo. Por exemplo, o alias a seguir atribui um rótulo para o que é necessário para definir uma computação com [CNTK](https://docs.microsoft.com/cognitive-toolkit/), uma biblioteca de aprendizado profundo:

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

O nome do `Computation` é uma maneira conveniente de denotar qualquer função que corresponda à assinatura que está sendo alias. Usar abreviações de tipo como essa é conveniente e permite um código mais sucinto.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Evite usar abreviações de tipo para representar seu domínio

Embora as abreviações de tipo sejam convenientes para dar um nome às assinaturas de função, elas podem ser confusas ao abreviar outros tipos. Considere esta abreviação:

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Isso pode ser confuso de várias maneiras:

* `BufferSize` não é uma abstração; Ele é apenas outro nome para um inteiro.
* Se `BufferSize` for exposta em uma API pública, ela poderá facilmente ser interpretada incorretamente para significar mais do que apenas `int`. Geralmente, os tipos de domínio têm vários atributos e não são tipos primitivos como `int`. Essa abreviação viola essa suposição.
* A capitalização de `BufferSize` (PascalCase) implica que esse tipo contém mais dados.
* Esse alias não oferece maior clareza em comparação com o fornecimento de um argumento nomeado para uma função.
* A abreviação não será manifestada no IL compilado; é apenas um inteiro e esse alias é uma construção de tempo de compilação.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

Em resumo, a armadilha com abreviações de tipo é que elas **não** são abstrações sobre os tipos que estão abreviando. No exemplo anterior, `BufferSize` é apenas um `int` nos bastidores, sem dados adicionais nem qualquer benefício do sistema de tipos além do que `int` já tem.

Uma abordagem alternativa para usar abreviações de tipo para representar um domínio é usar uniões discriminadas de um único caso. O exemplo anterior pode ser modelado da seguinte maneira:

```fsharp
type BufferSize = BufferSize of int
```

Se você escrever um código que opere em termos de `BufferSize` e seu valor subjacente, você precisará construir um em vez de passar em qualquer inteiro arbitrário:

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

Isso reduz a probabilidade de passar erroneamente um inteiro arbitrário para a função `send`, porque o chamador deve construir um tipo de `BufferSize` para encapsular um valor antes de chamar a função.
