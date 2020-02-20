---
title: Cria um cliente REST usando .NET Core
description: Este tutorial ensina vários recursos no .NET Core e da linguagem C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: f85d50b222d06caa045e22b452d0902aaac66088
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503979"
---
# <a name="rest-client"></a>Cliente REST

Este tutorial ensina vários recursos no .NET Core e da linguagem C#. Você aprenderá:

* As noções básicas do CLI do .NET Core.
* Uma visão geral dos recursos da linguagem C#.
* Gerenciamento de dependências com o NuGet
* Comunicações HTTP
* Processamento de informações de JSON
* Gerenciamento de configuração com Atributos.

Você compilará um aplicativo que emite solicitações HTTP para um serviço REST no GitHub. Você lerá informações no formato JSON e converterá esse pacote JSON em objetos C#. Por fim, você verá como trabalhar com objetos C#.

Há muitos recursos neste tutorial. Vamos compilá-los individualmente.

Se preferir acompanhar com o [exemplo final](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) para esse tópico, você poderá baixá-lo. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Prerequisites

Você precisará configurar seu computador para executar o .NET Core. Você pode encontrar as instruções de instalação na página de [downloads do .NET Core](https://dotnet.microsoft.com/download) . Execute esse aplicativo no Windows, Linux, macOS ou em um contêiner do Docker.
Você precisará instalar o editor de código de sua preferência. As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma. No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.

## <a name="create-the-application"></a>Criar o aplicativo

A primeira etapa é criar um novo aplicativo. Abra um prompt de comando e crie um novo diretório para seu aplicativo. Torne ele o diretório atual. Digite o seguinte comando em uma janela de console:

```dotnetcli
dotnet new console --name WebApiClient
```

Isso cria os arquivos iniciais de um aplicativo "Olá, Mundo" básico. O nome do projeto é "WebApiClient". Como esse é um novo projeto, nenhuma das dependências está em vigor. A primeira execução baixará o .NET Core Framework, instalará um certificado de desenvolvimento e executará o Gerenciador de pacotes NuGet para restaurar as dependências ausentes.

Antes de começar a fazer modificações, digite `dotnet run` ([veja a observação](#dotnet-restore-note)) no prompt de comando para executar seu aplicativo. `dotnet run` executará automaticamente `dotnet restore` se estiverem faltando dependências em seu ambiente. Ele também executará `dotnet build` se seu aplicativo precisar ser reconstruído.
Após sua configuração inicial, você só precisará executar `dotnet restore` ou `dotnet build` quando fizer sentido para seu projeto.

## <a name="adding-new-dependencies"></a>Adicionar novas dependências

Uma das principais metas de design para o .NET Core é minimizar o tamanho da instalação do .NET. Se um aplicativo precisar de mais bibliotecas para alguns de seus recursos, adicione essas dependências ao seu arquivo de projeto de C# (\*.csproj). Para nosso exemplo, você precisará adicionar o pacote `System.Runtime.Serialization.Json`, para que seu aplicativo possa processar respostas JSON.

Você precisará do pacote de `System.Runtime.Serialization.Json` para este aplicativo. Adicione-o ao seu projeto executando o seguinte comando da [CLI do .net](../../core/tools/dotnet-add-package.md) :

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a>Como fazer solicitações da Web

Agora você está pronto para começar a obter dados da Web. Neste aplicativo, você lerá informações da [API do GitHub](https://developer.github.com/v3/). Vamos ler informações sobre os projetos em [.NET Foundation](https://www.dotnetfoundation.org/). Comece fazendo a solicitação à API do GitHub para recuperar informações sobre os projetos. O ponto de extremidade que você usará é: <https://api.github.com/orgs/dotnet/repos>. Você quer obter todas as informações sobre esses projetos, portanto, use uma solicitação HTTP GET.
O navegador também usa solicitações HTTP GET, para que você possa colar essa URL em seu navegador e ver as informações que receberá.

Use a classe <xref:System.Net.Http.HttpClient> para fazer solicitações da Web. Como todas as APIs .NET modernas, a <xref:System.Net.Http.HttpClient> oferece suporte apenas aos métodos assíncronos para suas APIs de longa execução.
Comece criando um método assíncrono. Você preencherá a implementação à medida que compila a funcionalidade do aplicativo. Comece abrindo o arquivo `program.cs` no diretório do projeto e adicionando o seguinte método à classe `Program`:

```csharp
private static async Task ProcessRepositories()
{
}
```

Você precisará adicionar uma diretiva `using` na parte superior do seu método `Main` para que o C# compilador reconheça o tipo de <xref:System.Threading.Tasks.Task>:

```csharp
using System.Threading.Tasks;
```

Se você compilar o projeto neste momento, receberá um aviso gerado para esse método, pois ele não contém operadores `await` e executará de forma síncrona. Ignore isso por enquanto. Adicione os operadores `await` à medida que você preenche o método.

Em seguida, renomeie o namespace definido na instrução `namespace`, alterando o padrão de `ConsoleApp` para `WebAPIClient`. Posteriormente, definiremos uma classe `repo` neste namespace.

Em seguida, atualize o método `Main` para chamar esse método. O método `ProcessRepositories` retorna uma tarefa e você não deve sair do programa antes que essa tarefa seja concluída. Portanto, você deve alterar a assinatura de `Main`. Adicione o modificador de `async` e altere o tipo de retorno para `Task`. Em seguida, no corpo do método, adicione uma chamada para `ProcessRepositories`. Adicione a palavra-chave `await` a essa chamada de método:

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

Agora, você tem um programa que não faz nada, mas o faz de forma assíncrona. Vamos melhorar isso.

Primeiro você precisa de um objeto que é capaz de recuperar dados da Web; você pode usar um <xref:System.Net.Http.HttpClient> para fazer isso. Esse objeto manipula a solicitação e as respostas. Crie uma instância única desse tipo na classe `Program` dentro do arquivo *Program.cs* .

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static async Task Main(string[] args)
        {
            //...
        }
    }
}
```

Vamos voltar ao método `ProcessRepositories` e preencher uma primeira versão dele:

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

Você também precisará adicionar duas novas diretivas de `using` na parte superior do arquivo para que isso seja compilado:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

A primeira versão faz uma solicitação da Web para ler a lista de todos os repositórios na organização dotnet foundation. (A ID do gitHub para o .NET Foundation é 'dotnet'). As primeiras linhas configuram o <xref:System.Net.Http.HttpClient> para essa solicitação. Primeiro, ele é configurado para aceitar as respostas JSON do GitHub.
Esse formato é simplesmente JSON. A próxima linha adiciona um cabeçalho de agente do usuário para todas as solicitações deste objeto. Esses dois cabeçalhos são verificados pelo código do servidor GitHub e são necessários para recuperar informações do GitHub.

Depois de configurar o <xref:System.Net.Http.HttpClient>, faça uma solicitação da Web e recupere a resposta. Nesta primeira versão, você usa o método de conveniência <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType>. Este método prático inicia uma tarefa que faz a solicitação da Web e, depois, quando a solicitação retornar, ele lê o fluxo de resposta e extrai o conteúdo do fluxo. O corpo da resposta retorna como um <xref:System.String>. A cadeia de caracteres fica disponível após a conclusão da tarefa.

As duas últimas linhas desse método aguardam a tarefa e, depois, imprimem a resposta no console.
Compilar o aplicativo e executá-lo. O aviso de compilação desapareceu, pois agora o `ProcessRepositories` contêm um operador `await`. Você verá uma longa exibição do texto formatado em JSON.

## <a name="processing-the-json-result"></a>Processar o resultado JSON

Neste ponto, você já escreveu o código para recuperar uma resposta de um servidor da Web e exibiu o texto contido nessa resposta. Agora, vamos converter essa resposta em JSON em objetos de C#.

A classe <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> serializa objetos para JSON e desserializa JSON em objetos. Comece definindo uma classe para representar o `repo` objeto JSON retornado da API do GitHub:

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; }
    }
}
```

Coloque o código acima em um novo arquivo chamado 'repo.cs'. Esta versão da classe representa o caminho mais simples para processar os dados em JSON. O nome da classe e o nome do membro corresponderem aos nomes usados no pacote JSON, em vez de seguir as convenções em C#. Corrija isso mais tarde fornecendo alguns atributos de configuração. Essa classe demonstra outro recurso importante de serialização e desserialização em JSON: nem todos os campos no pacote JSON fazem parte dessa classe.
O serializador JSON ignorará as informações que não estão incluídas no tipo de classe que está sendo usado.
Esse recurso facilita a criação de tipos que funcionam apenas com um subconjunto dos campos no pacote JSON.

Agora que você criou o tipo, vamos desserializá-lo. 

Em seguida, você usará o serializador para converter JSON em objetos de C#. Substitua a chamada para <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> em seu método `ProcessRepositories` com as três linhas a seguir:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

Você está usando um novo namespace, portanto, você precisará adicioná-lo na parte superior do arquivo também:

```csharp
using System.Text.Json;
```

Observe que agora você está usando <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> em vez de <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>. O serializador usa um fluxo, em vez de uma cadeia de caracteres, como sua fonte. Vamos explicar alguns recursos do C# idioma que estão sendo usados na segunda linha do trecho de código anterior. O primeiro argumento para <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> é uma expressão de `await`. (Os outros dois parâmetros são opcionais e são omitidos no trecho de código.) As expressões Await podem aparecer quase em qualquer lugar no seu código, embora até agora você as tenha visto apenas como parte de uma instrução de atribuição. O método `Deserialize` é *genérico*, o que significa que você deve fornecer argumentos de tipo para o tipo de objeto que deve ser criado a partir do texto JSON. Neste exemplo, você está desserializando para um `List<Repository>`, que é outro objeto genérico, o <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. A classe `List<>` armazena uma coleção de objetos. O argumento Type declara o tipo de objetos armazenados no `List<>`. O texto JSON representa uma coleção de objetos de repositório, portanto, o argumento de tipo é `Repository`.

Você está quase terminando esta seção. Agora que você converteu o JSON em objetos C#, vamos exibir o nome de cada repositório. Substitua as linhas que mostram:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

pelo seguinte:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Compile e execute o aplicativo. Ele imprimirá os nomes dos repositórios que fazem parte do .NET Foundation.

## <a name="controlling-serialization"></a>Controle da serialização

Antes de adicionar mais recursos, vamos abordar a propriedade `name` usando o atributo `[JsonPropertyName]`. Faça as seguintes alterações na declaração do campo `name` em repo.cs:

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

Para usar `[JsonPropertyName]` atributo, será necessário adicionar o namespace <xref:System.Text.Json.Serialization> às diretivas `using`:

```csharp
using System.Text.Json.Serialization;
```

Essa alteração significa que você precisa alterar o código que grava o nome de cada repositório em program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Execute `dotnet run` para certificar-se de que você tem os mapeamentos corretos. Você deve ver o mesmo resultado de antes.

Vamos fazer mais uma alteração antes de adicionar novos recursos. O método `ProcessRepositories` pode fazer o trabalho assíncrono e retornar uma coleção de repositórios. Vamos retornar o `List<Repository>` desse método e mover o código que grava as informações no método `Main`.

Altere a assinatura de `ProcessRepositories` para retornar uma tarefa cujo resultado é uma lista de objetos `Repository`:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Depois, basta retornar os repositórios depois de processar a resposta JSON:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

O compilador gera o objeto `Task<T>` para o retorno porque você marcou esse método como `async`.
Em seguida, vamos modificar o método `Main` para que ele capture esses resultados e grave cada nome de repositório no console. Seu método `Main` terá a seguinte aparência:

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a>Ler mais informações

Vamos concluir isso processando mais algumas propriedades no pacote JSON que são enviadas da API do GitHub. Não convém capturar tudo, mas a adição de algumas propriedades demonstrará mais alguns recursos da linguagem C#.

Vamos começar pela adição de alguns tipos mais simples para a definição de classe `Repository`. Adicione essas propriedades à classe:

```csharp
[JsonPropertyName("description")]
public string Description { get; set; }

[JsonPropertyName("html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName("homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName("watchers")]
public int Watchers { get; set; }
```

Essas propriedades têm conversões internas do tipo cadeia de caracteres (que é o que os pacotes JSON contêm) para o tipo de destino. O tipo <xref:System.Uri> pode ser novidade para você. Ele representa um URI, ou, nesse caso, uma URL. No caso dos tipos `Uri` e `int`, se o pacote JSON contiver dados que não são convertidos para o tipo de destino, a ação de serialização lançará uma exceção.

Depois de adicioná-los, atualize o método `Main` para exibir esses elementos:

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```

Como etapa final, vamos adicionar as informações para a última operação de envio por push. Essas informações são formatadas dessa maneira na resposta JSON:

```json
2016-02-08T21:27:00Z
```

Esse formato não segue o formato <xref:System.DateTime> padrão do .NET. Por isso, você precisará escrever um método de conversão personalizado. Provavelmente você também não quer expor a cadeia de caracteres bruta aos usuários da classe `Repository`. Os atributos podem ajudar a controlar isto também. Primeiro, defina uma propriedade `public` que conterá a representação da cadeia de caracteres da data e hora em sua classe `Repository` e uma propriedade `LastPush` `readonly` que retorna uma cadeia de caracteres formatada que representa a data de retorno:

```csharp
[JsonPropertyName("pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

Vamos examinar as novas construções que acabamos de definir. A propriedade `LastPush` é definida usando um *membro expression-apto para* para o acessador `get`. Não há nenhum acessador `set`. Omitir o acessador de `set` é como você define uma propriedade *somente leitura* no C#. (Sim, você pode criar propriedades *somente gravação* no C#, mas seu valor é limitado.) O método <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analisa uma cadeia de caracteres e cria um objeto <xref:System.DateTime> usando um formato de data fornecido e adiciona metadados adicionais ao `DateTime` usando um objeto `CultureInfo`. Se a operação de análise falhar, o acessador da propriedade gerará uma exceção.

Para usar <xref:System.Globalization.CultureInfo.InvariantCulture>, será necessário adicionar o namespace <xref:System.Globalization> às diretivas `using` no `repo.cs`:

```csharp
using System.Globalization;
```

Por fim, adicione mais uma instrução de saída no console, e você estará pronto para compilar e executar esse aplicativo novamente:

```csharp
Console.WriteLine(repo.LastPush);
```

Agora, sua versão deve corresponder ao [exemplo finalizado](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).

## <a name="conclusion"></a>Conclusão

Este tutorial mostrou como fazer solicitações da Web, analisar o resultados e exibir as propriedades dos resultados. Você também adicionou novos pacotes como dependências em seu projeto. Você viu alguns dos recursos da linguagem C# que dão suporte a técnicas orientadas a objeto.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
