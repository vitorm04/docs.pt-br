---
title: ASP.NET Core alterações significativas
titleSuffix: ''
description: Lista as alterações significativas em ASP.NET Core.
ms.date: 08/20/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 8b37ae5c5eea9e192a269092fccf435ab4877e61
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867666"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="cc509-103">ASP.NET Core alterações significativas</span><span class="sxs-lookup"><span data-stu-id="cc509-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="cc509-104">ASP.NET Core fornece os recursos de desenvolvimento de aplicativo Web usados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cc509-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="cc509-105">Selecione um dos links a seguir para alterações significativas em uma versão específica:</span><span class="sxs-lookup"><span data-stu-id="cc509-105">Select one of the following links for breaking changes in a specific version:</span></span>

* [<span data-ttu-id="cc509-106">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="cc509-106">ASP.NET Core 5.0</span></span>](#aspnet-core-50)
* [<span data-ttu-id="cc509-107">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="cc509-107">ASP.NET Core 3.1</span></span>](#aspnet-core-31)
* [<span data-ttu-id="cc509-108">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="cc509-108">ASP.NET Core 3.0</span></span>](#aspnet-core-30)

<span data-ttu-id="cc509-109">As seguintes alterações significativas no ASP.NET Core 3,0, 3,1 e 5,0 estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="cc509-109">The following breaking changes in ASP.NET Core 3.0, 3.1, and 5.0 are documented on this page:</span></span>

- [<span data-ttu-id="cc509-110">APIs antifalsificação obsoletas, CORS, diagnóstico, MVC e roteamento removidas</span><span class="sxs-lookup"><span data-stu-id="cc509-110">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="cc509-111">Autenticação: Google + substituição</span><span class="sxs-lookup"><span data-stu-id="cc509-111">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="cc509-112">Autenticação: Propriedade HttpContext. Authentication removida</span><span class="sxs-lookup"><span data-stu-id="cc509-112">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="cc509-113">Autenticação: Newtonsoft.Jsem tipos substituídos</span><span class="sxs-lookup"><span data-stu-id="cc509-113">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="cc509-114">Autenticação: assinatura OAuthHandler ExchangeCodeAsync alterada</span><span class="sxs-lookup"><span data-stu-id="cc509-114">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="cc509-115">Autorização: sobrecarga de addautoria movida para um assembly diferente</span><span class="sxs-lookup"><span data-stu-id="cc509-115">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="cc509-116">Autorização: IAllowAnonymous removido de AuthorizationFilterContext. Filters</span><span class="sxs-lookup"><span data-stu-id="cc509-116">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="cc509-117">Autorização: implementações de IAuthorizationPolicyProvider exigem novo método</span><span class="sxs-lookup"><span data-stu-id="cc509-117">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="cc509-118">Autorização: o recurso no roteamento de ponto de extremidade é HttpContext</span><span class="sxs-lookup"><span data-stu-id="cc509-118">Authorization: Resource in endpoint routing is HttpContext</span></span>](#authorization-resource-in-endpoint-routing-is-httpcontext)
- [<span data-ttu-id="cc509-119">Azure: pacotes de integração do Azure prefixados da Microsoft removidos</span><span class="sxs-lookup"><span data-stu-id="cc509-119">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="cc509-120">Os métodos de serialização BinaryFormatter são obsoletos e proibidos em aplicativos ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cc509-120">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps)
- [<span data-ttu-id="cc509-121">Mais grande: espaço em branco insignificado cortado de componentes em tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="cc509-121">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>](#blazor-insignificant-whitespace-trimmed-from-components-at-compile-time)
- [<span data-ttu-id="cc509-122">Mais incrivelmente: estrutura de destino de pacotes NuGet alterada</span><span class="sxs-lookup"><span data-stu-id="cc509-122">Blazor: Target framework of NuGet packages changed</span></span>](#blazor-target-framework-of-nuget-packages-changed)
- [<span data-ttu-id="cc509-123">Caching: Propriedade CompactOnMemoryPressure removida</span><span class="sxs-lookup"><span data-stu-id="cc509-123">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="cc509-124">Caching: o Microsoft. Extensions. Caching. SqlServer usa o novo pacote SqlClient</span><span class="sxs-lookup"><span data-stu-id="cc509-124">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="cc509-125">Caching: tipos de ResponseCaching "pubternal" alterados para interno</span><span class="sxs-lookup"><span data-stu-id="cc509-125">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="cc509-126">Proteção de dados: dataprotection. AzureStorage usa novas APIs de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="cc509-126">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="cc509-127">Extensões: alterações de referência de pacote que afetam alguns pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="cc509-127">Extensions: Package reference changes affecting some NuGet packages</span></span>](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [<span data-ttu-id="cc509-128">Hospedagem: AspNetCoreModule v1 removido do pacote de hospedagem do Windows</span><span class="sxs-lookup"><span data-stu-id="cc509-128">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="cc509-129">Hospedagem: host genérico restringe injeção de construtor de inicialização</span><span class="sxs-lookup"><span data-stu-id="cc509-129">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="cc509-130">Hospedagem: redirecionamento de HTTPS habilitado para aplicativos fora do processo do IIS</span><span class="sxs-lookup"><span data-stu-id="cc509-130">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="cc509-131">Hospedagem: tipos IHostingEnvironment e IApplicationLifetime substituídos</span><span class="sxs-lookup"><span data-stu-id="cc509-131">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="cc509-132">Hospedagem: objectpoolprovider removido de dependências WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="cc509-132">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="cc509-133">Tipos de BadHttpRequestException de HTTP: Kestrel e IIS marcados como obsoletos e substituídos</span><span class="sxs-lookup"><span data-stu-id="cc509-133">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="cc509-134">HTTP: navegador SameSite alterações de impacto na autenticação</span><span class="sxs-lookup"><span data-stu-id="cc509-134">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="cc509-135">HTTP: extensibilidade defaulthttpcontext removida</span><span class="sxs-lookup"><span data-stu-id="cc509-135">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="cc509-136">Campos HTTP: Headernames alterados para static readonly</span><span class="sxs-lookup"><span data-stu-id="cc509-136">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="cc509-137">HTTP: instâncias de HttpClient criadas por códigos de status de inteiro de log IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="cc509-137">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [<span data-ttu-id="cc509-138">HTTP: alterações de infraestrutura de corpo de resposta</span><span class="sxs-lookup"><span data-stu-id="cc509-138">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="cc509-139">HTTP: alguns SameSite de cookie foram alterados valores padrão</span><span class="sxs-lookup"><span data-stu-id="cc509-139">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="cc509-140">HTTP: e/s síncrona desabilitada por padrão</span><span class="sxs-lookup"><span data-stu-id="cc509-140">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="cc509-141">HttpS: renegociação de certificado de cliente desabilitada por padrão</span><span class="sxs-lookup"><span data-stu-id="cc509-141">HttpSys: Client certificate renegotiation disabled by default</span></span>](#httpsys-client-certificate-renegotiation-disabled-by-default)
- [<span data-ttu-id="cc509-142">Identidade: sobrecarga do método AddDefaultUI removida</span><span class="sxs-lookup"><span data-stu-id="cc509-142">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="cc509-143">Identidade: alteração da versão de inicialização da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="cc509-143">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="cc509-144">Identidade: o SignInAsync gera uma exceção para a identidade não autenticada</span><span class="sxs-lookup"><span data-stu-id="cc509-144">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="cc509-145">Identity: o Construtor SignInManager aceita o novo parâmetro</span><span class="sxs-lookup"><span data-stu-id="cc509-145">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="cc509-146">Identidade: a interface do usuário usa o recurso de ativos da Web estáticos</span><span class="sxs-lookup"><span data-stu-id="cc509-146">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="cc509-147">IIS: cadeias de consulta de middleware UrlRewrite são preservadas</span><span class="sxs-lookup"><span data-stu-id="cc509-147">IIS: UrlRewrite middleware query strings are preserved</span></span>](#iis-urlrewrite-middleware-query-strings-are-preserved)
- [<span data-ttu-id="cc509-148">Kestrel: alterações de configuração em tempo de execução detectadas por padrão</span><span class="sxs-lookup"><span data-stu-id="cc509-148">Kestrel: Configuration changes at run time detected by default</span></span>](#kestrel-configuration-changes-at-run-time-detected-by-default)
- [<span data-ttu-id="cc509-149">Kestrel: adaptadores de conexão removidos</span><span class="sxs-lookup"><span data-stu-id="cc509-149">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="cc509-150">Kestrel: versões do protocolo TLS com suporte padrão alteradas</span><span class="sxs-lookup"><span data-stu-id="cc509-150">Kestrel: Default supported TLS protocol versions changed</span></span>](#kestrel-default-supported-tls-protocol-versions-changed)
- [<span data-ttu-id="cc509-151">Kestrel: assembly HTTPS vazio removido</span><span class="sxs-lookup"><span data-stu-id="cc509-151">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="cc509-152">Kestrel: HTTP/2 desabilitado via TLS em versões incompatíveis do Windows</span><span class="sxs-lookup"><span data-stu-id="cc509-152">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>](#kestrel-http2-disabled-over-tls-on-incompatible-windows-versions)
- [<span data-ttu-id="cc509-153">Kestrel: transporte Libuv marcado como obsoleto</span><span class="sxs-lookup"><span data-stu-id="cc509-153">Kestrel: Libuv transport marked as obsolete</span></span>](#kestrel-libuv-transport-marked-as-obsolete)
- [<span data-ttu-id="cc509-154">Kestrel: Solicitar cabeçalhos de trailer movidos para nova coleção</span><span class="sxs-lookup"><span data-stu-id="cc509-154">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="cc509-155">Kestrel: alterações na camada de abstração de transporte</span><span class="sxs-lookup"><span data-stu-id="cc509-155">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="cc509-156">Localização: APIs marcadas como obsoletas</span><span class="sxs-lookup"><span data-stu-id="cc509-156">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="cc509-157">Localização: APIs "Pubternal" removidas</span><span class="sxs-lookup"><span data-stu-id="cc509-157">Localization: "Pubternal" APIs removed</span></span>](#localization-pubternal-apis-removed)
- [<span data-ttu-id="cc509-158">Localização: Construtor obsoleto removido no middleware de localização de solicitação</span><span class="sxs-lookup"><span data-stu-id="cc509-158">Localization: Obsolete constructor removed in request localization middleware</span></span>](#localization-obsolete-constructor-removed-in-request-localization-middleware)
- [<span data-ttu-id="cc509-159">Localização: classe ResourceManagerWithCultureStringLocalizer e membro da interface WithCulture removidos</span><span class="sxs-lookup"><span data-stu-id="cc509-159">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [<span data-ttu-id="cc509-160">Log: classe DebugLogger criada internamente</span><span class="sxs-lookup"><span data-stu-id="cc509-160">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="cc509-161">Middleware: página de erro do banco de dados marcada como obsoleta</span><span class="sxs-lookup"><span data-stu-id="cc509-161">Middleware: Database error page marked as obsolete</span></span>](#middleware-database-error-page-marked-as-obsolete)
- [<span data-ttu-id="cc509-162">MVC: sufixo assíncrono de ação do controlador removido</span><span class="sxs-lookup"><span data-stu-id="cc509-162">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="cc509-163">MVC: JsonResult movido para Microsoft. AspNetCore. Mvc. Core</span><span class="sxs-lookup"><span data-stu-id="cc509-163">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="cc509-164">MVC: ferramenta de pré-compilação preterida</span><span class="sxs-lookup"><span data-stu-id="cc509-164">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="cc509-165">MVC: tipos alterados para interno</span><span class="sxs-lookup"><span data-stu-id="cc509-165">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="cc509-166">MVC: Shim de compatibilidade da API Web removido</span><span class="sxs-lookup"><span data-stu-id="cc509-166">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="cc509-167">Razor: compilação de tempo de execução movida para um pacote</span><span class="sxs-lookup"><span data-stu-id="cc509-167">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="cc509-168">Segurança: codificação de nome de cookie removida</span><span class="sxs-lookup"><span data-stu-id="cc509-168">Security: Cookie name encoding removed</span></span>](#security-cookie-name-encoding-removed)
- [<span data-ttu-id="cc509-169">Segurança: versões do pacote NuGet do IdentityModel atualizadas</span><span class="sxs-lookup"><span data-stu-id="cc509-169">Security: IdentityModel NuGet package versions updated</span></span>](#security-identitymodel-nuget-package-versions-updated)
- [<span data-ttu-id="cc509-170">Estado da sessão: APIs obsoletas removidas</span><span class="sxs-lookup"><span data-stu-id="cc509-170">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="cc509-171">Estrutura compartilhada: remoção de assembly do Microsoft. AspNetCore. app</span><span class="sxs-lookup"><span data-stu-id="cc509-171">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="cc509-172">Estrutura compartilhada: Microsoft. AspNetCore. All removidas</span><span class="sxs-lookup"><span data-stu-id="cc509-172">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="cc509-173">Signalr: HandshakeProtocol. SuccessHandshakeData substituído</span><span class="sxs-lookup"><span data-stu-id="cc509-173">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="cc509-174">Signalr: métodos HubConnection removidos</span><span class="sxs-lookup"><span data-stu-id="cc509-174">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="cc509-175">Signalr: construtores HubConnectionContext alterados</span><span class="sxs-lookup"><span data-stu-id="cc509-175">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="cc509-176">Signalr: alteração de nome de pacote de cliente JavaScript</span><span class="sxs-lookup"><span data-stu-id="cc509-176">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="cc509-177">Signalr: protocolo Hub MessagePack movido para o pacote MessagePack 2. x</span><span class="sxs-lookup"><span data-stu-id="cc509-177">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="cc509-178">Signalr: tipo de opções de protocolo de Hub MessagePack alterado</span><span class="sxs-lookup"><span data-stu-id="cc509-178">SignalR: MessagePack Hub Protocol options type changed</span></span>](#signalr-messagepack-hub-protocol-options-type-changed)
- [<span data-ttu-id="cc509-179">Signalr: APIs obsoletas</span><span class="sxs-lookup"><span data-stu-id="cc509-179">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="cc509-180">Signalr: métodos UseSignalR e UseConnections removidos</span><span class="sxs-lookup"><span data-stu-id="cc509-180">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="cc509-181">SPAs: SpaServices e Nodeservices console agente de fallback alterar padrão</span><span class="sxs-lookup"><span data-stu-id="cc509-181">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="cc509-182">SPAs: SpaServices e Nodeservices marcados como obsoletos</span><span class="sxs-lookup"><span data-stu-id="cc509-182">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="cc509-183">Arquivos estáticos: tipo de conteúdo CSV alterado para compatível com padrões</span><span class="sxs-lookup"><span data-stu-id="cc509-183">Static files: CSV content type changed to standards-compliant</span></span>](#static-files-csv-content-type-changed-to-standards-compliant)
- [<span data-ttu-id="cc509-184">Estrutura de destino: .NET Framework sem suporte</span><span class="sxs-lookup"><span data-stu-id="cc509-184">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="cc509-185">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="cc509-185">ASP.NET Core 5.0</span></span>

[!INCLUDE[Authorization: Resource in endpoint routing is HttpContext](~/includes/core-changes/aspnetcore/5.0/authorization-resource-in-endpoint-routing.md)]

***

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE[Blazor: Insignificant whitespace trimmed from components at compile time](~/includes/core-changes/aspnetcore/5.0/blazor-components-trim-insignificant-whitespace.md)]

***

[!INCLUDE[Blazor: Target framework of NuGet packages changed](~/includes/core-changes/aspnetcore/5.0/blazor-packages-target-framework-changed.md)]

***

[!INCLUDE[Extensions: Package reference changes](~/includes/core-changes/aspnetcore/5.0/extensions-package-reference-changes.md)]

***

[!INCLUDE[HTTP: HttpClient instances created by IHttpClientFactory log integer status codes](~/includes/core-changes/aspnetcore/5.0/http-httpclient-instances-log-integer-status-codes.md)]

***

[!INCLUDE[HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced](~/includes/core-changes/aspnetcore/5.0/http-badhttprequestexception-obsolete.md)]

***

[!INCLUDE[HttpSys: Client certificate renegotiation disabled by default](~/includes/core-changes/aspnetcore/5.0/httpsys-client-certificate-renegotiation-disabled-by-default.md)]

***

[!INCLUDE[IIS: UrlRewrite middleware query strings are preserved](~/includes/core-changes/aspnetcore/5.0/iis-urlrewrite-middleware-query-strings-are-preserved.md)]

***

[!INCLUDE[Kestrel: Configuration changes at run time detected by default](~/includes/core-changes/aspnetcore/5.0/kestrel-configuration-changes-at-run-time-detected-by-default.md)]

***
[!INCLUDE[Kestrel: Default supported TLS protocol versions changed](~/includes/core-changes/aspnetcore/5.0/kestrel-default-supported-tls-protocol-versions-changed.md)]

***

[!INCLUDE[Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions](~/includes/core-changes/aspnetcore/5.0/kestrel-disables-http2-over-tls.md)]

***

[!INCLUDE[Kestrel: Libuv transport marked as obsolete](~/includes/core-changes/aspnetcore/5.0/kestrel-libuv-transport-obsolete.md)]

***

[!INCLUDE[Localization: "Pubternal" APIs removed](~/includes/core-changes/aspnetcore/5.0/localization-pubternal-apis-removed.md)]

***

[!INCLUDE[Localization: Obsolete constructor removed in request localization middleware](~/includes/core-changes/aspnetcore/5.0/localization-requestlocalizationmiddleware-constructor-removed.md)]

***

[!INCLUDE[Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed](~/includes/core-changes/aspnetcore/5.0/localization-members-removed.md)]

***

[!INCLUDE[Middleware: Database error page marked as obsolete](~/includes/core-changes/aspnetcore/5.0/middleware-database-error-page-obsolete.md)]

***

[!INCLUDE[Security: Cookie name encoding removed](~/includes/core-changes/aspnetcore/5.0/security-cookie-name-encoding-removed.md)]

***

[!INCLUDE[Security: IdentityModel NuGet package versions updated](~/includes/core-changes/aspnetcore/5.0/security-identitymodel-nuget-package-versions-updated.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a><span data-ttu-id="cc509-186">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="cc509-186">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="cc509-187">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="cc509-187">ASP.NET Core 3.0</span></span>

[!INCLUDE[Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed](~/includes/core-changes/aspnetcore/3.0/obsolete-apis-removed.md)]

***

[!INCLUDE[Authentication: Google+ deprecation](~/includes/core-changes/aspnetcore/3.0/authn-google-plus-authn-changes.md)]

***

[!INCLUDE[Authentication: HttpContext.Authentication property removed](~/includes/core-changes/aspnetcore/3.0/authn-httpcontext-property-removed.md)]

***

[!INCLUDE[Authentication: Newtonsoft.Json types replaced](~/includes/core-changes/aspnetcore/3.0/authn-apis-json-types.md)]

***

[!INCLUDE[Authentication: OAuthHandler ExchangeCodeAsync signature changed](~/includes/core-changes/aspnetcore/3.0/authn-exchangecodeasync-signature-change.md)]

***

[!INCLUDE[Authorization: AddAuthorization overload assembly change](~/includes/core-changes/aspnetcore/3.0/authz-assembly-change.md)]

***

[!INCLUDE[Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters](~/includes/core-changes/aspnetcore/3.0/authz-iallowanonymous-removed-from-collection.md)]

***

[!INCLUDE[Authorization: IAuthorizationPolicyProvider implementations require new method](~/includes/core-changes/aspnetcore/3.0/authz-iauthzpolicyprovider-new-method.md)]

***

[!INCLUDE[Caching: CompactOnMemoryPressure property removed](~/includes/core-changes/aspnetcore/3.0/caching-memory-property-removed.md)]

***

[!INCLUDE[Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package](~/includes/core-changes/aspnetcore/3.0/caching-new-sqlclient-package.md)]

***

[!INCLUDE[Caching: ResponseCaching types changed to internal](~/includes/core-changes/aspnetcore/3.0/caching-response-pubternal-to-internal.md)]

***

[!INCLUDE[Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs](~/includes/core-changes/aspnetcore/3.0/dataprotection-azstorage-using-azstorage-apis.md)]

***

[!INCLUDE[Hosting: ANCM version 1 removed from hosting bundle](~/includes/core-changes/aspnetcore/3.0/hosting-ancmv1-hosting-bundle-removal.md)]

***

[!INCLUDE[Hosting: Generic host restriction on Startup constructor injection](~/includes/core-changes/aspnetcore/3.0/hosting-generic-host-startup-ctor-restriction.md)]

***

[!INCLUDE[Hosting: HTTPS redirection enabled for IIS OutOfProcess](~/includes/core-changes/aspnetcore/3.0/hosting-https-redirection-iis-outofprocess.md)]

***

[!INCLUDE[Hosting: IHostingEnvironment and IApplicationLifetime types replaced](~/includes/core-changes/aspnetcore/3.0/hosting-ihostingenv-iapplifetime-types-replaced.md)]

***

[!INCLUDE[Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies](~/includes/core-changes/aspnetcore/3.0/hosting-objectpoolprovider-webhostbuilder-dependencies.md)]

***

[!INCLUDE[HTTP: DefaultHttpContext extensibility removed](~/includes/core-changes/aspnetcore/3.0/http-defaulthttpcontext-extensibility-removed.md)]

***

[!INCLUDE[HTTP: HeaderNames fields changed to static readonly](~/includes/core-changes/aspnetcore/3.0/http-headernames-constants-staticreadonly.md)]

***

[!INCLUDE[HTTP: Response body infrastructure changes](~/includes/core-changes/aspnetcore/3.0/http-response-body-changes.md)]

***

[!INCLUDE[HTTP: Some cookie SameSite default values changed](~/includes/core-changes/aspnetcore/3.0/http-cookie-samesite-defaults-change.md)]

***

[!INCLUDE[HTTP: Synchronous IO disabled by default](~/includes/core-changes/aspnetcore/3.0/http-synchronous-io-disabled.md)]

***

[!INCLUDE[Identity: AddDefaultUI method overload removed](~/includes/core-changes/aspnetcore/3.0/identity-ui-adddefaultui-overload-removed.md)]

***

[!INCLUDE[Identity: UI Bootstrap version change](~/includes/core-changes/aspnetcore/3.0/identity-ui-bootstrap-version.md)]

***

[!INCLUDE[Identity: SignInAsync throws exception for unauthenticated identity](~/includes/core-changes/aspnetcore/3.0/identity-signinasync-throws-exception.md)]

***

[!INCLUDE[Identity: SignInManager constructor accepts new parameter](~/includes/core-changes/aspnetcore/3.0/identity-signinmanager-ctor-parameter.md)]

***

[!INCLUDE[Identity: UI uses static web assets feature](~/includes/core-changes/aspnetcore/3.0/identity-ui-static-web-assets.md)]

***

[!INCLUDE[Kestrel: Connection adapters removed](~/includes/core-changes/aspnetcore/3.0/kestrel-connection-adapters-removed.md)]

***

[!INCLUDE[Kestrel: Empty HTTPS assembly removed](~/includes/core-changes/aspnetcore/3.0/kestrel-empty-assembly-removed.md)]

***

[!INCLUDE[Kestrel: Request trailer headers moved to new collection](~/includes/core-changes/aspnetcore/3.0/kestrel-request-trailer-headers.md)]

***

[!INCLUDE[Kestrel: Transport abstraction layer changes](~/includes/core-changes/aspnetcore/3.0/kestrel-transport-abstractions.md)]

***

[!INCLUDE[Localization: APIs marked obsolete](~/includes/core-changes/aspnetcore/3.0/localization-apis-marked-obsolete.md)]

***

[!INCLUDE[Logging: DebugLogger class made internal](~/includes/core-changes/aspnetcore/3.0/logging-debuglogger-to-internal.md)]

***

[!INCLUDE[MVC: Controller action Async suffix removed](~/includes/core-changes/aspnetcore/3.0/mvc-action-async-suffix-trimmed.md)]

***

[!INCLUDE[MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core](~/includes/core-changes/aspnetcore/3.0/mvc-jsonresult-moved.md)]

***

[!INCLUDE[MVC: Precompilation tool deprecated](~/includes/core-changes/aspnetcore/3.0/mvc-precompilation-tool-deprecated.md)]

***

[!INCLUDE[MVC: Types changed to internal](~/includes/core-changes/aspnetcore/3.0/mvc-pubternal-to-internal.md)]

***

[!INCLUDE[MVC: Web API compatibility shim removed](~/includes/core-changes/aspnetcore/3.0/mvc-webapi-compat-shim-removed.md)]

***

[!INCLUDE[Razor: Runtime compilation moved to a package](~/includes/core-changes/aspnetcore/3.0/razor-runtime-compilation-package.md)]

***

[!INCLUDE[Session state: Obsolete APIs removed](~/includes/core-changes/aspnetcore/3.0/session-obsolete-apis-removed.md)]

***

[!INCLUDE[Shared framework: Assembly removal from Microsoft.AspNetCore.App](~/includes/core-changes/aspnetcore/3.0/sharedfx-app-shared-framework-assemblies.md)]

***

[!INCLUDE[Shared framework: Microsoft.AspNetCore.All removed](~/includes/core-changes/aspnetcore/3.0/sharedfx-all-framework-removed.md)]

***

[!INCLUDE[SignalR: HandshakeProtocol.SuccessHandshakeData replaced](~/includes/core-changes/aspnetcore/3.0/signalr-successhandshakedata-replaced.md)]

***

[!INCLUDE[SignalR: HubConnection methods removed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnection-methods-removed.md)]

***

[!INCLUDE[SignalR: HubConnectionContext constructors changed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnectioncontext-ctors.md)]

***

[!INCLUDE[SignalR: JavaScript client package name change](~/includes/core-changes/aspnetcore/3.0/signalr-js-client-package-name.md)]

***

[!INCLUDE[SignalR: Obsolete APIs](~/includes/core-changes/aspnetcore/3.0/signalr-obsolete-apis.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices marked obsolete](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-obsolete.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices console logger fallback default change](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-fallback.md)]

***

[!INCLUDE[Target framework: .NET Framework not supported](~/includes/core-changes/aspnetcore/3.0/targetfx-netfx-tfm-support.md)]

***
