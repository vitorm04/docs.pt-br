---
title: Credenciais do canal-gRPC para desenvolvedores do WCF
description: Como implementar e usar as credenciais de canal do gRPC no ASP.NET Core 3,0.
ms.date: 09/02/2019
ms.openlocfilehash: 133de2c732e72844f249f11bfe22b5980b828b89
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711498"
---
# <a name="channel-credentials"></a><span data-ttu-id="6a04e-103">Credenciais de canal</span><span class="sxs-lookup"><span data-stu-id="6a04e-103">Channel credentials</span></span>

<span data-ttu-id="6a04e-104">Como o nome indica, as credenciais de canal são anexadas ao canal gRPC subjacente.</span><span class="sxs-lookup"><span data-stu-id="6a04e-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="6a04e-105">A forma padrão de credenciais de canal usa a autenticação de certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="6a04e-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="6a04e-106">Nesse processo, o cliente fornece um certificado TLS quando está fazendo a conexão e, em seguida, o servidor verifica isso antes de permitir que qualquer chamada seja feita.</span><span class="sxs-lookup"><span data-stu-id="6a04e-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this before allowing any calls to be made.</span></span>

<span data-ttu-id="6a04e-107">Você pode combinar credenciais de canal com credenciais de chamada para fornecer segurança abrangente para um serviço gRPC.</span><span class="sxs-lookup"><span data-stu-id="6a04e-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="6a04e-108">As credenciais do canal provam que o aplicativo cliente tem permissão para acessar o serviço e as credenciais de chamada fornecem informações sobre a pessoa que está usando o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="6a04e-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="6a04e-109">A autenticação de certificado de cliente funciona para gRPC da mesma maneira que funciona para ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6a04e-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="6a04e-110">Para obter mais informações, consulte [Configurar a autenticação de certificado no ASP.NET Core](/aspnet/core/security/authentication/certauth).</span><span class="sxs-lookup"><span data-stu-id="6a04e-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="6a04e-111">Para fins de desenvolvimento, você pode usar um certificado autoassinado, mas para produção, você deve usar um certificado HTTPS adequado assinado por uma autoridade confiável.</span><span class="sxs-lookup"><span data-stu-id="6a04e-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="6a04e-112">Adicionar autenticação de certificado ao servidor</span><span class="sxs-lookup"><span data-stu-id="6a04e-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="6a04e-113">Configure a autenticação de certificado no nível do host (por exemplo, no servidor Kestrel) e no pipeline ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6a04e-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="6a04e-114">Configurar a validação de certificado no Kestrel</span><span class="sxs-lookup"><span data-stu-id="6a04e-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="6a04e-115">Você pode configurar Kestrel (o servidor HTTP ASP.NET Core) para exigir um certificado de cliente e, opcionalmente, realizar alguma validação do certificado fornecido, antes de aceitar conexões de entrada.</span><span class="sxs-lookup"><span data-stu-id="6a04e-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="6a04e-116">Você faz isso no método `CreateWebHostBuilder` da classe `Program`, em vez de no `Startup`.</span><span class="sxs-lookup"><span data-stu-id="6a04e-116">You do this in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="6a04e-117">A configuração `ClientCertificateMode.RequireCertificate` faz com que o Kestrel rejeite imediatamente qualquer solicitação de conexão que não forneça um certificado de cliente, mas essa configuração por si só não validará um certificado fornecido.</span><span class="sxs-lookup"><span data-stu-id="6a04e-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="6a04e-118">Adicione o `ClientCertificateValidation` retorno de chamada para permitir que o Kestrel valide o certificado do cliente no ponto em que a conexão é feita, antes que o pipeline de ASP.NET Core seja envolvido.</span><span class="sxs-lookup"><span data-stu-id="6a04e-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="6a04e-119">(Nesse caso, o retorno de chamada garante que ele foi emitido pela mesma *autoridade de certificação* que o certificado do servidor.)</span><span class="sxs-lookup"><span data-stu-id="6a04e-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span> 

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="6a04e-120">Adicionar ASP.NET Core autenticação de certificado</span><span class="sxs-lookup"><span data-stu-id="6a04e-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="6a04e-121">O pacote NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) fornece autenticação de certificado.</span><span class="sxs-lookup"><span data-stu-id="6a04e-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="6a04e-122">Adicione o serviço de autenticação de certificado no método `ConfigureServices` e adicione autenticação e autorização ao pipeline de ASP.NET Core no método `Configure`.</span><span class="sxs-lookup"><span data-stu-id="6a04e-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="6a04e-123">Fornecer credenciais de canal no aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="6a04e-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="6a04e-124">Com o pacote `Grpc.Net.Client`, você configura certificados em uma instância <xref:System.Net.Http.HttpClient> que é fornecida para o `GrpcChannel` usado para a conexão.</span><span class="sxs-lookup"><span data-stu-id="6a04e-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="6a04e-125">Combinar ChannelCredentials e CallCredentials</span><span class="sxs-lookup"><span data-stu-id="6a04e-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="6a04e-126">Você pode configurar o servidor para usar a autenticação de certificado e de token.</span><span class="sxs-lookup"><span data-stu-id="6a04e-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="6a04e-127">Faça isso aplicando as alterações de certificado ao servidor Kestrel e usando o middleware portador JWT no ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6a04e-127">Do this by applying the certificate changes to the Kestrel server, and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="6a04e-128">Para fornecer `ChannelCredentials` e `CallCredentials` no cliente, use o método `ChannelCredentials.Create` para aplicar as credenciais de chamada.</span><span class="sxs-lookup"><span data-stu-id="6a04e-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="6a04e-129">Você ainda precisa aplicar a autenticação de certificado usando a instância de <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="6a04e-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="6a04e-130">Se você passar quaisquer argumentos para o construtor de `SslCredentials`, o código de cliente interno lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="6a04e-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="6a04e-131">O parâmetro `SslCredentials` só é incluído no método `Create` do pacote `Grpc.Net.Client` para manter a compatibilidade com o pacote `Grpc.Core`.</span><span class="sxs-lookup"><span data-stu-id="6a04e-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="6a04e-132">Você pode usar o método `ChannelCredentials.Create` para um cliente sem autenticação de certificado.</span><span class="sxs-lookup"><span data-stu-id="6a04e-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="6a04e-133">Essa é uma maneira útil de passar credenciais de token com cada chamada feita no canal.</span><span class="sxs-lookup"><span data-stu-id="6a04e-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="6a04e-134">Uma versão do [aplicativo de exemplo FullStockTicker gRPC com autenticação de certificado adicionada](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) está no github.</span><span class="sxs-lookup"><span data-stu-id="6a04e-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6a04e-135">[Anterior](call-credentials.md)
>[Próximo](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="6a04e-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
