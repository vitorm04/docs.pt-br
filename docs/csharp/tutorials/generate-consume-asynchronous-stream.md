---
title: Gerar e consumir fluxos assíncronos
description: Este tutorial avançado mostra como gerar e consumir fluxos assíncronos. Os fluxos assíncronos fornecem uma maneira mais natural de trabalhar com sequências de dados que podem ser gerados de forma assíncrona.
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: fd9fed3469d18c919102640df7bb501b116f5e0e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420364"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Tutorial: gerar e consumir fluxos assíncronos usando C# 8,0 e .NET Core 3,0

O C# 8,0 introduz **fluxos assíncronos**, que modelam uma fonte de transmissão de dados. Os fluxos de dados geralmente recuperam ou geram elementos de forma assíncrona. Os fluxos assíncronos dependem de novas interfaces introduzidas no .NET Standard 2,1. Essas interfaces têm suporte no .NET Core 3,0 e posterior. Eles fornecem um modelo de programação natural para fontes de dados de streaming assíncronas.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> - Criar uma fonte de dados que gera uma sequência de elementos de dados de forma assíncrona.
> - Consumir essa fonte de dados de forma assíncrona.
> - Suporte a cancelamento e contextos capturados para fluxos assíncronos.
> - Reconhecer quando a nova interface e a fonte de dados forem preferenciais para sequências anteriores de dados síncronos.

## <a name="prerequisites"></a>Pré-requisitos

Você precisará configurar seu computador para executar o .NET Core, incluindo o compilador C# 8,0. O compilador C# 8 está disponível a partir do [Visual Studio 2019 versão 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou do [SDK do .NET Core 3,0](https://dotnet.microsoft.com/download).

Você precisará criar um [token de acesso do GitHub](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) para poder acessar o ponto de extremidade GitHub GraphQL. Selecione as seguintes permissões para o Token de acesso do GitHub:

- repo:status
- public_repo

Salve o token de acesso em um local seguro, de modo que possa usá-lo para acessar o ponto de extremidade da API do GitHub.

> [!WARNING]
> Mantenha seu token de acesso pessoal protegido. Qualquer software com seu token de acesso pessoal pode fazer chamadas da API do GitHub usando seus direitos de acesso.

Este tutorial pressupõe que você esteja familiarizado com o C# e .NET, incluindo o Visual Studio ou a CLI do .NET Core.

## <a name="run-the-starter-application"></a>Executar o aplicativo inicial

