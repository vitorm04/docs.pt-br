---
title: Programação assincronia
description: Saiba como f# fornece suporte limpo para assincronia com base em um modelo de programação em nível de linguagem derivado de conceitos de programação funcional principais.
ms.date: 12/17/2018
ms.openlocfilehash: 0a7d400c9778e30d6b25798239f12b7b2b0e3d82
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021528"
---
# <a name="async-programming-in-f"></a>Programação de assincronismo em F\#

A programação assíncrona é um mecanismo essencial para aplicações modernas por diversas razões. Existem dois casos de uso primário que a maioria dos desenvolvedores encontrará:

- Apresentar um processo de servidor que possa atender a um número significativo de solicitações simultâneas recebidas, minimizando os recursos do sistema ocupados enquanto o processamento de solicitação aguarda entradas de sistemas ou serviços externos a esse processo
- Mantendo uma ui responsiva ou um segmento principal enquanto simultaneamente progride o trabalho de fundo

Embora o trabalho de fundo muitas vezes envolva a utilização de vários threads, é importante considerar os conceitos de assincronia e multi-threading separadamente. Na verdade, são preocupações separadas, e uma não implica a outra. Este artigo descreve os conceitos separados com mais detalhes.

## <a name="asynchrony-defined"></a>Assincronia definida

O ponto anterior - que a assincronia é independente da utilização de vários segmentos - vale a pena explicar um pouco mais. Há três conceitos que às vezes estão relacionados, mas estritamente independentes um do outro:

- Concorrência; quando vários cálculos são executados em períodos de tempo sobrepostos.
- Paralelismo; quando vários cálculos ou várias partes de uma única computação são executados exatamente ao mesmo tempo.
- Assincronia; quando um ou mais cálculos podem ser executados separadamente do fluxo principal do programa.

Todos os três são conceitos ortogonais, mas podem ser facilmente confundidos, especialmente quando são usados juntos. Por exemplo, você pode precisar executar vários cálculos assíncronos em paralelo. Essa relação não significa que o paralelismo ou a assincronia implicam um ao outro.

Se você considerar a etimologia da palavra "assíncrona", há duas peças envolvidas:

- "A", que significa "não".
- "síncrono", que significa "ao mesmo tempo".

Quando você colocar esses dois termos juntos, você verá que "assíncrono" significa "não ao mesmo tempo". É isso! Não há implicação de simultismo ou paralelismo nesta definição. Isso também é verdade na prática.

Em termos práticos, computações assíncronas em F# são programadas para executar independentemente do fluxo principal do programa. Essa execução independente não implica simultuou-se ou paralelismo, nem implica que uma computação sempre acontece em segundo plano. Na verdade, cálculos assíncronos podem até mesmo executar sincronicamente, dependendo da natureza da computação e do ambiente em que a computação está sendo executada.

A principal vantagem que você deve ter é que os cálculos assíncronos são independentes do fluxo principal do programa. Embora existam poucas garantias sobre quando ou como uma computação assíncrona é executada, existem algumas abordagens para orquestre-las e agendar. O resto deste artigo explora conceitos centrais para a assincronia F# e como usar os tipos, funções e expressões incorporadas em F#.

## <a name="core-concepts"></a>Conceitos principais

Em F#, a programação assíncrona é centrada em três conceitos principais:

- O `Async<'T>` tipo, que representa uma composável computação assíncrona.
- As `Async` funções do módulo, que permitem programar trabalhos assíncronos, compõem cálculos assíncronos e transformam resultados assíncronos.
- A `async { }` [expressão computacional,](../../language-reference/computation-expressions.md)que fornece uma sintaxe conveniente para construir e controlar cálculos assíncronos.

Você pode ver esses três conceitos no seguinte exemplo:

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

No exemplo, `printTotalFileBytes` a função `string -> Async<unit>`é do tipo . Chamar a função não executa realmente a computação assíncrona. Em vez disso, retorna um `Async<unit>` que age como uma *especificação* do trabalho que é executar assíncronamente. Ele `Async.AwaitTask` chama em seu corpo, que <xref:System.IO.File.ReadAllBytesAsync%2A> converte o resultado de um tipo apropriado.

Outra linha importante é `Async.RunSynchronously`a chamada para . Esta é uma das funções de partida do módulo Assync que você precisará chamar se quiser realmente executar uma computação assíncrona F#.

