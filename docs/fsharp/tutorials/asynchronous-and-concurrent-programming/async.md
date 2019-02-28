---
title: Programação assíncrona
description: Saiba como F# programação assíncrona é realizada por meio de um modelo de programação de nível de linguagem que é o idioma natural e fácil de usar.
ms.date: 06/20/2016
ms.openlocfilehash: 18ba4873cd3dba6d9548a07c4487306d96adab61
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980081"
---
# <a name="async-programming-in-f"></a>Programação assíncrona em F\#

> [!NOTE]
> Algumas imprecisões foram descobertos neste artigo.  Ele está sendo regravado.  Ver [problema #666](https://github.com/dotnet/docs/issues/666) para saber mais sobre as alterações.

Assíncrono de programação no F# pode ser feito por meio de um modelo de programação de nível de linguagem projetado para ser fácil de usar e a linguagem natural.

O núcleo de async programando em F# é `Async<'T>`, uma representação de trabalho que pode ser disparado para ser executado em segundo plano, onde `'T` é o tipo retornado por meio de especiais `return` palavra-chave ou `unit` se o fluxo de trabalho assíncronos não tem nenhum resultado a ser retornado.

O conceito-chave para entender é que tipo de uma expressão async é `Async<'T>`, que é simplesmente uma _especificação_ de trabalho a ser feito em um contexto assíncrono. Não é executado até que você o inicie explicitamente com uma das funções de partida (como `Async.RunSynchronously`). Embora essa seja uma maneira diferente de pensar sobre como fazer o trabalho, ele acaba sendo bastante simples na prática.

Por exemplo, digamos que você quiser baixar o HTML de dotnetfoundation.org sem bloquear o thread principal. Você pode fazer isso como este:

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()

        // Execution of fetchHtmlAsync won't continue until the result
        // of AsyncDownloadString is bound.
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

E pronto! Além do uso de `async`, `let!`, e `return`, isso é apenas normal F# código.

Há algumas construções sintáticas que vale a pena observar:

*   `let!` associa o resultado de uma expressão assíncrona (que é executado em outro contexto).
*   `use!` funciona da mesma forma `let!`, mas descarta os seus recursos associados quando ele sai do escopo.
*   `do!` irá esperar um fluxo de trabalho de async que não retorna nada.
*   `return` simplesmente retorna um resultado de uma expressão assíncrona.
*   `return!` executa outro fluxo de trabalho assíncrono e retorna seu valor de retorno como resultado.

Além disso, normal `let`, `use`, e `do` palavras-chave podem ser usadas junto com as versões assíncronas, assim como fariam em uma função normal.

## <a name="how-to-start-async-code-in-f"></a>Como iniciar o código assíncrono no F\#

Como mencionado anteriormente, o código assíncrono é uma especificação de trabalho a ser feito em outro contexto que deve ser iniciada explicitamente. Aqui estão duas maneiras principais de fazer isso:

1.  `Async.RunSynchronously` Inicie um fluxo de trabalho assíncrono em outro thread e await seu resultado.

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

 // Execution will pause until fetchHtmlAsync finishes
 let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2.  `Async.Start` iniciará um fluxo de trabalho assíncrono em outro thread e serão **não** await seu resultado.

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

Há outras maneiras de iniciar um fluxo de trabalho assíncronos disponível para cenários mais específicos. Elas são detalhadas [na referência do Async](https://msdn.microsoft.com/library/ee370232.aspx).

### <a name="a-note-on-threads"></a>Uma observação sobre Threads

A frase "em outro thread" é mencionada acima, mas é importante saber que **isso não significa que os fluxos de trabalho assíncronos são uma fachada para multithreading**. O fluxo de trabalho, na verdade, "salta" entre threads, emprestando-los para uma pequena quantidade de tempo para fazer trabalho útil. Quando um fluxo de trabalho assíncrono está efetivamente "Aguardando" (por exemplo, aguardando uma chamada de rede retornar algo), qualquer thread que ele foi emprestando no momento é liberada até vá fazer o trabalho útil em algo mais. Isso permite que fluxos de trabalho assíncronos utilizar o sistema a em que serem executados com eficiência possível e os torna especialmente forte para cenários de e/s de alto volume.

## <a name="how-to-add-parallelism-to-async-code"></a>Como adicionar paralelismo em código assíncrono

Às vezes, você pode precisa para executar vários trabalhos assíncronos em paralelo, coletar seus resultados e interpretá-los de alguma forma. `Async.Parallel` permite que você faça isso sem a necessidade de usar a biblioteca paralela de tarefas, que envolveria a necessidade de forçar `Task<'T>` e `Async<'T>` tipos.

O exemplo a seguir usará `Async.Parallel` para baixar o HTML de quatro sites popular em paralelo, aguardar a conclusão dessas tarefas e, em seguida, imprima o HTML que foi baixado.

```fsharp
open System
open System.Net

let urlList = 
    [ "https://www.microsoft.com"
      "https://www.google.com"
      "https://www.amazon.com"
      "https://www.facebook.com" ]

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let getHtmlList urls =
    urls
    |> Seq.map fetchHtmlAsync   // Build an Async<'T> for each site
    |> Async.Parallel           // Returns an Async<'T []>
    |> Async.RunSynchronously   // Wait for the result of the parallel work

let htmlList = getHtmlList urlList

// We now have the downloaded HTML for each site!
for html in htmlList do
    printfn "%s" html
```

## <a name="important-info-and-advice"></a>Conselhos e informações importantes

*   Acrescentar "Async" ao final de todas as funções que irá consumir

 Embora essa seja apenas uma convenção de nomenclatura, ele facilitar as coisas, como a capacidade de descoberta de API. Especialmente se houver versões síncronas e assíncronas da mesma rotina, é aconselhável declarar explicitamente que é assíncrona por meio do nome.

*   Ouça o compilador!

 F#do compilador é muito estrito, tornando praticamente impossível fazer alguma coisa um problema, como executar código de "async" de forma síncrona. Se você se deparar com um aviso, que é um sinal de que o código não será executado como você acha que ele será. Se você pode deixar o compilador feliz, seu código provavelmente será executado conforme o esperado.

## <a name="for-the-cvb-programmer-looking-into-f"></a>Para o C#programador /VB procurando em F\#

Esta seção pressupõe que você esteja familiarizado com o modelo de async no C#/VB. Se não, [assíncrono de programação em C# ](../../../csharp/async.md) é um ponto de partida.

Há uma diferença fundamental entre o C#modelo assíncrono /VB e o F# modelo assíncrono.

Quando você chama uma função que retorna um `Task` ou `Task<'T>`, que o trabalho já tiver começado a execução. O identificador retornado representa um trabalho assíncrono do já em execução. Por outro lado, quando você chama uma função assíncrona F#, o `Async<'a>` retornada representa um trabalho que será **gerado** em algum momento. Noções básicas sobre esse modelo é muito eficiente, porque permite trabalhos assíncronos no F# para ser encadeados juntos, executadas condicionalmente e ser iniciada com um detalhamento mais refinado de controle.

Há algumas semelhanças e diferenças que merecem atenção.

### <a name="similarities"></a>Semelhanças

*   `let!`, `use!`, e `do!` são análogos aos `await` ao chamar um trabalho assíncrono de dentro um `async{ }` bloco.

 As três palavras-chave só podem ser usadas dentro de um `async { }` bloco, de forma semelhante a como `await` só pode ser chamada dentro de um `async` método. Em resumo, `let!` destina-se quando você deseja capturar e usar um resultado `use!` é o mesmo, mas algo cujos recursos devem obter limpos depois que ele é usado, e `do!` é para quando você deseja esperar para um fluxo de trabalho assíncrono com nenhum valor de retorno para concluir antes de prosseguir.

*   F#dá suporte a paralelismo de dados de maneira semelhante.

 Embora ele opera de forma muito diferente `Async.Parallel` corresponde ao `Task.WhenAll` para o cenário de que deseja os resultados de um conjunto de trabalhos assíncronos quando todos forem concluídos.

### <a name="differences"></a>Diferenças

*   Aninhado `let!` não é permitido, ao contrário de aninhados `await`

 Diferentemente `await`, que podem ser aninhado indefinidamente `let!` não é possível e deve ter seu resultado associado antes de usá-lo dentro de outra `let!`, `do!`, ou `use!`.

*   Suporte ao cancelamento é mais simples no F# que no C#/VB.

 Oferecer suporte ao cancelamento de midway uma tarefa por meio de sua execução no C#/VB requer verificação o `IsCancellationRequested` propriedade ou chamada `ThrowIfCancellationRequested()` em um `CancellationToken` objeto que é passado para o método assíncrono.

Por outro lado, F# fluxos de trabalho assíncronos são mais naturalmente cancelável. O cancelamento é um processo de três etapas simples.

1.  Crie um novo `CancellationTokenSource`.
2.  Passá-la para uma função inicial.
3.  Chamar `Cancel` no token.

Exemplo:

```fsharp
open System.Threading

// Create a workflow which will loop forever.
let workflow =
    async {
        while true do
            printfn "Working..."
            do! Async.Sleep 1000
    }
    
let tokenSource = new CancellationTokenSource()

// Start the workflow in the background
Async.Start (workflow, tokenSource.Token)

// Executing the next line will stop the workflow
tokenSource.Cancel()
```

E pronto!

## <a name="further-resources"></a>Recursos adicionais:

*   [Fluxos de trabalho assíncronos no MSDN](https://msdn.microsoft.com/library/dd233250.aspx)
*   [Sequências assíncronas paraF#](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [F#Utilitários de dados HTTP](https://fsharp.github.io/FSharp.Data/library/Http.html)