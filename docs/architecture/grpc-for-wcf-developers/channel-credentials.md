---
title: Credenciais do canal-gRPC para desenvolvedores do WCF
description: Como implementar e usar as credenciais de canal do gRPC no ASP.NET Core 3,0.
ms.date: 09/02/2019
ms.openlocfilehash: b424db49337a2dc6e3d0245d36349e3f408cdf6c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967955"
---
# <a name="channel-credentials"></a>Credenciais de canal

Como o nome indica, as credenciais de canal são anexadas ao canal gRPC subjacente. A forma padrão de credenciais de canal usa a autenticação de certificado de cliente, em que o cliente fornece um certificado TLS quando está fazendo a conexão, que é verificada pelo servidor antes de permitir que qualquer chamada seja feita.

As credenciais de canal podem ser combinadas com credenciais de chamada para fornecer segurança abrangente para um serviço gRPC. As credenciais do canal provam que o aplicativo cliente tem permissão para acessar o serviço e as credenciais de chamada fornecem informações sobre a pessoa usando o aplicativo cliente.

A autenticação de certificado de cliente funciona para gRPC da mesma maneira que funciona para ASP.NET Core. O processo de configuração será resumido aqui, mas mais informações estarão disponíveis no artigo [Configurar a autenticação de certificado no ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) .

Para fins de desenvolvimento, você pode usar um certificado autoassinado, mas para produção, você deve usar um certificado HTTPS adequado assinado por uma autoridade confiável.

## <a name="adding-certificate-authentication-to-the-server"></a>Adicionando autenticação de certificado ao servidor

Você precisa configurar a autenticação de certificado no nível do host, por exemplo, no servidor Kestrel e no pipeline ASP.NET Core.

### <a name="configuring-certificate-validation-on-kestrel"></a>Configurando a validação de certificado no Kestrel

Você pode configurar Kestrel (o servidor HTTP ASP.NET Core) para exigir um certificado de cliente e, opcionalmente, realizar alguma validação do certificado fornecido antes de aceitar conexões de entrada. Essa configuração é feita no método `CreateWebHostBuilder` da classe `Program`, em vez de em `Startup`.

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            var serverCert = ObtainServerCertificate();
            webBuilder.UseStartup<Startup>()
                .ConfigureKestrel(kestrelServerOptions => {
                    kestrelServerOptions.ConfigureHttpsDefaults(opt =>
                    {
                        opt.ClientCertificateMode = ClientCertificateMode.RequireCertificate;

                        // Verify that client certificate was issued by same CA as server certificate
                        opt.ClientCertificateValidation = (certificate, chain, errors) =>
                            certificate.Issuer == serverCert.Issuer;
                    });
                });
        });

```

A configuração `ClientCertificateMode.RequireCertificate` fará com que o Kestrel rejeite imediatamente qualquer solicitação de conexão que não forneça um certificado de cliente, mas não validará o certificado. Adicionar o `ClientCertificateValidation` retorno de chamada permite que o Kestrel valide o certificado do cliente (nesse caso, garantindo que ele foi emitido pela mesma *autoridade de certificação* que o certificado do servidor) no ponto em que a conexão é feita, antes que o pipeline de ASP.NET Core seja envolvido.

### <a name="adding-aspnet-core-certificate-authentication"></a>Adicionando ASP.NET Core autenticação de certificado

A autenticação de certificado é fornecida pelo pacote NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) .

Adicione o serviço de autenticação de certificado no método `ConfigureServices` e adicione autenticação e autorização ao pipeline de ASP.NET Core no método `Configure`.

```csharp
public class Startup
{
    private readonly bool _isDevelopment;

    public Startup(IWebHostEnvironment env)
    {
        _isDevelopment = env.IsDevelopment();
    }

    public void ConfigureServices(IServiceCollection services)
    {
        services.AddAuthentication(CertificateAuthenticationDefaults.AuthenticationScheme)
            .AddCertificate(options =>
            {
                if (_isDevelopment)
                {
                    // DO NOT DO THIS IN PRODUCTION!
                    options.RevocationMode = X509RevocationMode.NoCheck;
                }
            });
        services.AddAuthorization();
        services.AddGrpc();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        app.UseRouting();

        app.UseAuthentication();
        app.UseAuthorization();

        app.UseEndpoints(endpoints => { endpoints.MapGrpcService<GreeterService>(); });
    }
}
```

## <a name="providing-channel-credentials-in-the-client-application"></a>Fornecendo credenciais de canal no aplicativo cliente

Com o pacote `Grpc.Net.Client`, os certificados são configurados em uma instância <xref:System.Net.Http.HttpClient> fornecida para o `GrpcChannel` usado para a conexão.

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        // Assume path to a client .pfx file and password are passed from command line
        // On Windows this would probably be a reference to the Certificate Store
        var cert = new X509Certificate2(args[0], args[1]);

        var handler = new HttpClientHandler();
        handler.ClientCertificates.Add(cert);
        var httpClient = new HttpClient(handler);

        var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
        {
            HttpClient = httpClient
        });

        var grpc = new Greeter.GreeterClient(channel);
        var response = await grpc.SayHelloAsync(new HelloRequest { Name = "Bob" });
        System.Console.WriteLine(response.Message);
    }
}
```

## <a name="combining-channelcredentials-and-callcredentials"></a>Combinando ChannelCredentials e CallCredentials

Você pode configurar o servidor para usar a autenticação de certificado e de token aplicando as alterações de certificado ao servidor Kestrel e usando o middleware portador JWT no ASP.NET Core.

Para fornecer ChannelCredentials e CallCredentials no cliente, use o método `ChannelCredentials.Create` para aplicar as credenciais de chamada. A autenticação de certificado ainda precisa ser aplicada usando a instância de <xref:System.Net.Http.HttpClient>: se você passar quaisquer argumentos para o construtor de `SslCredentials`, o código do cliente interno lançará uma exceção. O parâmetro `SslCredentials` só é incluído no método `Create` do pacote `Grpc.Net.Client` para manter a compatibilidade com o pacote `Grpc.Core`.

```csharp
var handler = new HttpClientHandler();
handler.ClientCertificates.Add(cert);

var httpClient = new HttpClient(handler);

var callCredentials = CallCredentials.FromInterceptor(((context, metadata) =>
    {
        metadata.Add("Authorization", $"Bearer {_token}");
    }));

var channelCredentials = ChannelCredentials.Create(new SslCredentials(), callCredentials);

var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
{
    HttpClient = httpClient,
    Credentials = channelCredentials
});

var grpc = new Portfolios.PortfoliosClient(channel);
```

> [!TIP]
> Você pode usar o método `ChannelCredentials.Create` para um cliente sem autenticação de certificado, como uma maneira útil de passar credenciais de token com cada chamada feita no canal.

Uma versão do [aplicativo de exemplo FullStockTicker gRPC com autenticação de certificado adicionada](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) está no github.

>[!div class="step-by-step"]
>[Anterior](call-credentials.md)
>[Próximo](encryption.md)
