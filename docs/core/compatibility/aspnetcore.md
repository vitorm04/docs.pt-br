---
title: ASP.NET Core alterações significativas
titleSuffix: ''
description: Lista as alterações significativas em ASP.NET Core.
ms.date: 09/18/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 33d8d1f7a6179229b3218d0102550a64bfc35a87
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078860"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="f9773-103">ASP.NET Core alterações significativas</span><span class="sxs-lookup"><span data-stu-id="f9773-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="f9773-104">ASP.NET Core fornece os recursos de desenvolvimento de aplicativo Web usados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9773-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="f9773-105">Selecione um dos links a seguir para alterações significativas em uma versão específica:</span><span class="sxs-lookup"><span data-stu-id="f9773-105">Select one of the following links for breaking changes in a specific version:</span></span>

* [<span data-ttu-id="f9773-106">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="f9773-106">ASP.NET Core 5.0</span></span>](#aspnet-core-50)
* [<span data-ttu-id="f9773-107">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="f9773-107">ASP.NET Core 3.1</span></span>](#aspnet-core-31)
* [<span data-ttu-id="f9773-108">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="f9773-108">ASP.NET Core 3.0</span></span>](#aspnet-core-30)

<span data-ttu-id="f9773-109">As seguintes alterações significativas no ASP.NET Core 3,0, 3,1 e 5,0 estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="f9773-109">The following breaking changes in ASP.NET Core 3.0, 3.1, and 5.0 are documented on this page:</span></span>

- [<span data-ttu-id="f9773-110">APIs antifalsificação obsoletas, CORS, diagnóstico, MVC e roteamento removidas</span><span class="sxs-lookup"><span data-stu-id="f9773-110">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="f9773-111">Autenticação: AzureAD. UI e AzureADB2C. UI APIs e pacotes marcados como obsoletos</span><span class="sxs-lookup"><span data-stu-id="f9773-111">Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete</span></span>](#authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete)
- [<span data-ttu-id="f9773-112">Autenticação: Google + substituição</span><span class="sxs-lookup"><span data-stu-id="f9773-112">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="f9773-113">Autenticação: Propriedade HttpContext. Authentication removida</span><span class="sxs-lookup"><span data-stu-id="f9773-113">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="f9773-114">Autenticação: Newtonsoft.Jsem tipos substituídos</span><span class="sxs-lookup"><span data-stu-id="f9773-114">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="f9773-115">Autenticação: assinatura OAuthHandler ExchangeCodeAsync alterada</span><span class="sxs-lookup"><span data-stu-id="f9773-115">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="f9773-116">Autorização: sobrecarga de addautoria movida para um assembly diferente</span><span class="sxs-lookup"><span data-stu-id="f9773-116">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="f9773-117">Autorização: IAllowAnonymous removido de AuthorizationFilterContext. Filters</span><span class="sxs-lookup"><span data-stu-id="f9773-117">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="f9773-118">Autorização: implementações de IAuthorizationPolicyProvider exigem novo método</span><span class="sxs-lookup"><span data-stu-id="f9773-118">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="f9773-119">Autorização: o recurso no roteamento de ponto de extremidade é HttpContext</span><span class="sxs-lookup"><span data-stu-id="f9773-119">Authorization: Resource in endpoint routing is HttpContext</span></span>](#authorization-resource-in-endpoint-routing-is-httpcontext)
- [<span data-ttu-id="f9773-120">Azure: pacotes de integração do Azure prefixados da Microsoft removidos</span><span class="sxs-lookup"><span data-stu-id="f9773-120">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="f9773-121">Os métodos de serialização BinaryFormatter são obsoletos e proibidos em aplicativos ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f9773-121">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps)
- [<span data-ttu-id="f9773-122">Mais grande: espaço em branco insignificado cortado de componentes em tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="f9773-122">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>](#blazor-insignificant-whitespace-trimmed-from-components-at-compile-time)
- [<span data-ttu-id="f9773-123">Mais de: JSObjectReference e tipos JSInProcessObjectReference alterados para interno</span><span class="sxs-lookup"><span data-stu-id="f9773-123">Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal</span></span>](#blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal)
- [<span data-ttu-id="f9773-124">Mais incrivelmente: o recurso ProtectedBrowserStorage mudou para a estrutura compartilhada</span><span class="sxs-lookup"><span data-stu-id="f9773-124">Blazor: ProtectedBrowserStorage feature moved to shared framework</span></span>](#blazor-protectedbrowserstorage-feature-moved-to-shared-framework)
- [<span data-ttu-id="f9773-125">Mais do que: RenderTreeFrame campos públicos ReadOnly se tornaram Propriedades</span><span class="sxs-lookup"><span data-stu-id="f9773-125">Blazor: RenderTreeFrame readonly public fields have become properties</span></span>](#blazor-rendertreeframe-readonly-public-fields-have-become-properties)
- [<span data-ttu-id="f9773-126">Mais incrivelmente: estrutura de destino de pacotes NuGet alterada</span><span class="sxs-lookup"><span data-stu-id="f9773-126">Blazor: Target framework of NuGet packages changed</span></span>](#blazor-target-framework-of-nuget-packages-changed)
- [<span data-ttu-id="f9773-127">Caching: Propriedade CompactOnMemoryPressure removida</span><span class="sxs-lookup"><span data-stu-id="f9773-127">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="f9773-128">Caching: o Microsoft. Extensions. Caching. SqlServer usa o novo pacote SqlClient</span><span class="sxs-lookup"><span data-stu-id="f9773-128">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="f9773-129">Caching: tipos de ResponseCaching "pubternal" alterados para interno</span><span class="sxs-lookup"><span data-stu-id="f9773-129">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="f9773-130">Proteção de dados: dataprotection. AzureStorage usa novas APIs de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="f9773-130">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="f9773-131">Extensões: alterações de referência de pacote que afetam alguns pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="f9773-131">Extensions: Package reference changes affecting some NuGet packages</span></span>](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [<span data-ttu-id="f9773-132">Hospedagem: AspNetCoreModule v1 removido do pacote de hospedagem do Windows</span><span class="sxs-lookup"><span data-stu-id="f9773-132">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="f9773-133">Hospedagem: host genérico restringe injeção de construtor de inicialização</span><span class="sxs-lookup"><span data-stu-id="f9773-133">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="f9773-134">Hospedagem: redirecionamento de HTTPS habilitado para aplicativos fora do processo do IIS</span><span class="sxs-lookup"><span data-stu-id="f9773-134">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="f9773-135">Hospedagem: tipos IHostingEnvironment e IApplicationLifetime substituídos</span><span class="sxs-lookup"><span data-stu-id="f9773-135">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="f9773-136">Hospedagem: objectpoolprovider removido de dependências WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="f9773-136">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="f9773-137">Tipos de BadHttpRequestException de HTTP: Kestrel e IIS marcados como obsoletos e substituídos</span><span class="sxs-lookup"><span data-stu-id="f9773-137">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="f9773-138">HTTP: navegador SameSite alterações de impacto na autenticação</span><span class="sxs-lookup"><span data-stu-id="f9773-138">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="f9773-139">HTTP: extensibilidade defaulthttpcontext removida</span><span class="sxs-lookup"><span data-stu-id="f9773-139">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="f9773-140">Campos HTTP: Headernames alterados para static readonly</span><span class="sxs-lookup"><span data-stu-id="f9773-140">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="f9773-141">HTTP: instâncias de HttpClient criadas por códigos de status de inteiro de log IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="f9773-141">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [<span data-ttu-id="f9773-142">HTTP: alterações de infraestrutura de corpo de resposta</span><span class="sxs-lookup"><span data-stu-id="f9773-142">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="f9773-143">HTTP: alguns SameSite de cookie foram alterados valores padrão</span><span class="sxs-lookup"><span data-stu-id="f9773-143">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="f9773-144">HTTP: e/s síncrona desabilitada por padrão</span><span class="sxs-lookup"><span data-stu-id="f9773-144">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="f9773-145">HttpS: renegociação de certificado de cliente desabilitada por padrão</span><span class="sxs-lookup"><span data-stu-id="f9773-145">HttpSys: Client certificate renegotiation disabled by default</span></span>](#httpsys-client-certificate-renegotiation-disabled-by-default)
- [<span data-ttu-id="f9773-146">Identidade: sobrecarga do método AddDefaultUI removida</span><span class="sxs-lookup"><span data-stu-id="f9773-146">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="f9773-147">Identidade: alteração da versão de inicialização da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f9773-147">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="f9773-148">Identidade: o SignInAsync gera uma exceção para a identidade não autenticada</span><span class="sxs-lookup"><span data-stu-id="f9773-148">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="f9773-149">Identity: o Construtor SignInManager aceita o novo parâmetro</span><span class="sxs-lookup"><span data-stu-id="f9773-149">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="f9773-150">Identidade: a interface do usuário usa o recurso de ativos da Web estáticos</span><span class="sxs-lookup"><span data-stu-id="f9773-150">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="f9773-151">IIS: cadeias de consulta de middleware UrlRewrite são preservadas</span><span class="sxs-lookup"><span data-stu-id="f9773-151">IIS: UrlRewrite middleware query strings are preserved</span></span>](#iis-urlrewrite-middleware-query-strings-are-preserved)
- [<span data-ttu-id="f9773-152">Kestrel: alterações de configuração em tempo de execução detectadas por padrão</span><span class="sxs-lookup"><span data-stu-id="f9773-152">Kestrel: Configuration changes at run time detected by default</span></span>](#kestrel-configuration-changes-at-run-time-detected-by-default)
- [<span data-ttu-id="f9773-153">Kestrel: adaptadores de conexão removidos</span><span class="sxs-lookup"><span data-stu-id="f9773-153">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="f9773-154">Kestrel: versões do protocolo TLS com suporte padrão alteradas</span><span class="sxs-lookup"><span data-stu-id="f9773-154">Kestrel: Default supported TLS protocol versions changed</span></span>](#kestrel-default-supported-tls-protocol-versions-changed)
- [<span data-ttu-id="f9773-155">Kestrel: assembly HTTPS vazio removido</span><span class="sxs-lookup"><span data-stu-id="f9773-155">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="f9773-156">Kestrel: HTTP/2 desabilitado via TLS em versões incompatíveis do Windows</span><span class="sxs-lookup"><span data-stu-id="f9773-156">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>](#kestrel-http2-disabled-over-tls-on-incompatible-windows-versions)
- [<span data-ttu-id="f9773-157">Kestrel: transporte Libuv marcado como obsoleto</span><span class="sxs-lookup"><span data-stu-id="f9773-157">Kestrel: Libuv transport marked as obsolete</span></span>](#kestrel-libuv-transport-marked-as-obsolete)
- [<span data-ttu-id="f9773-158">Kestrel: Solicitar cabeçalhos de trailer movidos para nova coleção</span><span class="sxs-lookup"><span data-stu-id="f9773-158">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="f9773-159">Kestrel: alterações na camada de abstração de transporte</span><span class="sxs-lookup"><span data-stu-id="f9773-159">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="f9773-160">Localização: APIs marcadas como obsoletas</span><span class="sxs-lookup"><span data-stu-id="f9773-160">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="f9773-161">Localização: APIs "Pubternal" removidas</span><span class="sxs-lookup"><span data-stu-id="f9773-161">Localization: "Pubternal" APIs removed</span></span>](#localization-pubternal-apis-removed)
- [<span data-ttu-id="f9773-162">Localização: Construtor obsoleto removido no middleware de localização de solicitação</span><span class="sxs-lookup"><span data-stu-id="f9773-162">Localization: Obsolete constructor removed in request localization middleware</span></span>](#localization-obsolete-constructor-removed-in-request-localization-middleware)
- [<span data-ttu-id="f9773-163">Localização: classe ResourceManagerWithCultureStringLocalizer e membro da interface WithCulture removidos</span><span class="sxs-lookup"><span data-stu-id="f9773-163">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [<span data-ttu-id="f9773-164">Log: classe DebugLogger criada internamente</span><span class="sxs-lookup"><span data-stu-id="f9773-164">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="f9773-165">Middleware: página de erro do banco de dados marcada como obsoleta</span><span class="sxs-lookup"><span data-stu-id="f9773-165">Middleware: Database error page marked as obsolete</span></span>](#middleware-database-error-page-marked-as-obsolete)
- [<span data-ttu-id="f9773-166">Middleware: o middleware do manipulador de exceção lança a exceção original se o manipulador não for encontrado</span><span class="sxs-lookup"><span data-stu-id="f9773-166">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>](#middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found)
- [<span data-ttu-id="f9773-167">MVC: sufixo assíncrono de ação do controlador removido</span><span class="sxs-lookup"><span data-stu-id="f9773-167">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="f9773-168">MVC: JsonResult movido para Microsoft. AspNetCore. Mvc. Core</span><span class="sxs-lookup"><span data-stu-id="f9773-168">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="f9773-169">MVC: ferramenta de pré-compilação preterida</span><span class="sxs-lookup"><span data-stu-id="f9773-169">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="f9773-170">MVC: tipos alterados para interno</span><span class="sxs-lookup"><span data-stu-id="f9773-170">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="f9773-171">MVC: Shim de compatibilidade da API Web removido</span><span class="sxs-lookup"><span data-stu-id="f9773-171">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="f9773-172">Razor: API RazorTemplateEngine removida</span><span class="sxs-lookup"><span data-stu-id="f9773-172">Razor: RazorTemplateEngine API removed</span></span>](#razor-razortemplateengine-api-removed)
- [<span data-ttu-id="f9773-173">Razor: compilação de tempo de execução movida para um pacote</span><span class="sxs-lookup"><span data-stu-id="f9773-173">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="f9773-174">Segurança: codificação de nome de cookie removida</span><span class="sxs-lookup"><span data-stu-id="f9773-174">Security: Cookie name encoding removed</span></span>](#security-cookie-name-encoding-removed)
- [<span data-ttu-id="f9773-175">Segurança: versões do pacote NuGet do IdentityModel atualizadas</span><span class="sxs-lookup"><span data-stu-id="f9773-175">Security: IdentityModel NuGet package versions updated</span></span>](#security-identitymodel-nuget-package-versions-updated)
- [<span data-ttu-id="f9773-176">Estado da sessão: APIs obsoletas removidas</span><span class="sxs-lookup"><span data-stu-id="f9773-176">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="f9773-177">Estrutura compartilhada: remoção de assembly do Microsoft. AspNetCore. app</span><span class="sxs-lookup"><span data-stu-id="f9773-177">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="f9773-178">Estrutura compartilhada: Microsoft. AspNetCore. All removidas</span><span class="sxs-lookup"><span data-stu-id="f9773-178">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="f9773-179">Signalr: HandshakeProtocol. SuccessHandshakeData substituído</span><span class="sxs-lookup"><span data-stu-id="f9773-179">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="f9773-180">Signalr: métodos HubConnection removidos</span><span class="sxs-lookup"><span data-stu-id="f9773-180">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="f9773-181">Signalr: construtores HubConnectionContext alterados</span><span class="sxs-lookup"><span data-stu-id="f9773-181">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="f9773-182">Signalr: alteração de nome de pacote de cliente JavaScript</span><span class="sxs-lookup"><span data-stu-id="f9773-182">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="f9773-183">Signalr: protocolo Hub MessagePack movido para o pacote MessagePack 2. x</span><span class="sxs-lookup"><span data-stu-id="f9773-183">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="f9773-184">Signalr: tipo de opções de protocolo de Hub MessagePack alterado</span><span class="sxs-lookup"><span data-stu-id="f9773-184">SignalR: MessagePack Hub Protocol options type changed</span></span>](#signalr-messagepack-hub-protocol-options-type-changed)
- [<span data-ttu-id="f9773-185">Signalr: APIs obsoletas</span><span class="sxs-lookup"><span data-stu-id="f9773-185">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="f9773-186">Signalr: métodos UseSignalR e UseConnections removidos</span><span class="sxs-lookup"><span data-stu-id="f9773-186">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="f9773-187">SPAs: SpaServices e Nodeservices console agente de fallback alterar padrão</span><span class="sxs-lookup"><span data-stu-id="f9773-187">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="f9773-188">SPAs: SpaServices e Nodeservices marcados como obsoletos</span><span class="sxs-lookup"><span data-stu-id="f9773-188">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="f9773-189">Arquivos estáticos: tipo de conteúdo CSV alterado para compatível com padrões</span><span class="sxs-lookup"><span data-stu-id="f9773-189">Static files: CSV content type changed to standards-compliant</span></span>](#static-files-csv-content-type-changed-to-standards-compliant)
- [<span data-ttu-id="f9773-190">Estrutura de destino: .NET Framework sem suporte</span><span class="sxs-lookup"><span data-stu-id="f9773-190">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="f9773-191">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="f9773-191">ASP.NET Core 5.0</span></span>

[!INCLUDE[Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete](~/includes/core-changes/aspnetcore/5.0/authentication-aad-packages-obsolete.md)]

***

[!INCLUDE[Authorization: Resource in endpoint routing is HttpContext](~/includes/core-changes/aspnetcore/5.0/authorization-resource-in-endpoint-routing.md)]

***

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE[Blazor: Insignificant whitespace trimmed from components at compile time](~/includes/core-changes/aspnetcore/5.0/blazor-components-trim-insignificant-whitespace.md)]

***

[!INCLUDE[Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal](~/includes/core-changes/aspnetcore/5.0/blazor-jsobjectreference-to-internal.md)]

***

[!INCLUDE[Blazor: ProtectedBrowserStorage feature moved to shared framework](~/includes/core-changes/aspnetcore/5.0/blazor-protectedbrowserstorage-moved.md)]

***

[!INCLUDE[Blazor: RenderTreeFrame readonly public fields have become properties](~/includes/core-changes/aspnetcore/5.0/blazor-rendertreeframe-fields-become-properties.md)]

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

[!INCLUDE[Middleware: Exception Handler Middleware throws original exception if handler not found](~/includes/core-changes/aspnetcore/5.0/middleware-exception-handler-throws-original-exception.md)]

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

## <a name="aspnet-core-31"></a><span data-ttu-id="f9773-192">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="f9773-192">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="f9773-193">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="f9773-193">ASP.NET Core 3.0</span></span>

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

[!INCLUDE[Razor: RazorTemplatEengine API removed](~/includes/core-changes/aspnetcore/3.0/razor-razortemplateengine-api-removed.md)]

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
