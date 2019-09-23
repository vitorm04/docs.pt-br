---
title: Migrar um serviço de solicitação-resposta do WCF para gRPC-gRPC para desenvolvedores do WCF
description: Saiba como migrar um serviço de solicitação-resposta simples do WCF para o gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: ac9eecf66a7ac37a1df9714e6383f7eaebae4781
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184305"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a>Migrar um serviço de solicitação-resposta WCF para um RPC unário gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Esta seção aborda como migrar um serviço de solicitação-resposta básico no WCF para um serviço RPC unário no ASP.NET Core gRPC. Esses serviços são os tipos de serviço mais simples no Windows Communication Foundation (WCF) e no gRPC, portanto, é um ótimo lugar para começar. Depois de migrar o serviço, você aprenderá a gerar uma biblioteca de cliente do `.proto` mesmo arquivo para consumir o serviço de um aplicativo cliente .net.

## <a name="the-wcf-solution"></a>A solução WCF

A [solução PortfoliosSample](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) inclui um serviço de portfólio simples de solicitação-resposta para baixar um único portfólio ou todos os portfólios de um determinado Trader. O serviço é definido na interface `IPortfolioService` com um `ServiceContract` atributo:

```csharp
[ServiceContract]
public interface IPortfolioService
{
    [OperationContract]
    Task<Portfolio> Get(Guid traderId, int portfolioId);

    [OperationContract]
    Task<List<Portfolio>> GetAll(Guid traderId);
}
```

O `Portfolio` modelo é uma classe C# simples marcada com [DataContract](xref:System.Runtime.Serialization.DataContractAttribute), incluindo uma lista de `PortfolioItem` objetos. Esses modelos são definidos no `TraderSys.PortfolioData` projeto, juntamente com uma classe de repositório que representa uma abstração de acesso a dados.

```csharp
[DataContract]
public class Portfolio
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public Guid TraderId { get; set; }

    [DataMember]
    public List<PortfolioItem> Items { get; set; }
}

[DataContract]
public class PortfolioItem
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public int ShareId { get; set; }

    [DataMember]
    public int Holding { get; set; }

    [DataMember]
    public decimal Cost { get; set; }
}
```

A `ServiceContract` implementação usa uma classe `DataContract` de repositório fornecida por meio de injeção de dependência que retorna instâncias dos tipos.

```csharp
public class PortfolioService : IPortfolioService
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }

    public async Task<Portfolio> Get(Guid traderId, int portfolioId)
    {
        return await _repository.GetAsync(traderId, portfolioId);
    }

    public async Task<List<Portfolio>> GetAll(Guid traderId)
    {
        return await _repository.GetAllAsync(traderId);
    }
}
```

## <a name="the-portfoliosproto-file"></a>O arquivo portfolios. proto

Se você seguiu as instruções na seção anterior, deve ter um projeto gRPC com um `portfolios.proto` arquivo parecido com este.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

A primeira etapa é migrar as `DataContract` classes para seus equivalentes Protobuf.

## <a name="convert-the-datacontracts-to-grpc-messages"></a>Converter os DataContracts em mensagens gRPC

A `PortfolioItem` classe será convertida primeiro em uma mensagem Protobuf, pois a `Portfolio` classe depende dela. A classe é muito simples e três das propriedades são mapeadas diretamente para os tipos de dados gRPC. A `Cost` Propriedade, que representa o preço pago pelos compartilhamentos na compra, `decimal` é um campo, e gRPC `float` só `double` dá suporte a ou para números reais, que não são adequados para a moeda. Como os preços de compartilhamento variam em um mínimo de uma centésimo, o custo pode ser expresso `int32` como uma das centavos.

