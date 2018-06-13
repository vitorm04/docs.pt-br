---
title: 'Programação assíncrona em F #'
description: 'Saiba como programação assíncrona em F # é realizada por meio de um modelo de programação de nível de linguagem natural para a linguagem e fácil de usar.'
ms.date: 06/20/2016
ms.openlocfilehash: 93ecd05efc493489435214dcd7ae78fffcccec1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566867"
---
# <a name="async-programming-in-f"></a>Programação assíncrona em F # #

> [!NOTE]
> Alguns imprecisões foram descobertos neste artigo.  Ele está sendo reconfigurado.  Consulte [problema #666](https://github.com/dotnet/docs/issues/666) para saber mais sobre as alterações.

Programação em F # assíncrona pode ser feita por meio de um modelo de programação de nível de linguagem foi projetado para ser fácil de usar e a linguagem natural.

O núcleo de programação assíncrona em F # é `Async<'T>`, uma representação de trabalho que pode ser disparado para ser executado em segundo plano, onde `'T` é o tipo retornado por meio de especiais `return` palavra-chave ou `unit` se o fluxo de trabalho assíncrono não tem nenhum resultado a ser retornado.

O conceito de chave para entender é que o tipo da expressão um async é `Async<'T>`, que é simplesmente uma _especificação_ do trabalho a ser feito em um contexto assíncrono. Não será executado até que você o inicie explicitamente com uma das funções iniciais (como `Async.RunSynchronously`). Embora essa seja uma maneira diferente de pensar sobre como fazer o trabalho, ele acaba sendo bem simples na prática.

Por exemplo, digamos que você deseja baixar o HTML de dotnetfoundation.org sem bloquear o thread principal. Você pode fazer isso assim:

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

E pronto! Além do uso de `async`, `let!`, e `return`, isso é normal apenas código F #.

Há algumas construções sintáticas que vale a pena observar:

*   `let!` associa o resultado de uma expressão assíncrona (que é executado em outro contexto).
*   `use!` funciona da mesma forma `let!`, mas descarta seus recursos associados quando ele sai do escopo.
*   `do!` irá esperar um fluxo de trabalho assíncrona que não retorna nada.
*   `return` simplesmente retorna um resultado de uma expressão assíncrona.
*   `return!` executa outro fluxo de trabalho assíncrono e retorna seu valor de retorno como resultado.

Além disso, normal `let`, `use`, e `do` palavras-chave podem ser usadas junto com as versões assíncronas, como faria em uma função normal.

## <a name="how-to-start-async-code-in-f"></a>Como iniciar o código assíncrono em F # #

Como mencionado anteriormente, o código assíncrono é uma especificação de trabalho a ser feito em outro contexto que deve ser iniciada explicitamente. Aqui estão duas maneiras principais para fazer isso:

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

2.  `Async.Start` irá iniciar um fluxo de trabalho assíncrono em outro thread e será **não** await seu resultado.

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

Existem outras maneiras de iniciar um fluxo de trabalho assíncrono disponível para cenários mais específicos. Elas são detalhadas [na referência de Async](https://msdn.microsoft.com/library/ee370232.aspx).

### <a name="a-note-on-threads"></a>Uma observação sobre Threads

A frase "em outro thread" é mencionada acima, mas é importante saber que **isso não significa que fluxos de trabalho assíncronos são uma fachada para multithreading**. O fluxo de trabalho, na verdade, "salta" entre threads, empréstimo-los para uma pequena quantidade de tempo para fazer o trabalho útil. Quando um fluxo de trabalho assíncrono é efetivamente "Aguardando" (por exemplo, aguardando uma chamada de rede retornar algo), qualquer thread que ele foi empréstimo no momento é liberada até o trabalho útil que vá fazer outra coisa. Isso permite que os fluxos de trabalho assíncrono utilizar o sistema que estiverem sendo executados em maneira eficaz e torna especialmente forte para cenários de e/s de alto volume.

## <a name="how-to-add-parallelism-to-async-code"></a>Como adicionar paralelismo código assíncrono

Às vezes, você pode necessárias para executar várias tarefas assíncronas em paralelo, coletar seus resultados e interpretá-los de algum modo. `Async.Parallel` permite que você faça isso sem a necessidade de usar a biblioteca paralela de tarefas, que envolve a necessidade de forçar `Task<'T>` e `Async<'T>` tipos.

O exemplo a seguir usará `Async.Parallel` para baixar o HTML de quatro sites populares em paralelo, aguarde até que essas tarefas a serem concluídas e imprima o HTML que foi baixado.

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

*   Anexar "Async" ao final de qualquer função que você irá consumir

 Embora essa seja apenas uma convenção de nomenclatura, ele facilitar as coisas como a descoberta de API. Especialmente se houver versões síncronas e assíncronas da rotina mesmo, é uma boa ideia declarar explicitamente que é assíncrona por meio do nome.

*   Ouça o compilador!

 Compilador do F # é muito estrito, tornando quase impossível fazer algo o troubling como executar código de "async" sincronicamente. Se você se deparar com um aviso, que é um sinal de que o código não irá executar como você acha que ele será. Se você pode fazer o compilador felizes, seu código provavelmente será executado conforme o esperado.

## <a name="for-the-cvb-programmer-looking-into-f"></a>Para o programador de c# /VB C procurando no F # #

Esta seção pressupõe que você esteja familiarizado com o modelo assíncrono em c# / VB. Se não, [assíncrono de programação em c#](../../../csharp/async.md) é um ponto de partida.

Há uma diferença fundamental entre o modelo de async c# /VB C e o modelo de async F #.

Quando você chama uma função que retorna um `Task` ou `Task<'T>`, já que o trabalho começou execução. O identificador retornado representa uma tarefa assíncrona já em execução. Por outro lado, quando você chama uma função async em F #, a `Async<'a>` retornado representa um trabalho que será **gerado** em algum momento. Noções básicas sobre esse modelo é muito eficiente, porque permite tarefas assíncronas em F # para ser encadeadas, executada condicionalmente e ser iniciada com mais individualizadas do controle.

Há algumas semelhanças e diferenças vale a pena observar.

### <a name="similarities"></a>Semelhanças

*   `let!`, `use!`, e `do!` são análogos a `await` ao chamar um trabalho assíncrono de dentro um `async{ }` bloco.

 As três palavras-chave só podem ser usadas dentro de um `async { }` bloco, semelhante a como `await` só pode ser chamado dentro de um `async` método. Em resumo, `let!` é para quando você deseja capturar e usar um resultado, `use!` é o mesmo, mas algo cujos recursos devem obter limpo depois que ele é usado, e `do!` é para quando você quiser esperar um fluxo de trabalho assíncrono com nenhum valor de retorno para concluir antes de continuar.

*   F # suporta o paralelismo de dados de maneira semelhante.

 Embora ele opera de forma muito diferente, `Async.Parallel` corresponde à `Task.WhenAll` para o cenário de que os resultados de um conjunto de trabalhos assíncronos quando concluem a todos eles.

### <a name="differences"></a>Diferenças

*   Aninhados `let!` não é permitido; diferentemente aninhados `await`

 Ao contrário de `await`, que podem ser aninhado indefinidamente, `let!` não é possível e deve ter seu resultado associado antes de usá-la em outro `let!`, `do!`, ou `use!`.

*   Suporte ao cancelamento é mais simples em F # que em c# / VB.

 Oferecer suporte ao cancelamento de um tarefa no meio do caminho por meio de sua execução em C# /VB requer verificando o `IsCancellationRequested` propriedade ou chamar `ThrowIfCancellationRequested()` em uma `CancellationToken` objeto que é passado para o método assíncrono.

Em contraste, F # assíncrona fluxos de trabalho são mais naturalmente cancelável. Cancelamento é um processo de três etapas simple.

1.  Crie um novo `CancellationTokenSource`.
2.  Passá-la em uma função inicial.
3.  Chamar `Cancel` no token.

Exemplo:

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

let token = new CancellationTokenSource()
Async.Start (workflow, token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

E pronto!

## <a name="further-resources"></a>Recursos adicionais:

*   [Fluxos de trabalho assíncrono no MSDN](https://msdn.microsoft.com/library/dd233250.aspx)
*   [Sequências assíncronas para F #](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [Utilitários de F # dados HTTP](https://fsharp.github.io/FSharp.Data/library/Http.html)
