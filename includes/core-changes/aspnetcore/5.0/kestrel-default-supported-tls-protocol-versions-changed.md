---
ms.openlocfilehash: 97870553d4ec66a569ba63cd945639b03bbbd6df
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539434"
---
### <a name="kestrel-default-supported-tls-protocol-versions-changed"></a><span data-ttu-id="efca5-101">Kestrel: versões do protocolo TLS com suporte padrão alteradas</span><span class="sxs-lookup"><span data-stu-id="efca5-101">Kestrel: Default supported TLS protocol versions changed</span></span>

<span data-ttu-id="efca5-102">O Kestrel agora usa as versões do protocolo TLS padrão do sistema em vez de restringir as conexões com os protocolos TLS 1,1 e TLS 1,2 como fazia anteriormente.</span><span class="sxs-lookup"><span data-stu-id="efca5-102">Kestrel now uses the system default TLS protocol versions rather than restricting connections to the TLS 1.1 and TLS 1.2 protocols like it did previously.</span></span>

<span data-ttu-id="efca5-103">Essa alteração permite:</span><span class="sxs-lookup"><span data-stu-id="efca5-103">This change allows:</span></span>

* <span data-ttu-id="efca5-104">O TLS 1,3 a ser usado por padrão em ambientes que dão suporte a ele.</span><span class="sxs-lookup"><span data-stu-id="efca5-104">TLS 1.3 to be used by default in environments that support it.</span></span>
* <span data-ttu-id="efca5-105">O TLS 1,0 a ser usado em alguns ambientes (como o Windows Server 2016 por padrão), que geralmente [não é desejável](/security/engineering/solving-tls1-problem).</span><span class="sxs-lookup"><span data-stu-id="efca5-105">TLS 1.0 to be used in some environments (such as Windows Server 2016 by default), which is usually [not desirable](/security/engineering/solving-tls1-problem).</span></span>

<span data-ttu-id="efca5-106">Para obter uma discussão, veja Issue [dotnet/aspnetcore # 22563](https://github.com/dotnet/aspnetcore/issues/22563).</span><span class="sxs-lookup"><span data-stu-id="efca5-106">For discussion, see issue [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="efca5-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="efca5-107">Version introduced</span></span>

<span data-ttu-id="efca5-108">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="efca5-108">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="efca5-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="efca5-109">Old behavior</span></span>

<span data-ttu-id="efca5-110">O Kestrel exigiu que as conexões usem TLS 1,1 ou TLS 1,2 por padrão.</span><span class="sxs-lookup"><span data-stu-id="efca5-110">Kestrel required that connections use TLS 1.1 or TLS 1.2 by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="efca5-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="efca5-111">New behavior</span></span>

<span data-ttu-id="efca5-112">O Kestrel permite que o sistema operacional escolha o melhor protocolo a ser usado e bloqueie protocolos inseguros.</span><span class="sxs-lookup"><span data-stu-id="efca5-112">Kestrel allows the operating system to choose the best protocol to use and to block insecure protocols.</span></span> <span data-ttu-id="efca5-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> Agora, o padrão é `SslProtocols.None` em vez de `SslProtocols.Tls12 | SslProtocols.Tls11` .</span><span class="sxs-lookup"><span data-stu-id="efca5-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> now defaults to `SslProtocols.None` instead of `SslProtocols.Tls12 | SslProtocols.Tls11`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="efca5-114">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="efca5-114">Reason for change</span></span>

<span data-ttu-id="efca5-115">A alteração foi feita para dar suporte a TLS 1,3 e futuras versões de TLS por padrão, pois elas se tornam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="efca5-115">The change was made to support TLS 1.3 and future TLS versions by default as they become available.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="efca5-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="efca5-116">Recommended action</span></span>

<span data-ttu-id="efca5-117">A menos que seu aplicativo tenha um motivo específico para não, você deve usar os novos padrões.</span><span class="sxs-lookup"><span data-stu-id="efca5-117">Unless your app has a specific reason not to, you should use the new defaults.</span></span> <span data-ttu-id="efca5-118">Verifique se o sistema está configurado para permitir apenas protocolos seguros.</span><span class="sxs-lookup"><span data-stu-id="efca5-118">Verify your system is configured to allow only secure protocols.</span></span>

<span data-ttu-id="efca5-119">Para desabilitar protocolos mais antigos, execute uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="efca5-119">To disable older protocols, take one of the following actions:</span></span>

* <span data-ttu-id="efca5-120">Desabilite os protocolos mais antigos, como o TLS 1,0, em todo o sistema com as [instruções do Windows](../../../../docs/framework/network-programming/tls.md#configuring-schannel-protocols-in-the-windows-registry).</span><span class="sxs-lookup"><span data-stu-id="efca5-120">Disable older protocols, such as TLS 1.0, system-wide with the [Windows instructions](../../../../docs/framework/network-programming/tls.md#configuring-schannel-protocols-in-the-windows-registry).</span></span> <span data-ttu-id="efca5-121">Atualmente, ele está habilitado por padrão em todas as versões do Windows.</span><span class="sxs-lookup"><span data-stu-id="efca5-121">It's currently enabled by default on all Windows versions.</span></span>
* <span data-ttu-id="efca5-122">Selecione manualmente os protocolos aos quais você deseja dar suporte no código da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="efca5-122">Manually select which protocols you want to support in code as follows:</span></span>

    ```csharp
    using System.Security.Authentication;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel(kestrelOptions =>
                    {
                        kestrelOptions.ConfigureHttpsDefaults(httpsOptions =>
                        {
                            httpsOptions.SslProtocols = SslProtocols.Tls12 | SslProtocols.Tls13;
                        });
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="efca5-123">Infelizmente, não há API para excluir protocolos específicos.</span><span class="sxs-lookup"><span data-stu-id="efca5-123">Unfortunately, there's no API to exclude specific protocols.</span></span>

#### <a name="category"></a><span data-ttu-id="efca5-124">Categoria</span><span class="sxs-lookup"><span data-stu-id="efca5-124">Category</span></span>

<span data-ttu-id="efca5-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="efca5-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="efca5-126">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="efca5-126">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
