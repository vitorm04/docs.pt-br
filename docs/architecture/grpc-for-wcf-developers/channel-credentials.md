---
title: Credenciais do canal-gRPC para desenvolvedores do WCF
description: Como implementar e usar as credenciais de canal do gRPC no ASP.NET Core 3,0.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 61305ee47a2c09a0b2a0fd866beb9b7c102ffeaa
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184578"
---
# <a name="channel-credentials"></a><span data-ttu-id="760d1-103">Credenciais do canal</span><span class="sxs-lookup"><span data-stu-id="760d1-103">Channel credentials</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="760d1-104">Como o nome indica, as credenciais de canal são anexadas ao canal gRPC subjacente.</span><span class="sxs-lookup"><span data-stu-id="760d1-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="760d1-105">A forma padrão de credenciais de canal usa a autenticação de certificado de cliente, em que o cliente fornece um certificado TLS quando está fazendo a conexão, que é verificada pelo servidor antes de permitir que qualquer chamada seja feita.</span><span class="sxs-lookup"><span data-stu-id="760d1-105">The standard form of channel credentials uses Client Certificate authentication, where the client provides a TLS certificate when it's making the connection, which is verified by the server before allowing any calls to be made.</span></span>

<span data-ttu-id="760d1-106">As credenciais de canal podem ser combinadas com credenciais de chamada para fornecer segurança abrangente para um serviço gRPC.</span><span class="sxs-lookup"><span data-stu-id="760d1-106">Channel credentials can be combined with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="760d1-107">As credenciais do canal provam que o aplicativo cliente tem permissão para acessar o serviço e as credenciais de chamada fornecem informações sobre a pessoa usando o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="760d1-107">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person using the client application.</span></span>

<span data-ttu-id="760d1-108">A autenticação de certificado de cliente funciona para gRPC da mesma maneira que funciona para ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="760d1-108">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="760d1-109">O processo de configuração será resumido aqui, mas mais informações estarão disponíveis no artigo [Configurar a autenticação de certificado no ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) .</span><span class="sxs-lookup"><span data-stu-id="760d1-109">The configuration process will be summarized here, but more information is available in the [Configure certificate authentication in ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) article.</span></span>

<span data-ttu-id="760d1-110">Para fins de desenvolvimento, você pode usar um certificado autoassinado, mas para produção, você deve usar um certificado HTTPS adequado assinado por uma autoridade confiável.</span><span class="sxs-lookup"><span data-stu-id="760d1-110">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="adding-certificate-authentication-to-the-server"></a><span data-ttu-id="760d1-111">Adicionando autenticação de certificado ao servidor</span><span class="sxs-lookup"><span data-stu-id="760d1-111">Adding certificate authentication to the server</span></span>

<span data-ttu-id="760d1-112">Você precisa configurar a autenticação de certificado no nível do host, por exemplo, no servidor Kestrel e no pipeline ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="760d1-112">You need to configure certificate authentication both at the host level, for example on the Kestrel server, and in the ASP.NET Core pipeline.</span></span>

### <a name="configuring-certificate-validation-on-kestrel"></a><span data-ttu-id="760d1-113">Configurando a validação de certificado no Kestrel</span><span class="sxs-lookup"><span data-stu-id="760d1-113">Configuring certificate validation on Kestrel</span></span>

<span data-ttu-id="760d1-114">Você pode configurar Kestrel (o servidor HTTP ASP.NET Core) para exigir um certificado de cliente e, opcionalmente, realizar alguma validação do certificado fornecido antes de aceitar conexões de entrada.</span><span class="sxs-lookup"><span data-stu-id="760d1-114">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate before accepting incoming connections.</span></span> <span data-ttu-id="760d1-115">Essa configuração é feita no `CreateWebHostBuilder` método `Program` da classe, em vez de em `Startup`.</span><span class="sxs-lookup"><span data-stu-id="760d1-115">This configuration is done in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="760d1-116">A `ClientCertificateMode.RequireCertificate` configuração fará com que o Kestrel rejeite imediatamente qualquer solicitação de conexão que não forneça um certificado de cliente, mas não validará o certificado.</span><span class="sxs-lookup"><span data-stu-id="760d1-116">The `ClientCertificateMode.RequireCertificate` setting will cause Kestrel to immediately reject any connection request that doesn't provide a client certificate, but it won't validate the certificate.</span></span> <span data-ttu-id="760d1-117">A adição `ClientCertificateValidation` do retorno de chamada permite que o Kestrel valide o certificado do cliente (nesse caso, garantindo que ele foi emitido pela mesma *autoridade de certificação* que o certificado do servidor) no ponto em que a conexão é feita, antes da ASP.NET Core o pipeline está envolvido.</span><span class="sxs-lookup"><span data-stu-id="760d1-117">Adding the `ClientCertificateValidation` callback enables Kestrel to validate the client certificate (in this case, ensuring that it was issued by the same *Certificate Authority* as the server certificate) at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span>

