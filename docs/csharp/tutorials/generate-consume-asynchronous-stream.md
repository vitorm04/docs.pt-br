---
title: Gerar e consumir fluxos assíncronos
description: Este tutorial avançado ilustra os cenários em que gerar e consumir fluxos assíncronos oferecem uma forma mais natural de trabalhar com sequências de dados que podem ser geradas de forma assíncrona.
ms.date: 02/10/2019
ms.custom: mvc
ms.openlocfilehash: 0fa7c778ca9ce0f0124fcc520dd4de65f2f92ea8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308543"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Tutorial: Gerar e consumir fluxos assíncronos usando o C# 8.0 e .NET Core 3.0

O C#8.0 apresenta **fluxos assíncronos**, que modelam uma fonte de dados de streaming quando os elementos no fluxo de dados podem ser recuperados ou gerados de forma assíncrona. Os fluxos assíncronos contam com novas interfaces introduzidas no .NET Standard 2.1 e implementadas no .NET Core 3.0 para fornecer um modelo de programação natural para fontes de dados de streaming assíncrono.

Neste tutorial, você aprenderá a:

> [!div class="checklist"]
> * Criar uma fonte de dados que gera uma sequência de elementos de dados de forma assíncrona.
> * Consumir essa fonte de dados de forma assíncrona.
> * Reconhecer quando a nova interface e a fonte de dados forem preferenciais para sequências anteriores de dados síncronos.

## <a name="prerequisites"></a>Pré-requisitos

Você precisará configurar seu computador para executar o .NET Core, incluindo o compilador beta do C# 8.0. O compilador beta do C# 8 está disponível com o [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou o mais recente [SDK .NET Core 3.0 versão prévia](https://dotnet.microsoft.com/download/dotnet-core/3.0). Os fluxos assíncronos estão disponíveis a partir do .NET Core 3.0 versão prévia 1.

Você precisará criar um [token de acesso do GitHub](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) para poder acessar o ponto de extremidade GitHub GraphQL. Selecione as seguintes permissões para o Token de acesso do GitHub:

- repo:status
- public_repo

Salve o token de acesso em um local seguro, de modo que possa usá-lo para acessar o ponto de extremidade da API do GitHub.

> [!WARNING]
> Mantenha seu token de acesso pessoal protegido. Qualquer software com seu token de acesso pessoal pode fazer chamadas da API do GitHub usando seus direitos de acesso.

Este tutorial pressupõe que você esteja familiarizado com o C# e .NET, incluindo o Visual Studio ou a CLI do .NET Core.

## <a name="run-the-starter-application"></a>Executar o aplicativo inicial

