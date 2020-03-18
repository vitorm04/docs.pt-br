---
title: Credenciais de canal - gRPC para Desenvolvedores WCF
description: Como implementar e usar credenciais de canal gRPC em ASP.NET Core 3.0.
ms.date: 09/02/2019
ms.openlocfilehash: 9ebe0aecb517e4cc2fe280632c4ecb593da9871c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148199"
---
# <a name="channel-credentials"></a>Credenciais de canal

Como o nome indica, as credenciais do canal são anexadas ao canal gRPC subjacente. A forma padrão de credenciais de canal usa autenticação de certificado de cliente. Nesse processo, o cliente fornece um certificado TLS quando está fazendo a conexão e, em seguida, o servidor verifica isso antes de permitir que quaisquer chamadas sejam feitas.

Você pode combinar credenciais de canal com credenciais de chamada para fornecer segurança abrangente para um serviço gRPC. As credenciais do canal comprovam que o aplicativo cliente pode acessar o serviço, e as credenciais de chamada fornecem informações sobre a pessoa que está usando o aplicativo cliente.

A autenticação do certificado cliente funciona para o gRPC da mesma forma que funciona para ASP.NET Core. Para obter mais informações, consulte [Configurar autenticação de certificado no ASP.NET Core](/aspnet/core/security/authentication/certauth).

Para fins de desenvolvimento, você pode usar um certificado auto-assinado, mas para a produção você deve usar um certificado HTTPS adequado assinado por uma autoridade confiável.

## <a name="add-certificate-authentication-to-the-server"></a>Adicionar autenticação de certificado ao servidor

Configure a autenticação do certificado tanto no nível host (por exemplo, no servidor Kestrel) quanto no pipeline ASP.NET Core.

### <a name="configure-certificate-validation-on-kestrel"></a>Configure validação de certificado no Kestrel

Você pode configurar o Kestrel (o servidor ASP.NET Core HTTP) para exigir um certificado de cliente e, opcionalmente, realizar alguma validação do certificado fornecido, antes de aceitar conexões recebidas. Você faz isso `CreateWebHostBuilder` no `Program` método da classe, em vez de em `Startup`.

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

A `ClientCertificateMode.RequireCertificate` configuração faz com que a Kestrel rejeite imediatamente qualquer solicitação de conexão que não forneça um certificado de cliente, mas essa configuração por si só não validará um certificado fornecido. Adicione `ClientCertificateValidation` o retorno de chamada para permitir que o Kestrel valide o certificado do cliente no momento em que a conexão é feita, antes que o pipeline ASP.NET Core seja ativado. (Neste caso, o retorno de chamada garante que ele foi emitido pela mesma *Autoridade de Certificado* que o certificado do servidor.)

### <a name="add-aspnet-core-certificate-authentication"></a>Adicionar autenticação de certificado ASP.NET Core

O pacote [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet fornece autenticação de certificado.

Adicione o serviço de `ConfigureServices` autenticação de certificado no método e adicione `Configure` autenticação e autorização ao ASP.NET pipeline Core no método.

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

## <a name="provide-channel-credentials-in-the-client-application"></a>Fornecer credenciais de canal no aplicativo cliente

Com `Grpc.Net.Client` o pacote, você configura <xref:System.Net.Http.HttpClient> certificados em uma `GrpcChannel` instância fornecida ao usado para a conexão.

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

## <a name="combine-channelcredentials-and-callcredentials"></a>Combine credenciais de canal e credenciais de chamada

Você pode configurar seu servidor para usar autenticação de certificado e token. Faça isso aplicando as alterações de certificado no servidor Kestrel e usando o middleware do portador JWT no ASP.NET Core.

Para fornecer `ChannelCredentials` `CallCredentials` tanto e sobre `ChannelCredentials.Create` o cliente, use o método para aplicar as credenciais de chamada. Você ainda precisa aplicar a autenticação do certificado usando a <xref:System.Net.Http.HttpClient> instância. Se você passar quaisquer `SslCredentials` argumentos para o construtor, o código interno do cliente lança uma exceção. O `SslCredentials` parâmetro só está `Grpc.Net.Client` incluído no `Create` método do pacote `Grpc.Core` para manter a compatibilidade com o pacote.

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
> Você pode `ChannelCredentials.Create` usar o método para um cliente sem autenticação de certificado. Esta é uma maneira útil de passar credenciais de token a cada chamada feita no canal.

Uma versão do [aplicativo gRPC da amostra FullStockTicker com autenticação de certificado adicionada](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) está no GitHub.

>[!div class="step-by-step"]
>[Próximo](call-credentials.md)
>[anterior](encryption.md)