### <a name="adding-aspnet-core-certificate-authentication"></a><span data-ttu-id="760d1-118">Adicionando ASP.NET Core autenticação de certificado</span><span class="sxs-lookup"><span data-stu-id="760d1-118">Adding ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="760d1-119">A autenticação de certificado é fornecida pelo pacote NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) .</span><span class="sxs-lookup"><span data-stu-id="760d1-119">Certificate authentication is provided by the [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package.</span></span>

<span data-ttu-id="760d1-120">Adicione o serviço de autenticação de certificado `ConfigureServices` no método e adicione autenticação e autorização ao pipeline de ASP.NET Core `Configure` no método.</span><span class="sxs-lookup"><span data-stu-id="760d1-120">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="providing-channel-credentials-in-the-client-application"></a><span data-ttu-id="760d1-121">Fornecendo credenciais de canal no aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="760d1-121">Providing channel credentials in the client application</span></span>

<span data-ttu-id="760d1-122">Com o `Grpc.Net.Client` pacote, os certificados são configurados em uma <xref:System.Net.Http.HttpClient> instância do `GrpcChannel` que é fornecida para o usado para a conexão.</span><span class="sxs-lookup"><span data-stu-id="760d1-122">With the `Grpc.Net.Client` package, certificates are configured on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combining-channelcredentials-and-callcredentials"></a><span data-ttu-id="760d1-123">Combinando ChannelCredentials e CallCredentials</span><span class="sxs-lookup"><span data-stu-id="760d1-123">Combining ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="760d1-124">Você pode configurar o servidor para usar a autenticação de certificado e de token aplicando as alterações de certificado ao servidor Kestrel e usando o middleware portador JWT no ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="760d1-124">You can configure your server to use both certificate and token authentication by applying the certificate changes to the Kestrel server and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="760d1-125">Para fornecer ChannelCredentials e CallCredentials no cliente, use o `ChannelCredentials.Create` método para aplicar as credenciais de chamada.</span><span class="sxs-lookup"><span data-stu-id="760d1-125">To provide both ChannelCredentials and CallCredentials on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="760d1-126">A autenticação de certificado ainda precisa ser aplicada usando <xref:System.Net.Http.HttpClient> a instância: se você passar quaisquer argumentos para `SslCredentials` o construtor, o código do cliente interno lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="760d1-126">Certificate authentication still needs to be applied using the <xref:System.Net.Http.HttpClient> instance: if you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="760d1-127">O `SslCredentials` parâmetro só é incluído `Grpc.Net.Client` no método do `Create` pacote para manter a compatibilidade com o `Grpc.Core` pacote.</span><span class="sxs-lookup"><span data-stu-id="760d1-127">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="760d1-128">Você pode usar o `ChannelCredentials.Create` método para um cliente sem autenticação de certificado, como uma maneira útil de passar credenciais de token com cada chamada feita no canal.</span><span class="sxs-lookup"><span data-stu-id="760d1-128">You can use the `ChannelCredentials.Create` method for a client without certificate authentication, as a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="760d1-129">Uma versão do [aplicativo de exemplo FullStockTicker gRPC com autenticação de certificado adicionada](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) está no github.</span><span class="sxs-lookup"><span data-stu-id="760d1-129">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="760d1-130">[Anterior](call-credentials.md)
>[Próximo](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="760d1-130">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
