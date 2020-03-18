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
# <a name="channel-credentials"></a><span data-ttu-id="640f2-103">Credenciais de canal</span><span class="sxs-lookup"><span data-stu-id="640f2-103">Channel credentials</span></span>

<span data-ttu-id="640f2-104">Como o nome indica, as credenciais do canal são anexadas ao canal gRPC subjacente.</span><span class="sxs-lookup"><span data-stu-id="640f2-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="640f2-105">A forma padrão de credenciais de canal usa autenticação de certificado de cliente.</span><span class="sxs-lookup"><span data-stu-id="640f2-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="640f2-106">Nesse processo, o cliente fornece um certificado TLS quando está fazendo a conexão e, em seguida, o servidor verifica isso antes de permitir que quaisquer chamadas sejam feitas.</span><span class="sxs-lookup"><span data-stu-id="640f2-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this before allowing any calls to be made.</span></span>

<span data-ttu-id="640f2-107">Você pode combinar credenciais de canal com credenciais de chamada para fornecer segurança abrangente para um serviço gRPC.</span><span class="sxs-lookup"><span data-stu-id="640f2-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="640f2-108">As credenciais do canal comprovam que o aplicativo cliente pode acessar o serviço, e as credenciais de chamada fornecem informações sobre a pessoa que está usando o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="640f2-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="640f2-109">A autenticação do certificado cliente funciona para o gRPC da mesma forma que funciona para ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="640f2-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="640f2-110">Para obter mais informações, consulte [Configurar autenticação de certificado no ASP.NET Core](/aspnet/core/security/authentication/certauth).</span><span class="sxs-lookup"><span data-stu-id="640f2-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="640f2-111">Para fins de desenvolvimento, você pode usar um certificado auto-assinado, mas para a produção você deve usar um certificado HTTPS adequado assinado por uma autoridade confiável.</span><span class="sxs-lookup"><span data-stu-id="640f2-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="640f2-112">Adicionar autenticação de certificado ao servidor</span><span class="sxs-lookup"><span data-stu-id="640f2-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="640f2-113">Configure a autenticação do certificado tanto no nível host (por exemplo, no servidor Kestrel) quanto no pipeline ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="640f2-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="640f2-114">Configure validação de certificado no Kestrel</span><span class="sxs-lookup"><span data-stu-id="640f2-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="640f2-115">Você pode configurar o Kestrel (o servidor ASP.NET Core HTTP) para exigir um certificado de cliente e, opcionalmente, realizar alguma validação do certificado fornecido, antes de aceitar conexões recebidas.</span><span class="sxs-lookup"><span data-stu-id="640f2-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="640f2-116">Você faz isso `CreateWebHostBuilder` no `Program` método da classe, em vez de em `Startup`.</span><span class="sxs-lookup"><span data-stu-id="640f2-116">You do this in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="640f2-117">A `ClientCertificateMode.RequireCertificate` configuração faz com que a Kestrel rejeite imediatamente qualquer solicitação de conexão que não forneça um certificado de cliente, mas essa configuração por si só não validará um certificado fornecido.</span><span class="sxs-lookup"><span data-stu-id="640f2-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="640f2-118">Adicione `ClientCertificateValidation` o retorno de chamada para permitir que o Kestrel valide o certificado do cliente no momento em que a conexão é feita, antes que o pipeline ASP.NET Core seja ativado.</span><span class="sxs-lookup"><span data-stu-id="640f2-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="640f2-119">(Neste caso, o retorno de chamada garante que ele foi emitido pela mesma *Autoridade de Certificado* que o certificado do servidor.)</span><span class="sxs-lookup"><span data-stu-id="640f2-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span>

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="640f2-120">Adicionar autenticação de certificado ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="640f2-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="640f2-121">O pacote [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet fornece autenticação de certificado.</span><span class="sxs-lookup"><span data-stu-id="640f2-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="640f2-122">Adicione o serviço de `ConfigureServices` autenticação de certificado no método e adicione `Configure` autenticação e autorização ao ASP.NET pipeline Core no método.</span><span class="sxs-lookup"><span data-stu-id="640f2-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="640f2-123">Fornecer credenciais de canal no aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="640f2-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="640f2-124">Com `Grpc.Net.Client` o pacote, você configura <xref:System.Net.Http.HttpClient> certificados em uma `GrpcChannel` instância fornecida ao usado para a conexão.</span><span class="sxs-lookup"><span data-stu-id="640f2-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="640f2-125">Combine credenciais de canal e credenciais de chamada</span><span class="sxs-lookup"><span data-stu-id="640f2-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="640f2-126">Você pode configurar seu servidor para usar autenticação de certificado e token.</span><span class="sxs-lookup"><span data-stu-id="640f2-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="640f2-127">Faça isso aplicando as alterações de certificado no servidor Kestrel e usando o middleware do portador JWT no ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="640f2-127">Do this by applying the certificate changes to the Kestrel server, and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="640f2-128">Para fornecer `ChannelCredentials` `CallCredentials` tanto e sobre `ChannelCredentials.Create` o cliente, use o método para aplicar as credenciais de chamada.</span><span class="sxs-lookup"><span data-stu-id="640f2-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="640f2-129">Você ainda precisa aplicar a autenticação do certificado usando a <xref:System.Net.Http.HttpClient> instância.</span><span class="sxs-lookup"><span data-stu-id="640f2-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="640f2-130">Se você passar quaisquer `SslCredentials` argumentos para o construtor, o código interno do cliente lança uma exceção.</span><span class="sxs-lookup"><span data-stu-id="640f2-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="640f2-131">O `SslCredentials` parâmetro só está `Grpc.Net.Client` incluído no `Create` método do pacote `Grpc.Core` para manter a compatibilidade com o pacote.</span><span class="sxs-lookup"><span data-stu-id="640f2-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="640f2-132">Você pode `ChannelCredentials.Create` usar o método para um cliente sem autenticação de certificado.</span><span class="sxs-lookup"><span data-stu-id="640f2-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="640f2-133">Esta é uma maneira útil de passar credenciais de token a cada chamada feita no canal.</span><span class="sxs-lookup"><span data-stu-id="640f2-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="640f2-134">Uma versão do [aplicativo gRPC da amostra FullStockTicker com autenticação de certificado adicionada](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) está no GitHub.</span><span class="sxs-lookup"><span data-stu-id="640f2-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="640f2-135">[Próximo](call-credentials.md)
>[anterior](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="640f2-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
