---
title: Cria um cliente REST usando .NET Core
description: Este tutorial ensina vários recursos no .NET Core e da linguagem C#.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 13466b717d0676c2db5edf4c98a4ead3e673b96c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227253"
---
# <a name="rest-client"></a>Cliente REST

## <a name="introduction"></a>Introdução
Este tutorial ensina vários recursos no .NET Core e da linguagem C#. Você aprenderá:
*   As noções básicas da CLI (Interface de Linha de Comando) do .NET Core.
*   Uma visão geral dos recursos da linguagem C#.
*   Gerenciamento de dependências com o NuGet
*   Comunicações HTTP
*   Processamento de informações de JSON
*   Gerenciamento de configuração com Atributos. 

Você compilará um aplicativo que emite solicitações HTTP para um serviço REST no GitHub. Você lerá informações no formato JSON e converterá esse pacote JSON em objetos C#. Por fim, você verá como trabalhar com objetos C#.

Há vários recursos neste tutorial. Vamos compilá-los individualmente.

Se preferir acompanhar com o [exemplo final](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) para esse tópico, você poderá baixá-lo. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Pré-requisitos
Você precisará configurar seu computador para executar o .NET Core. Você encontrará as instruções de instalação na página do [.NET Core](https://www.microsoft.com/net/core). Execute esse aplicativo no Windows, Linux, macOS ou em um contêiner do Docker. Será necessário instalar o editor de código de sua preferência. As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma. No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.
## <a name="create-the-application"></a>Criar o aplicativo
A primeira etapa é criar um novo aplicativo. Abra um prompt de comando e crie um novo diretório para seu aplicativo. Torne ele o diretório atual. Digite o comando `dotnet new console` no prompt de comando. Isso cria os arquivos iniciais de um aplicativo "Olá, Mundo" básico.

Antes de começar as modificações, vamos percorrer as etapas para execução do aplicativo simples Hello World. Depois de criar o aplicativo, digite `dotnet restore` ([veja a observação](#dotnet-restore-note)) no prompt de comando. Esse comando executa o processo de restauração do pacote NuGet. O NuGet é um gerenciador de pacotes do .NET. Esse comando baixa qualquer uma das dependências ausentes para seu projeto. Como esse é um novo projeto, nenhuma das dependências foram aplicadas, portanto, a primeira execução baixará a estrutura do .NET Core. Após essa etapa inicial, você só precisará executar o `dotnet restore` ([veja a observação](#dotnet-restore-note)) ao adicionar novos pacotes dependentes, ou atualizar as versões de qualquer uma de suas dependências.  

Depois de restaurar os pacotes, execute `dotnet build`. Isso executa o mecanismo de compilação e cria seu aplicativo. Por fim, execute `dotnet run` para executar o aplicativo.

## <a name="adding-new-dependencies"></a>Adicionar novas dependências
Uma das principais metas de design para o .NET Core é minimizar o tamanho da instalação do .NET. Se um aplicativo precisar de mais bibliotecas para alguns de seus recursos, adicione essas dependências ao seu arquivo de projeto de C# (\*.csproj). Para nosso exemplo, você precisará adicionar o pacote `System.Runtime.Serialization.Json` para que seu aplicativo possa processar as respostas em JSON.

Abra seu arquivo de projeto `csproj`. A primeira linha do arquivo deve aparecer assim:

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Adicione o seguinte logo após esta linha: 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
A maioria dos editores de código fornece conclusão para versões diferentes dessas bibliotecas. Convém usar a versão mais recente de qualquer pacote que você adicionar. No entanto, é importante ter certeza de que as versões de todos os pacotes correspondam, e que também correspondam à versão da estrutura de aplicativo do .NET Core.

Após fazer essas alterações, execute `dotnet restore` ([veja a observação](#dotnet-restore-note)) novamente para que o pacote seja instalado em seu sistema.

## <a name="making-web-requests"></a>Como fazer solicitações da Web
Agora você está pronto para começar a obter dados da Web. Neste aplicativo, você lerá informações da [API do GitHub](https://developer.github.com/v3/). Vamos ler informações sobre os projetos em [.NET Foundation](http://www.dotnetfoundation.org/). Comece fazendo a solicitação à API do GitHub para recuperar informações sobre os projetos. O ponto de extremidade que você usará é: [ https://api.github.com/orgs/dotnet/repos ](https://api.github.com/orgs/dotnet/repos). Você quer obter todas as informações sobre esses projetos, portanto, use uma solicitação HTTP GET.
O navegador também usa solicitações HTTP GET, para que você possa colar essa URL em seu navegador e ver as informações que receberá.

Use a classe <xref:System.Net.Http.HttpClient> para fazer solicitações da Web. Como todas as APIs .NET modernas, a <xref:System.Net.Http.HttpClient> oferece suporte apenas aos métodos assíncronos para suas APIs de longa execução.
Comece criando um método assíncrono. Você preencherá a implementação à medida que compila a funcionalidade do aplicativo. Comece abrindo o arquivo `program.cs` no diretório do projeto e adicionando o seguinte método à classe `Program`:

```csharp
private static async Task ProcessRepositories()
{
    
}
```

Será necessário adicionar uma instrução `using` na parte superior de seu método `Main` para que o compilador de C# reconheça o tipo <xref:System.Threading.Tasks.Task>:

```csharp
using System.Threading.Tasks;
```

Se você compilar o projeto neste momento, receberá um aviso gerado para esse método, pois ele não contém operadores `await` e executará de forma síncrona. Ignore isso por enquanto. Adicione os operadores `await` à medida que você preenche o método.

Em seguida, renomeie o namespace definido na instrução `namespace`, alterando o padrão de `ConsoleApp` para `WebAPIClient`. Posteriormente, definiremos uma classe `repo` neste namespace.

Em seguida, atualize o método `Main` para chamar esse método. O método `ProcessRepositories` retorna uma Tarefa, e você não deve sair do programa antes da conclusão dessa tarefa. Portanto, use o método `Wait` para bloquear e esperar a conclusão da tarefa:

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

Agora, você tem um programa que não faz nada, mas o faz de forma assíncrona. Vamos melhorar isso.

Primeiro você precisa de um objeto que é capaz de recuperar dados da Web; você pode usar um <xref:System.Net.Http.HttpClient> para fazer isso. Esse objeto manipula a solicitação e as respostas. Crie uma única instância desse tipo na classe `Program` dentro do arquivo Program.cs.

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static void Main(string[] args)
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

Também será necessário adicionar duas instruções using novas na parte superior do arquivo para que isso seja compilado:

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

O serializador JSON converte os dados em JSON em objetos de C#. A primeira tarefa serve para definir um tipo de classe em C# para conter as informações usadas nessa resposta. Vamos compilar isso lentamente, então comece com um tipo C# simples que contém o nome do repositório:

```csharp
using System;

namespace WebAPIClient
{
    public class repo
    {
        public string name;
    }
}
``` 

Coloque o código acima em um novo arquivo chamado 'repo.cs'. Esta versão da classe representa o caminho mais simples para processar os dados em JSON. O nome da classe e o nome do membro corresponderem aos nomes usados no pacote JSON, em vez de seguir as convenções em C#. Corrija isso mais tarde fornecendo alguns atributos de configuração. Essa classe demonstra outro recurso importante de serialização e desserialização em JSON: nem todos os campos no pacote JSON fazem parte dessa classe.
O serializador JSON ignorará as informações que não estão incluídas no tipo de classe que está sendo usado.
Esse recurso facilita a criação de tipos que funcionam apenas com um subconjunto dos campos no pacote JSON.

Agora que você criou o tipo, vamos desserializá-lo. Você precisará criar um objeto <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Este objeto deve saber o tipo de CLR esperada para o pacote JSON que ele recupera. O pacote do GitHub contém uma sequência de repositórios, então um `List<repo>` é o tipo correto. Adicione a seguinte linha ao seu método `ProcessRepositories`:

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

Você está usando dois novos namespaces, portanto será necessário adicioná-los também:

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

Em seguida, você usará o serializador para converter JSON em objetos de C#. Substitua a chamada para <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> em seu método `ProcessRepositories` pelas duas linhas a seguir:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

Observe que agora você está usando <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> em vez de <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>. O serializador usa um fluxo, em vez de uma cadeia de caracteres, como sua fonte. Vamos explicar alguns recursos da linguagem C# que estão sendo usados na segunda linha acima. O argumento <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> é uma expressão `await`. Expressões await podem aparecer em quase todo lugar em seu código, apesar de que até o momento, você apenas as viu como parte de uma instrução de atribuição.

Em segundo lugar, o operador `as` converte do tipo de tempo de compilação do `object` para `List<repo>`. A declaração de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declara que ele retorna um objeto do tipo <xref:System.Object?displayProperty=nameWithType>. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> retornará o tipo especificado no momento da construção (`List<repo>` neste tutorial). Se a conversão não tiver êxito, o operador `as` será avaliado com `null`, em vez de gerar uma exceção.

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

Antes de adicionar mais recursos, vamos abordar o tipo `repo` e fazê-lo seguir convenções mais padrão de C#. Faça isso anotando a tipo `repo` com *atributos* que controlem o modo como o serializador JSON funciona. Em seu caso, você usará esses atributos para definir um mapeamento entre os nomes de chave JSON e os nomes de classe e de membros de C#. Os dois atributos usados são `DataContract` e `DataMember`. Por convenção, todas as classes de atributo terminam com o sufixo `Attribute`. No entanto, não é necessário usar esse sufixo ao aplicar um atributo. 

Os atributos `DataContract` e `DataMember` são atributos em uma biblioteca diferente, então você precisará adicionar essa biblioteca ao seu arquivo de projeto C# como uma dependência. Adicione a seguinte linha à seção `<ItemGroup>` de seu arquivo de projeto:

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

Depois de salvar o arquivo, execute `dotnet restore` ([veja a observação](#dotnet-restore-note)) para recuperar esse pacote.

Em seguida, abra o arquivo `repo.cs`. Vamos alterar o nome para usar Pascal Case e soletrar o nome `Repository` completo. Ainda queremos mapear os nós de 'repositório' de JSON para esse tipo, então será necessário adicionar o atributo `DataContract` à declaração de classe. Você definirá a propriedade `Name` do atributo como o nome de nós de JSON mapeados para esse tipo:

```csharp
[DataContract(Name="repo")]
public class Repository
```

O <xref:System.Runtime.Serialization.DataContractAttribute> é um membro do namespace <xref:System.Runtime.Serialization>, então você precisará adicionar a instrução `using` apropriado na parte superior do arquivo:

```csharp
using System.Runtime.Serialization;
```

Você alterou o nome da classe `repo` para `Repository`, portanto, será necessário fazer a mesma alteração em Program.cs (alguns editores podem oferecer suporte a uma refatoração de renomeação que fará essa alteração automaticamente:)

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

Em seguida, vamos fazer a mesma alteração com o campo `name` usando a classe <xref:System.Runtime.Serialization.DataMemberAttribute>. Faça as seguintes alterações na declaração do campo `name` em repo.cs:

```csharp
[DataMember(Name="name")]
public string Name;
```

Essa alteração significa que você precisa alterar o código que grava o nome de cada repositório em program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Faça uma `dotnet build` seguido por um `dotnet run` para certificar-se de que você tem os mapeamentos corretos. Você deve ver o mesmo resultado de antes. Antes, processamos mais propriedades do servidor Web, vamos fazer mais uma alteração na classe `Repository`. O membro `Name` é um campo acessível publicamente. Essa não é uma boa prática orientada a objeto, então vamos alterá-lo para uma propriedade. Para nossos propósitos, não é necessário executar nenhum código específico ao obter ou configurar a propriedade, mas a alteração de uma propriedade facilita a adição dessas alterações posteriormente sem interromper qualquer código que usa a classe `Repository`.

Remova a definição de campo e substitua-a por uma [propriedade autoimplementada](../programming-guide/classes-and-structs/auto-implemented-properties.md):

```csharp
public string Name { get; set; }
```

O compilador gera o corpo dos acessadores `get` e `set`, bem como um campo particular para armazenar o nome. Seria semelhante ao código a seguir, que você pode digitar manualmente:

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

Vamos fazer mais uma alteração antes de adicionar novos recursos. O método `ProcessRepositories` pode fazer o trabalho assíncrono e retornar uma coleção de repositórios. Vamos retornar o `List<Repository>` desse método e mover o código que grava as informações no método `Main`.

Altere a assinatura de `ProcessRepositories` para retornar uma tarefa cujo resultado é uma lista de objetos `Repository`:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Depois, basta retornar os repositórios depois de processar a resposta JSON:

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

O compilador gera o objeto `Task<T>` para o retorno porque você marcou esse método como `async`.
Em seguida, vamos modificar o método `Main` para que ele capture esses resultados e grave cada nome de repositório no console. Seu método `Main` terá a seguinte aparência:

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

O acesso à propriedade `Result` de uma Tarefa é bloqueado até que a tarefa seja concluída. Normalmente, seria preferível `await` (aguardar) a conclusão da tarefa, como no método `ProcessRepositories`, mas isso não é permitido no método `Main`.

## <a name="reading-more-information"></a>Ler mais informações

Vamos concluir isso processando mais algumas propriedades no pacote JSON que são enviadas da API do GitHub. Não convém capturar tudo, mas a adição de algumas propriedades demonstrará mais alguns recursos da linguagem C#.

Vamos começar pela adição de alguns tipos mais simples para a definição de classe `Repository`. Adicione essas propriedades à classe:

```csharp
[DataMember(Name="description")]
public string Description { get; set; }

[DataMember(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[DataMember(Name="homepage")]
public Uri Homepage { get; set; }

[DataMember(Name="watchers")]
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

Esse formato não segue o formato <xref:System.DateTime> padrão do .NET. Por isso, você precisará escrever um método de conversão personalizado. Provavelmente você também não quer expor a cadeia de caracteres bruta aos usuários da classe `Repository`. Os atributos podem ajudar a controlar isto também. Primeiro, defina uma propriedade `private` que conterá a representação de cadeia de caracteres da data e hora em sua classe `Repository`:

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

O atributo `DataMember` informa ao serializador de que isso deve ser processado, mesmo que não seja um membro público. Em seguida, você precisa escrever uma propriedade pública somente leitura que converte a cadeia de caracteres em um objeto <xref:System.DateTime> válido, e retorna esse <xref:System.DateTime>:

```csharp
[IgnoreDataMember]
public DateTime LastPush
{
    get
    {
        return DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
    }
}
```

Vamos falar sobre as novas construções acima. O atributo `IgnoreDataMember` instrui o serializador que esse tipo não deve ser lido para ou gravado de qualquer objeto JSON. Essa propriedade contém apenas um acessador `get`. Não há nenhum acessador `set`. É assim que você define uma propriedade *somente leitura* em C#. (Sim, você pode criar propriedades *somente gravação* em C#, mas o valor delas é limitado.) O método <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analisa uma cadeia de caracteres e cria um objeto <xref:System.DateTime> usando um formato de data fornecido e adiciona outros metadados a `DateTime` usando um objeto `CultureInfo`. Se a operação de análise falhar, o acessador da propriedade gerará uma exceção.

Para usar <xref:System.Globalization.CultureInfo.InvariantCulture>, você precisará adicionar o namespace <xref:System.Globalization> às instruções `using` em `repo.cs`:

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