> [!NOTE]
> Lembre-se `camelCase` de usar para nomes de `.proto` campo em seu C# arquivo; o gerador de código `PascalCase` os converterá em para você e os usuários de outras linguagens lhe agradecerão por respeitar seus diferentes padrões de codificação.

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 shareId = 2;
    int32 holding = 3;
    int32 costCents = 4;
}
```

A `Portfolio` classe é um pouco mais complicada. No código WCF, o desenvolvedor usou um `Guid` para a `TraderId` Propriedade e contém um `List<PortfolioItem>`. No Protobuf, que não tem um tipo de primeira `UUID` classe, você deve usar um `string` para o `traderId` campo e analisá-lo em seu próprio código. Para a lista de itens, use a `repeated` palavra-chave no campo.

```protobuf
message Portfolio {
    int32 id = 1;
    string traderId = 2;
    repeated PortfolioItem items = 3;
}
```

Agora temos nossas mensagens de dados, podemos declarar os pontos de extremidade de RPC do serviço.

## <a name="convert-the-servicecontract-to-a-grpc-service"></a>Converter o ServiceContract em um serviço gRPC

O método `Get` WCF usa dois parâmetros: `Guid traderId` e `int portfolioId`. os métodos de serviço gRPC podem pegar apenas um único parâmetro, portanto, uma mensagem deve ser criada para conter os dois valores. É uma prática comum nomear esses objetos de solicitação com o mesmo nome que o método e o `Request`sufixo. Novamente, `string` o está sendo usado para `traderId` o campo em `Guid`vez de.

O serviço pode simplesmente retornar uma `Portfolio` mensagem diretamente, mas novamente, isso poderia afetar a compatibilidade com versões anteriores no futuro. É uma prática `Request` recomendada definir mensagens e `Response` separadas para cada método em um serviço, mesmo se muitos deles forem os mesmos no momento, portanto, declare uma `GetResponse` mensagem com um único `Portfolio` campo.

O exemplo a seguir mostra a declaração do método de serviço gRPC usando `GetRequest` a mensagem:

```protobuf
message GetRequest {
    string traderId = 1;
    int32 portfolioId = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

O método `GetAll` WCF usa apenas um único parâmetro, `traderId`, portanto, pode parecer que ele pode ser `string` especificado como o tipo de parâmetro, mas gRPC requer um tipo de mensagem definido. Esse requisito ajuda a impor a prática de usar mensagens personalizadas para todas as entradas e saídas, para compatibilidade com versões anteriores futuras.

O método WCF também retornou `List<Portfolio>`um, mas, pelo mesmo motivo, ele não permite tipos de parâmetro simples, `repeated Portfolio` gRPC não permitirá como um tipo de retorno. Em vez disso, `GetAllResponse` crie um tipo para encapsular a lista.

> [!WARNING]
> Você pode estar tentado a criar uma `PortfolioList` mensagem ou algo semelhante e usá-la em vários métodos de serviço, mas deve resistir a essa tentação. É impossível saber como os vários métodos em um serviço podem evoluir no futuro, portanto, mantenha suas mensagens específicas e separadas de forma limpa.

```protobuf
message GetAllRequest {
    string traderId = 1;
}

message PortfolioList {
    repeated Portfolio portfolios = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (Portfolio);
    rpc GetAll(GetAllRequest) returns (GetAllResponse);
}
```

Se você salvar seu projeto com essas alterações, o destino da compilação gRPC será executado em segundo plano e gerará todos os tipos de mensagem Protobuf e uma classe base que você pode herdar para implementar o serviço.

Abra a `Services/GreeterService.cs` classe e exclua o código de exemplo. Agora você pode adicionar a implementação do serviço de portfólio. A classe base gerada estará no `Protos` namespace e será gerada como uma classe aninhada. gRPC cria uma classe estática com o mesmo nome que o serviço no `.proto` arquivo e, em seguida, uma classe base com o sufixo `Base` dentro dessa classe estática, portanto, o identificador completo para o tipo `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`base é.

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

A classe base declara `virtual` métodos para `Get` e `GetAll` que podem ser substituídos para implementar o serviço. Os métodos são `virtual` em vez `abstract` de que, se você não implementá-los, o serviço poderá retornar `Unimplemented` um código de status gRPC explícito, assim como `NotImplementedException` você pode C# lançar um código regular.

A assinatura para todos os métodos de serviço unário gRPC no ASP.NET Core é consistente. Há dois parâmetros: o primeiro é o tipo de mensagem declarado no `.proto` arquivo e o segundo é um `ServerCallContext` `HttpContext` que funciona de forma semelhante ao de ASP.NET Core. Na verdade, há um método de extensão chamado `GetHttpContext` `ServerCallContext` na classe que você pode usar para obter o subjacente `HttpContext`, embora você não precise usá-lo com frequência. Vamos examinar `ServerCallContext` mais adiante neste capítulo e também no capítulo que aborda a autenticação.

O tipo de retorno do método é `Task<T>` um `T` em que é o tipo de mensagem de resposta. Todos os métodos de serviço gRPC são assíncronos.

## <a name="migrate-the-portfoliodata-library-to-net-core"></a>Migrar a biblioteca PortfolioData para o .NET Core

Neste ponto, o projeto precisa do repositório de portfólio e dos modelos contidos na `TraderSys.PortfolioData` biblioteca de classes na solução do WCF. A maneira mais fácil de trazê-los é criar uma nova biblioteca de classes usando a caixa de diálogo **novo projeto** do Visual Studio com o modelo *biblioteca de classes (.net Standard)* ou na linha de comando usando o CLI do .NET Core, executando os seguintes comandos do diretório que contém o `TraderSys.sln` arquivo.

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

Depois que a biblioteca tiver sido criada e adicionada à solução, exclua o `Class1.cs` arquivo gerado e copie os arquivos da biblioteca da solução WCF para a pasta da nova biblioteca de classes, mantendo a estrutura de pastas.

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

Os arquivos de projeto do .net modernos `.cs` incluem automaticamente todos os arquivos no ou em seu próprio diretório, portanto, não é necessário adicioná-los explicitamente ao projeto. A única etapa `DataContract` restante é remover os atributos e `DataMember` das `Portfolio` classes e para `PortfolioItem` que eles sejam classes simples e C# antigas.

```csharp
public class Portfolio
{
    public int Id { get; set; }
    public Guid TraderId { get; set; }
    public List<PortfolioItem> Items { get; set; }
}

public class PortfolioItem
{
    public int Id { get; set; }
    public int ShareId { get; set; }
    public int Holding { get; set; }
    public decimal Cost { get; set; }
}
```

## <a name="use-aspnet-core-dependency-injection"></a>Usar ASP.NET Core injeção de dependência

Agora você pode adicionar uma referência a essa biblioteca para o projeto de aplicativo gRPC e consumir `PortfolioRepository` a classe usando a injeção de dependência na implementação do serviço gRPC. No aplicativo WCF, a injeção de dependência foi fornecida pelo contêiner Autofac IoC. ASP.NET Core tem injeção de dependência inclusas em; o repositório pode ser registrado no `ConfigureServices` método `Startup` na classe.

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Register the repository class as a scoped service (instance per request)
        services.AddScoped<IPortfolioRepository, PortfolioRepository>();

        services.AddGrpc();
    }

    // ...
}
```

A `IPortfolioRepository` implementação agora pode ser especificada como um parâmetro `PortfolioService` de Construtor na classe, da seguinte maneira:

```csharp
public class PortfolioService : Protos.Portfolios.PortfoliosBase
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }
}
```

## <a name="implement-the-grpc-service"></a>Implementar o serviço gRPC

Agora que você declarou suas mensagens e seu serviço no `portfolios.proto` arquivo, precisará implementar os métodos de serviço `PortfolioService` na classe que herda da classe gerada `Portfolios.PortfoliosBase` pelo gRPC. Os métodos são declarados como `virtual` na classe base. Se você não substituí-los, eles retornarão um código de status gRPC "não implementado" por padrão.

Comece implementando o `Get` método. A substituição padrão é semelhante ao exemplo a seguir:

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

O primeiro problema é `request.TraderId` uma cadeia de caracteres, e o serviço requer um. `Guid` Embora o formato esperado para a cadeia de caracteres seja `UUID`a, o código precisa lidar com a possibilidade de um chamador ter enviado um valor inválido e responder adequadamente. O serviço pode responder com erros lançando um `RpcException`e usar o código de `InvalidArgument` status padrão para expressar o problema.

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    return base.Get(request, context);
}
```