Esta é uma diferença fundamental com o `async` estilo C#/Visual Basic de programação. Em F#, cálculos assíncronos podem ser considerados como **tarefas frias.** Eles devem ser explicitamente iniciados para realmente executar. Isso tem algumas vantagens, pois permite combinar e sequenciar trabalhos assíncronos muito mais facilmente do que em C# ou Visual Basic.

## <a name="combine-asynchronous-computations"></a>Combine cálculos assíncronos

Aqui está um exemplo que se baseia no anterior combinando cálculos:

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

Como você pode `main` ver, a função tem mais algumas chamadas feitas. Conceitualmente, ele faz o seguinte:

1. Transforme os argumentos `Async<unit>` da linha `Array.map`de comando em cálculos com .
2. Crie `Async<'T[]>` um que programe `printTotalFileBytes` e execute os cálculos em paralelo quando for executado.
3. Crie `Async<unit>` um que execute a computação paralela e ignore seu resultado.
4. Execute explicitamente a última `Async.RunSynchronously` computação com e bloqueie até que seja concluída.

Quando este programa `printTotalFileBytes` é executado, é executado em paralelo para cada argumento de linha de comando. Como os cálculos assíncronos são executados independentemente do fluxo do programa, não há ordem na qual imprimam suas informações e terminem a execução. Os cálculos serão agendados em paralelo, mas sua ordem de execução não é garantida.

## <a name="sequence-asynchronous-computations"></a>Cálculos assíncronos de seqüência

Por `Async<'T>` ser uma especificação do trabalho em vez de uma tarefa já em execução, você pode realizar transformações mais complexas facilmente. Aqui está um exemplo que sequencia um conjunto de cálculos Do Sync para que eles executem um após o outro.

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

Isso será `printTotalFileBytes` agendado para executar na `argv` ordem dos elementos de vez em programá-los em paralelo. Como o próximo item não será agendado até que a última computação tenha sido executada, os cálculos são sequenciados de tal forma que não haja sobreposição em sua execução.

## <a name="important-async-module-functions"></a>Funções importantes do módulo Async

Quando você escreve código assincrono em F#, você geralmente interage com uma estrutura que lida com o agendamento de cálculos para você. No entanto, nem sempre é assim, por isso é bom aprender as várias funções iniciais para agendar trabalhos assíncronos.

Como os cálculos assíncronos F# são uma _especificação_ do trabalho em vez de uma representação de trabalho que já está sendo executado, eles devem ser explicitamente iniciados com uma função inicial. Existem muitas [funções iniciais do Assync](https://msdn.microsoft.com/library/ee370232.aspx) que são úteis em diferentes contextos. A seção a seguir descreve algumas das funções de partida mais comuns.

### <a name="asyncstartchild"></a>Async.StartChild

Inicia uma computação infantil dentro de uma computação assíncrona. Isso permite que vários cálculos assíncronos sejam executados simultaneamente. A computação infantil compartilha um token de cancelamento com a computação dos pais. Se a computação dos pais for cancelada, a computação filho também será cancelada.

Assinatura:

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

Quando usar:

- Quando você deseja executar vários cálculos assíncronos simultaneamente em vez de um de cada vez, mas não tê-los agendados em paralelo.
- Quando você deseja vincular a vida útil de um cálculo infantil à de um cálculo pai.

O que tomar cuidado:

- Iniciar vários cálculos `Async.StartChild` com não é o mesmo que agendar em paralelo. Se você deseja agendar cálculos `Async.Parallel`em paralelo, use .
- O cancelamento de um cálculo dos pais provocará o cancelamento de todos os cálculos de crianças iniciados.

### <a name="asyncstartimmediate"></a>Async.StartImmediate

Executa uma computação assíncrona, iniciando imediatamente no segmento atual do sistema operacional. Isso é útil se você precisar atualizar algo no segmento de chamada durante a computação. Por exemplo, se uma computação assíncrona deve atualizar uma ui (como atualizar uma barra de progresso), então `Async.StartImmediate` deve ser usada.

Assinatura:

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

Quando usar:

- Quando você precisa atualizar algo no segmento de chamada no meio de uma computação assíncrona.

O que tomar cuidado:

- O código na computação assíncrona será executado em qualquer segmento que esteja programado. Isso pode ser problemático se esse segmento for de alguma forma sensível, como um segmento de UI. Nesses casos, `Async.StartImmediate` é provável que seja inapropriado usar.

### <a name="asyncstartastask"></a>Async.StartAsTask