Você pode obter o código para o aplicativo inicial usado neste tutorial em nosso repositório [dotnet/samples](https://github.com/dotnet/samples) na pasta [csharp/tutoriais/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start).

O aplicativo inicial é um aplicativo de console que usa a interface [GitHub GraphQL](https://developer.github.com/v4/) para recuperar os problemas recentes gravados no repositório [dotnet/docs](https://github.com/dotnet/docs). Comece observando o código a seguir para o método `Main` do aplicativo inicial:

[!code-csharp[StarterAppMain](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

Você pode definir uma variável de ambiente `GitHubKey` para o token de acesso pessoal ou pode substituir o último argumento na chamada para `GenEnvVariable` com seu token de acesso pessoal. Não coloque o código de acesso no código-fonte se for salvar a fonte com outras ou coloque-a em um repositório de origem compartilhado.

Após criar o cliente do GitHub, o código em `Main` criará um objeto de relatório de andamento e um token de cancelamento. Depois que esses objetos forem criados, `Main` chamará `runPagedQueryAsync` para recuperar os 250 problemas mais recente criados. Depois que a tarefa for concluída, os resultados serão exibidos.

Ao executar o aplicativo inicial, você poderá realizar algumas observações importantes sobre como esse aplicativo é executado.  Você verá o progresso informado para cada página retornada do GitHub. É possível observar uma pausa perceptível antes do GitHub retornar cada nova página de problemas. Por fim, os problemas só serão exibidos depois que todas as 10 páginas forem recuperadas do GitHub.

## <a name="examine-the-implementation"></a>Examinar a implementação

A implementação revela por que você observou o comportamento discutido na seção anterior. Examine o código para `runPagedQueryAsync`:

[!code-csharp[RunPagedQueryStarter](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

Vamos nos concentrar no algoritmo de paginação e na estrutura assíncrona do código anterior. (Confira na [documentação do GitHub GraphQL](https://developer.github.com/v4/guides/) mais detalhes sobre a API do GitHub GraphQL). O método `runPagedQueryAsync` enumera os problemas do mais recente ao mais antigo. Ele solicita 25 problemas por página e examina a estrutura `pageInfo` da resposta para continuar com a página anterior. Isso segue o suporte de paginação padrão do GraphQL para respostas com várias páginas. A resposta inclui um objeto `pageInfo` que inclui um valor `hasPreviousPages` e um valor `startCursor` usados para solicitar a página anterior. Os problemas estão na matriz `nodes`. O método `runPagedQueryAsync` anexa esses nós em uma matriz que contém todos os resultados de todas as páginas.

Após a recuperação e a restauração de uma página de resultados, `runPagedQueryAsync` informa o andamento e verifica o cancelamento. Se o cancelamento tiver sido solicitado, `runPagedQueryAsync` gerará um <xref:System.OperationCanceledException>.

Há vários elementos nesse código que podem ser melhorados. Acima de tudo, `runPagedQueryAsync` deve alocar armazenamento para todos os problemas retornados. Este exemplo é interrompido em 250 problemas porque recuperar todos os problemas exigiria muito mais memória para armazenar todos os problemas recuperados. Além disso, os protocolos que dão suporte ao progresso e ao cancelamento tornam o algoritmo mais difícil de entender em sua primeira leitura. Você deve procurar a classe progresso para localizar onde o progresso é informado. Você também tem que rastrear as comunicações por meio de <xref:System.Threading.CancellationTokenSource> e seu associado <xref:System.Threading.CancellationToken> para entender onde o cancelamento foi solicitado e onde ele foi concedido.

## <a name="async-streams-provide-a-better-way"></a>Os fluxos assíncronos fornecem uma melhor maneira

Os fluxos assíncronos e o suporte de linguagem associado lidam com todas essas preocupações. O código que gera a sequência agora pode usar `yield return` para retornar os elementos em um método que foi declarado com o modificador `async`. É possível consumir um fluxo assíncrono usando um loop `await foreach` da mesma forma que é possível consumir qualquer sequência usando um loop `foreach`.

Esses novos recursos de linguagem dependem das três novas interfaces adicionadas ao .NET Standard 2.1 e implementadas no .NET Core 3.0:

```csharp
namespace System.Collections.Generic
{
    public interface IAsyncEnumerable<out T>
    {
        IAsyncEnumerator<T> GetAsyncEnumerator(CancellationToken cancellationToken = default);
    }

    public interface IAsyncEnumerator<out T> : IAsyncDisposable
    {
        T Current { get; }

        ValueTask<bool> MoveNextAsync();
    }
}

namespace System
{
    public interface IAsyncDisposable
    {
        ValueTask DisposeAsync();
    }
}
```

Essas três interfaces devem ser familiares à maioria dos desenvolvedores C#. Elas se comportam de maneira semelhante às suas contrapartes síncronas:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Um tipo que pode não ser familiar é <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>. A estrutura `ValueTask` fornece uma API semelhante para a classe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>. `ValueTask` é usado nas interfaces por motivos de desempenho.

## <a name="convert-to-async-streams"></a>Converter para fluxos assíncronos

Em seguida, converta o método `runPagedQueryAsync` para gerar um fluxo assíncrono. Primeiro, altere a assinatura de `runPagedQueryAsync` para retornar um `IAsyncEnumerable<JToken>` e remova os objetos de progresso e o token de cancelamento da lista de parâmetros, conforme mostrado no código a seguir:

[!code-csharp[FinishedSignature](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

O código inicial processa cada página à medida que a página é recuperada, como mostrado no código a seguir:

[!code-csharp[StarterPaging](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

Substitua essas três linhas pelo seguinte código:

[!code-csharp[FinishedPaging](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

Você também pode remover a declaração de `finalResults` anteriormente nesse método e a instrução `return` que segue o loop que você modificou.

Você terminou as alterações para gerar um fluxo assíncrono. O método concluído deve se parecer com o código a seguir:

[!code-csharp[FinishedGenerate](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

Em seguida, você pode alterar o código que consome a coleção para consumir o fluxo assíncrono. Localize o seguinte código em `Main` que processa a coleção de problemas:

[!code-csharp[EnumerateOldStyle](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

Substitua o código pelo seguinte loop `await foreach`:

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

Você pode obter o código do tutorial concluído no repositório [dotnet/samples](https://github.com/dotnet/samples) na pasta [csharp/tutoriais/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished).

## <a name="run-the-finished-application"></a>Executar o aplicativo finalizado

Execute o aplicativo novamente. Compare esse comportamento com o comportamento do aplicativo inicial. A primeira página de resultados é enumerada assim que fica disponível. Há uma pausa observável à medida que cada nova página é solicitada e recuperada, e os resultados da próxima página são rapidamente enumerados. O bloco `try` / `catch` não é necessário para lidar com o cancelamento: o chamador pode interromper a enumeração da coleção. O progresso é claramente informado, pois o fluxo assíncrono gera resultados à medida que cada página é baixada.

Você pode ver as melhorias no uso da memória examinando o código. Não é mais necessário alocar uma coleção para armazenar todos os resultados antes de serem enumerados. O chamador pode determinar como consumir os resultados e se uma coleção de armazenamento é necessária.

Execute o aplicativos inicial e o acabado, e observe você mesmo as diferenças entre as implementações. Depois de terminar, você pode excluir o token de acesso de GitHub criado ao iniciar este tutorial. Se um invasor obtiver acesso a esse token, ele poderá acessar as APIs do GitHub usando suas credenciais.