Uma vez que há um `Guid` valor adequado `traderId`para, o repositório pode ser usado para recuperar o portfólio e retorná-lo para o cliente.

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a>Mapear modelos internos para mensagens gRPC

O código anterior não funciona realmente porque o repositório está retornando seu próprio modelo `Portfolio`poco, mas gRPC precisa *de sua* própria `Portfolio`mensagem Protobuf. Assim como o mapeamento de tipos de Entity Framework para tipos de transferência de dados, a melhor solução é fornecer conversão entre os dois. Um bom lugar para colocar o código para isso é na classe gerada pelo Protobuf, que é declarada como `partial` uma classe para que possa ser estendida.

```csharp
namespace TraderSys.Portfolios.Protos
{
    public partial class PortfolioItem
    {
        public static PortfolioItem FromRepositoryModel(PortfolioData.Models.PortfolioItem source)
        {
            if (source is null) return null;

            return new PortfolioItem
            {
                Id = source.Id,
                ShareId = source.ShareId,
                Holding = source.Holding,
                CostCents = (int)(source.Cost * 100)
            };
        }
    }

    public partial class Portfolio
    {
        public static Portfolio FromRepositoryModel(PortfolioData.Models.Portfolio source)
        {
            if (source is null) return null;

            var target = new Portfolio
            {
                Id = source.Id,
                TraderId = source.TraderId.ToString(),
            };

            target.Items.AddRange(source.Items.Select(PortfolioItem.FromRepositoryModel));

            return target;
        }
    }
}
```