Executa um cálculo no pool de segmentos. Retorna <xref:System.Threading.Tasks.Task%601> um que será concluído no estado correspondente assim que o cálculo terminar (produz o resultado, lança exceção ou é cancelado). Se nenhum token de cancelamento for fornecido, o token de cancelamento padrão será usado.

Assinatura:

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

Quando usar:

- Quando você precisa chamar uma API .NET que espera que a represente <xref:System.Threading.Tasks.Task%601> o resultado de uma computação assíncrona.

O que tomar cuidado:

- Esta chamada alocará um objeto adicional, `Task` que pode aumentar a sobrecarga se for usada com frequência.

### <a name="asyncparallel"></a>Assync.Parallel

Agenda uma seqüência de cálculos assíncronos a serem executados em paralelo. O grau de paralelismo pode ser opcionalmente `maxDegreesOfParallelism` ajustado/estrangulado especificando o parâmetro.

Assinatura:

```fsharp
computations: seq<Async<'T>> * ?maxDegreesOfParallelism: int -> Async<'T[]>
```

Quando usar:

- Se você precisar executar um conjunto de cálculos ao mesmo tempo e não confiar em sua ordem de execução.
- Se você não precisar de resultados de cálculos agendados em paralelo até que todos tenham sido concluídos.

O que tomar cuidado:

- Você só pode acessar a matriz de valores resultante uma vez que todos os cálculos tenham terminado.
- Os cálculos serão executados sempre que forem agendados. Este comportamento significa que você não pode confiar na ordem deles de sua execução.

### <a name="asyncsequential"></a>Async.Seqüencial

Agenda uma seqüência de cálculos assíncronos a serem executados na ordem em que são passados. O primeiro cálculo será executado, depois o próximo, e assim por diante. Nenhum cálculo será executado em paralelo.

Assinatura:

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

Quando usar:

- Se você precisar executar vários cálculos em ordem.

O que tomar cuidado:

- Você só pode acessar a matriz de valores resultante uma vez que todos os cálculos tenham terminado.
- Os cálculos serão executados na ordem em que são passados para esta função, o que pode significar que mais tempo se passará antes que os resultados sejam devolvidos.

### <a name="asyncawaittask"></a>Async.AwaitTask

Retorna uma computação assíncrona que <xref:System.Threading.Tasks.Task%601> espera que o dado complete e retorna seu resultado como um`Async<'T>`

Assinatura:

```fsharp
task: Task<'T> -> Async<'T>
```

Quando usar:

- Quando você está consumindo uma API <xref:System.Threading.Tasks.Task%601> .NET que retorna a dentro de uma computação assíncrona F#.

O que tomar cuidado:

- As exceções <xref:System.AggregateException> são embrulhadas seguindo a convenção da Biblioteca Paralela de Tarefas, e esse comportamento é diferente de como o f# assync geralmente aparece exceções.

### <a name="asynccatch"></a>Async.Catch

Cria uma computação assíncrona `Async<'T>`que executa `Async<Choice<'T, exn>>`um dado, retornando um . Se o `Async<'T>` dado for `Choice1Of2` concluído com sucesso, então um é devolvido com o valor resultante. Se uma exceção for lançada antes `Choice2of2` de ser concluída, então um é devolvido com a exceção levantada. Se for usado em uma computação assíncrona que é composta por muitos cálculos, e um desses cálculos abre uma exceção, a computação abrangente será totalmente interrompida.

Assinatura:

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

Quando usar:

- Quando você está realizando um trabalho assíncrono que pode falhar com uma exceção e você deseja lidar com essa exceção no chamador.

O que tomar cuidado:

- Ao usar cálculos assíncronos combinados ou seqüenciados, a computação abrangente irá parar totalmente se uma de suas computação "internas" lançar uma exceção.

### <a name="asyncignore"></a>Assync.Ignore

Cria uma computação assíncrona que executa a dada computação e ignora seu resultado.

Assinatura:

```fsharp
computation: Async<'T> -> Async<unit>
```

Quando usar:

- Quando você tem uma computação assíncrona cujo resultado não é necessário. Isso é análogo `ignore` ao código para código não assíncrono.

O que tomar cuidado:

- Se você `Async.Ignore` deve usar porque `Async.Start` deseja usar `Async<unit>`ou outra função que exija, considere se descartar o resultado está bem. Evite descartar resultados apenas para se encaixar em uma assinatura do tipo.

### <a name="asyncrunsynchronously"></a>Async.RunSynchronously