Você pode obter o código para o aplicativo inicial usado neste tutorial do repositório [dotnet/docs](https://github.com/dotnet/docs) na pasta [Csharp/tutoriais/AsyncStreams](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/snippets/generate-consume-asynchronous-streams/start) .

O aplicativo inicial é um aplicativo de console que usa a interface [GitHub GraphQL](https://developer.github.com/v4/) para recuperar os problemas recentes gravados no repositório [dotnet/docs](https://github.com/dotnet/docs). Comece observando o código a seguir para o método `Main` do aplicativo inicial:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetStarterAppMain" :::

Você pode definir uma variável de ambiente `GitHubKey` para o token de acesso pessoal ou pode substituir o último argumento na chamada para `GenEnvVariable` com seu token de acesso pessoal. Não coloque seu código de acesso no código-fonte se você estiver compartilhando a fonte com outras pessoas. Nunca carregue códigos de acesso em um repositório de origem compartilhado.

Após criar o cliente do GitHub, o código em `Main` criará um objeto de relatório de andamento e um token de cancelamento. Depois que esses objetos forem criados, `Main` chamará `runPagedQueryAsync` para recuperar os 250 problemas mais recente criados. Depois que a tarefa for concluída, os resultados serão exibidos.

Ao executar o aplicativo inicial, você poderá realizar algumas observações importantes sobre como esse aplicativo é executado.  Você verá o progresso informado para cada página retornada do GitHub. É possível observar uma pausa perceptível antes do GitHub retornar cada nova página de problemas. Por fim, os problemas só serão exibidos depois que todas as 10 páginas forem recuperadas do GitHub.

## <a name="examine-the-implementation"></a>Examinar a implementação

A implementação revela por que você observou o comportamento discutido na seção anterior. Examine o código para `runPagedQueryAsync`:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetRunPagedQuery" :::

Vamos nos concentrar no algoritmo de paginação e na estrutura assíncrona do código anterior. (Você pode consultar a [documentação do GitHub GraphQL](https://developer.github.com/v4/guides/) para obter detalhes sobre a API GraphQL do github.) O `runPagedQueryAsync` método enumera os problemas do mais recente para o mais antigo. Ele solicita 25 problemas por página e examina a estrutura `pageInfo` da resposta para continuar com a página anterior. Isso segue o suporte de paginação padrão do GraphQL para respostas com várias páginas. A resposta inclui um objeto `pageInfo` que inclui um valor `hasPreviousPages` e um valor `startCursor` usados para solicitar a página anterior. Os problemas estão na matriz `nodes`. O método `runPagedQueryAsync` anexa esses nós em uma matriz que contém todos os resultados de todas as páginas.

Após a recuperação e a restauração de uma página de resultados, `runPagedQueryAsync` informa o andamento e verifica o cancelamento. Se o cancelamento tiver sido solicitado, `runPagedQueryAsync` gerará um <xref:System.OperationCanceledException>.

Há vários elementos nesse código que podem ser melhorados. Acima de tudo, `runPagedQueryAsync` deve alocar armazenamento para todos os problemas retornados. Este exemplo é interrompido em 250 problemas porque recuperar todos os problemas exigiria muito mais memória para armazenar todos os problemas recuperados. Os protocolos para dar suporte a relatórios de progresso e cancelamento tornam o algoritmo mais difícil de entender em sua primeira leitura. Mais tipos e APIs estão envolvidos. Você deve rastrear as comunicações por meio do <xref:System.Threading.CancellationTokenSource> e seu associado <xref:System.Threading.CancellationToken> para entender onde o cancelamento é solicitado e onde ele é concedido.

## <a name="async-streams-provide-a-better-way"></a>Os fluxos assíncronos fornecem uma melhor maneira

Os fluxos assíncronos e o suporte de linguagem associado lidam com todas essas preocupações. O código que gera a sequência agora pode usar `yield return` para retornar os elementos em um método que foi declarado com o modificador `async`. É possível consumir um fluxo assíncrono usando um loop `await foreach` da mesma forma que é possível consumir qualquer sequência usando um loop `foreach`.

Esses novos recursos de linguagem dependem das três novas interfaces adicionadas ao .NET Standard 2.1 e implementadas no .NET Core 3.0:

- <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>
- <xref:System.IAsyncDisposable?displayProperty=nameWithType>

Essas três interfaces devem ser familiares à maioria dos desenvolvedores C#. Elas se comportam de maneira semelhante às suas contrapartes síncronas:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Um tipo que pode não ser familiar é <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>. A estrutura `ValueTask` fornece uma API semelhante para a classe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>. `ValueTask` é usado nas interfaces por motivos de desempenho.

## <a name="convert-to-async-streams"></a>Converter para fluxos assíncronos

Em seguida, converta o método `runPagedQueryAsync` para gerar um fluxo assíncrono. Primeiro, altere a assinatura de `runPagedQueryAsync` para retornar um `IAsyncEnumerable<JToken>` e remova os objetos de progresso e o token de cancelamento da lista de parâmetros, conforme mostrado no código a seguir:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetUpdateSignature" :::

O código inicial processa cada página à medida que a página é recuperada, como mostrado no código a seguir:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetProcessPage" :::

Substitua essas três linhas pelo seguinte código:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetYieldReturnPage" :::

Você também pode remover a declaração de `finalResults` anteriormente nesse método e a instrução `return` que segue o loop que você modificou.

Você terminou as alterações para gerar um fluxo assíncrono. O método finished deve ser semelhante ao seguinte código:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateAsyncStream" :::

Em seguida, você pode alterar o código que consome a coleção para consumir o fluxo assíncrono. Localize o seguinte código em `Main` que processa a coleção de problemas:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetEnumerateOldStyle" :::

Substitua o código pelo seguinte loop `await foreach`:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateAsyncStream" :::

A nova interface <xref:System.Collections.Generic.IAsyncEnumerator%601> deriva de <xref:System.IAsyncDisposable> . Isso significa que o loop anterior descartará o fluxo de forma assíncrona quando o loop for concluído. Você pode imaginar que o loop é semelhante ao seguinte código:

```csharp
int num = 0;
var enumerator = runPagedQueryAsync(client, PagedIssueQuery, "docs").GetEnumeratorAsync();
try
{
    while (await enumerator.MoveNextAsync())
    {
        var issue = enumerator.Current;
        Console.WriteLine(issue);
        Console.WriteLine($"Received {++num} issues in total");
    }
} finally
{
    if (enumerator != null)
        await enumerator.DisposeAsync();
}
```

Por padrão, os elementos de fluxo são processados no contexto capturado. Se você quiser desabilitar a captura do contexto, use o <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> método de extensão. Para obter mais informações sobre contextos de sincronização e como capturar o contexto atual, consulte o artigo sobre como [consumir o padrão assíncrono baseado em tarefa](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

Os fluxos assíncronos dão suporte ao cancelamento usando o mesmo protocolo que outros `async` métodos. Você modificaria a assinatura do método de iterador assíncrono da seguinte maneira para dar suporte ao cancelamento:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateWithCancellation" :::

O <xref:System.Runtime.CompilerServices.EnumeratorCancellationAttribute?dipslayProperty=nameWithType> atributo faz com que o compilador gere código para o <xref:System.Collections.Generic.IAsyncEnumerator%601> que torna o token passado para `GetAsyncEnumerator` visível para o corpo do iterador assíncrono como esse argumento. Dentro `runQueryAsync` do, você pode examinar o estado do token e cancelar mais trabalho, se solicitado.

Você usa outro método de extensão, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.WithCancellation%2A> , para passar o token de cancelamento para o fluxo assíncrono. Você modificaria o loop enumerando os problemas da seguinte maneira:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateWithCancellation" :::

Você pode obter o código para o tutorial concluído do repositório [dotnet/docs](https://github.com/dotnet/docs) na pasta [Csharp/tutoriais/AsyncStreams](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/snippets/generate-consume-asynchronous-streams/finished) .

## <a name="run-the-finished-application"></a>Executar o aplicativo finalizado

Execute o aplicativo novamente. Compare esse comportamento com o comportamento do aplicativo inicial. A primeira página de resultados é enumerada assim que fica disponível. Há uma pausa observável à medida que cada nova página é solicitada e recuperada, e os resultados da próxima página são rapidamente enumerados. O bloco `try` / `catch` não é necessário para lidar com o cancelamento: o chamador pode interromper a enumeração da coleção. O progresso é claramente informado, pois o fluxo assíncrono gera resultados à medida que cada página é baixada. O status de cada problema retornado é incluído diretamente no `await foreach` loop. Você não precisa de um objeto de retorno de chamada para acompanhar o progresso.

Você pode ver as melhorias no uso da memória examinando o código. Não é mais necessário alocar uma coleção para armazenar todos os resultados antes de serem enumerados. O chamador pode determinar como consumir os resultados e se uma coleção de armazenamento é necessária.

Execute o aplicativos inicial e o acabado, e observe você mesmo as diferenças entre as implementações. Depois de terminar, você pode excluir o token de acesso de GitHub criado ao iniciar este tutorial. Se um invasor obtiver acesso a esse token, ele poderá acessar as APIs do GitHub usando suas credenciais.