> [!NOTE]
> Você pode usar uma biblioteca como [o AutoMapper](https://automapper.org/) para lidar com essa conversão de classes de modelo internas para tipos Protobuf, contanto que configure as conversões de tipo de nível `string` inferior como ou `decimal` / `Guid` /e o mapeamento de lista. `double`

Com o código de conversão em vigor, `Get` a implementação do método pode ser concluída.

```csharp
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}

```

A implementação do `GetAll` método é semelhante. Observe que os `repeated` campos em mensagens Protobuf são gerados como `readonly` Propriedades do tipo `RepeatedField<T>`, portanto, você precisa adicionar itens a eles usando o `AddRange` método, como no exemplo a seguir:

```csharp
public override async Task<GetAllResponse> GetAll(GetAllRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolios = await _repository.GetAllAsync(traderId);

    var response = new GetAllResponse();
    response.Portfolios.AddRange(portfolios.Select(Portfolio.FromRepositoryModel));

    return response;
}
```

Tendo migrado com êxito o serviço de solicitação-resposta do WCF para gRPC, vamos examinar a criação de um cliente para ele `.proto` a partir do arquivo.

## <a name="generate-client-code"></a>Gerar código de cliente

Crie um .NET Standard biblioteca de classes na mesma solução para conter o cliente. Isso é basicamente um exemplo de criação de código de cliente, mas você pode empacotar uma biblioteca desse tipo usando o NuGet e distribuí-la em um repositório interno para que outras equipes do .NET consumam. Vá em frente e adicione uma nova biblioteca de classes `TraderSys.Portfolios.Client` .net Standard chamada à solução e exclua o `Class1.cs` arquivo.

> [!CAUTION]
> O pacote NuGet do [.net. Client do Grpc](https://www.nuget.org/packages/Grpc.Net.Client) requer o .net Core 3,0 (ou outro tempo de execução compatível com 2,1 .net Standard). As versões anteriores do .NET Framework e do .NET Core são compatíveis com o pacote NuGet [Grpc. Core](https://www.nuget.org/packages/Grpc.Core) .

No Visual Studio 2019, você pode adicionar referências a serviços gRPCs de forma semelhante à maneira como você adicionaria referências de serviço a projetos WCF em versões anteriores do Visual Studio. Referências de serviço e serviços conectados são todos gerenciados na mesma interface do usuário agora, que você pode acessar clicando com o botão direito do `TraderSys.Portfolios.Client` mouse no nó **dependências** no projeto no Gerenciador de soluções e selecionando **Adicionar serviço conectado**. Na janela de ferramentas exibida, selecione a seção **referências de serviço** e clique em **Adicionar nova referência de serviço gRPC**.

![A interface do usuário dos serviços conectados no Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

Navegue até o `portfolios.proto` arquivo `TraderSys.Portfolios` no projeto, deixe o **tipo de classe a ser gerado** como **cliente**e clique em **OK**.

![A caixa de diálogo Adicionar nova referência de serviço gRPC no Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> Observe que essa caixa de diálogo também fornece um campo URL. Se sua organização mantém um diretório de arquivos acessível pela `.proto` Web, você pode criar clientes apenas definindo esse endereço de URL.

Ao usar o recurso **Adicionar serviço conectado** do Visual Studio, `portfolios.proto` o arquivo é adicionado ao projeto de biblioteca de classes como um *arquivo vinculado*, em vez de copiado, portanto, as alterações no arquivo no projeto de serviço serão aplicadas automaticamente no projeto de cliente. O `<Protobuf>` elemento`csproj` no arquivo tem a seguinte aparência:

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

### <a name="use-the-portfolios-service-from-a-client-application"></a>Usar o serviço de portfólios de um aplicativo cliente

O código a seguir é um breve exemplo do uso do cliente gerado em um aplicativo de console. Uma exploração mais detalhada do código do cliente gRPC está no final deste capítulo.

```csharp
public class Program
{
    public async Task Main(string[] args)
    {
        GetResponse response;

        using (var channel = GrpcChannel.ForAddress("https://localhost:5001"))
        {
            var client = new Protos.Portfolios.PortfoliosClient(channel);

            response = await client.GetAsync(new GetRequest
            {
                TraderId = args[0],
                PortfolioId = int.Parse(args[1])
            });
        }

        foreach (var item in response.Portfolio.Items)
        {
            Console.WriteLine($"Holding {item.Holding} of Share ID {item.ShareId}.");
        }
    }
}
```

Agora, você migrou um aplicativo WCF básico para um serviço ASP.NET Core gRPC e criou um cliente para consumir o serviço de um aplicativo .NET. A próxima seção abordará os serviços "duplex" mais envolvidos.

>[!div class="step-by-step"]
>[Anterior](create-project.md)
>[Próximo](migrate-duplex-services.md)