Executa uma computação assíncrona e aguarda seu resultado no segmento de chamada. Esta chamada está bloqueando.

Assinatura:

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

Quando usar:

- Se você precisar, use-o apenas uma vez em um aplicativo - no ponto de entrada para um executável.
- Quando você não se importa com o desempenho e quer executar um conjunto de outras operações assíncronas ao mesmo tempo.

O que tomar cuidado:

- A `Async.RunSynchronously` chamada bloqueia o segmento de chamada até que a execução seja concluída.

### <a name="asyncstart"></a>Async.Start

Inicia uma computação assíncrona no `unit`pool de segmentos que retorna . Não espera pelo resultado. Os cálculos aninhados iniciados `Async.Start` são iniciados independentemente da computação parental que os chamou. Sua vida não está ligada a nenhum cálculo dos pais. Se a computação dos pais for cancelada, nenhum cálculo de filho será cancelado.

Assinatura:

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

Use somente quando:

- Você tem uma computação assíncrona que não produz um resultado e/ou requer processamento de um.
- Você não precisa saber quando uma computação assíncrona é concluída.
- Você não se importa em qual segmento uma computação assíncrona é executada.
- Você não precisa estar ciente ou relatar exceções resultantes da tarefa.

O que tomar cuidado:

- Exceções levantadas por cálculos `Async.Start` iniciados não são propagadas para o chamador. A pilha de chamadas será completamente desenrolada.
- Qualquer trabalho (como `printfn`chamada) `Async.Start` iniciado não fará com que o efeito aconteça no segmento principal da execução de um programa.

## <a name="interoperate-with-net"></a>Interoperar com .NET

Você pode estar trabalhando com uma biblioteca .NET ou c# codebase que usa programação assíncrona de estilo assíncrono de estilo assíncrono. [async/await](../../../standard/async.md) Como c# e a maioria das <xref:System.Threading.Tasks.Task%601> bibliotecas .NET usam os <xref:System.Threading.Tasks.Task> e `Async<'T>`tipos como suas abstrações principais em vez de , você deve cruzar um limite entre essas duas abordagens para a assincronia.

### <a name="how-to-work-with-net-async-and-taskt"></a>Como trabalhar com .NET async e`Task<T>`

Trabalhar com bibliotecas assincronias <xref:System.Threading.Tasks.Task%601> .NET e bases de código que usam (ou seja, asincronizar computações que têm valores de retorno) é simples e tem suporte interno com F#.

Você pode `Async.AwaitTask` usar a função para aguardar uma computação assíncrona .NET:

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

Você pode `Async.StartAsTask` usar a função para passar uma computação assíncrona para um chamador .NET:

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>Como trabalhar com .NET async e`Task`

Para trabalhar com APIs que usam <xref:System.Threading.Tasks.Task> (ou seja, computação sincronia .NET que não retorna `Async<'T>` um <xref:System.Threading.Tasks.Task>valor), talvez seja necessário adicionar uma função adicional que converterá um para:

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

Já existe `Async.AwaitTask` um que <xref:System.Threading.Tasks.Task> aceita uma entrada. Com isso e a `startTaskFromAsyncUnit` função previamente definida, você pode iniciar e esperar <xref:System.Threading.Tasks.Task> tipos a partir de uma computação assíncrona F#.

## <a name="relationship-to-multi-threading"></a>Relação com multi-threading

Embora o threading seja mencionado ao longo deste artigo, há duas coisas importantes a serem lembradas:

1. Não há afinidade entre uma computação assíncrona e um segmento, a menos que explicitamente iniciado no segmento atual.
1. Programação assíncrona em F# não é uma abstração para multi-threading.

Por exemplo, uma computação pode realmente ser executada no segmento de chamada, dependendo da natureza do trabalho. Uma computação também poderia "saltar" entre os segmentos, emprestando-os por um pequeno período de tempo para fazer um trabalho útil entre períodos de "espera" (como quando uma chamada de rede está em trânsito).

Embora f# forneça algumas habilidades para iniciar uma computação assíncrona no segmento atual (ou explicitamente não no segmento atual), a assincronia geralmente não está associada a uma estratégia de rosca específica.

## <a name="see-also"></a>Confira também

- [O Modelo de Programação Assíncrona F#](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Guia De Async F# da Jet.com](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [F# para diversão e lucro guia de Programação Assíncrona](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [Assync em C# e F#: Gotchas assíncronas em C #](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
