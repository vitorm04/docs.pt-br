---
title: ASP.NET Core alterações significativas
titleSuffix: ''
description: Lista as alterações significativas em ASP.NET Core.
ms.date: 10/06/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 37a366e30f7dc25a5da430de777755b8c9f6dd38
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804940"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="f5878-103">ASP.NET Core alterações significativas</span><span class="sxs-lookup"><span data-stu-id="f5878-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="f5878-104">ASP.NET Core fornece os recursos de desenvolvimento de aplicativo Web usados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f5878-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="f5878-105">Selecione um dos links a seguir para alterações significativas em uma versão específica:</span><span class="sxs-lookup"><span data-stu-id="f5878-105">Select one of the following links for breaking changes in a specific version:</span></span>

* [<span data-ttu-id="f5878-106">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="f5878-106">ASP.NET Core 5.0</span></span>](#aspnet-core-50)
* [<span data-ttu-id="f5878-107">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="f5878-107">ASP.NET Core 3.1</span></span>](#aspnet-core-31)
* [<span data-ttu-id="f5878-108">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="f5878-108">ASP.NET Core 3.0</span></span>](#aspnet-core-30)

<span data-ttu-id="f5878-109">As seguintes alterações significativas no ASP.NET Core 3,0, 3,1 e 5,0 estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="f5878-109">The following breaking changes in ASP.NET Core 3.0, 3.1, and 5.0 are documented on this page:</span></span>

- [<span data-ttu-id="f5878-110">APIs antifalsificação obsoletas, CORS, diagnóstico, MVC e roteamento removidas</span><span class="sxs-lookup"><span data-stu-id="f5878-110">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="f5878-111">Autenticação: AzureAD. UI e AzureADB2C. UI APIs e pacotes marcados como obsoletos</span><span class="sxs-lookup"><span data-stu-id="f5878-111">Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete</span></span>](#authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete)
- [<span data-ttu-id="f5878-112">Autenticação: Google + substituição</span><span class="sxs-lookup"><span data-stu-id="f5878-112">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="f5878-113">Autenticação: Propriedade HttpContext. Authentication removida</span><span class="sxs-lookup"><span data-stu-id="f5878-113">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="f5878-114">Autenticação: Newtonsoft.Jsem tipos substituídos</span><span class="sxs-lookup"><span data-stu-id="f5878-114">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="f5878-115">Autenticação: assinatura OAuthHandler ExchangeCodeAsync alterada</span><span class="sxs-lookup"><span data-stu-id="f5878-115">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="f5878-116">Autorização: sobrecarga de addautoria movida para um assembly diferente</span><span class="sxs-lookup"><span data-stu-id="f5878-116">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="f5878-117">Autorização: IAllowAnonymous removido de AuthorizationFilterContext. Filters</span><span class="sxs-lookup"><span data-stu-id="f5878-117">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="f5878-118">Autorização: implementações de IAuthorizationPolicyProvider exigem novo método</span><span class="sxs-lookup"><span data-stu-id="f5878-118">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="f5878-119">Autorização: o recurso no roteamento de ponto de extremidade é HttpContext</span><span class="sxs-lookup"><span data-stu-id="f5878-119">Authorization: Resource in endpoint routing is HttpContext</span></span>](#authorization-resource-in-endpoint-routing-is-httpcontext)
- [<span data-ttu-id="f5878-120">Azure: pacotes de integração do Azure prefixados da Microsoft removidos</span><span class="sxs-lookup"><span data-stu-id="f5878-120">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="f5878-121">Os métodos de serialização BinaryFormatter são obsoletos e proibidos em aplicativos ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f5878-121">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps)
- [<span data-ttu-id="f5878-122">Mais grande: espaço em branco insignificado cortado de componentes em tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="f5878-122">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>](#blazor-insignificant-whitespace-trimmed-from-components-at-compile-time)
- [<span data-ttu-id="f5878-123">Mais de: JSObjectReference e tipos JSInProcessObjectReference alterados para interno</span><span class="sxs-lookup"><span data-stu-id="f5878-123">Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal</span></span>](#blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal)
- [<span data-ttu-id="f5878-124">Mais incrivelmente: o recurso ProtectedBrowserStorage mudou para a estrutura compartilhada</span><span class="sxs-lookup"><span data-stu-id="f5878-124">Blazor: ProtectedBrowserStorage feature moved to shared framework</span></span>](#blazor-protectedbrowserstorage-feature-moved-to-shared-framework)
- [<span data-ttu-id="f5878-125">Mais do que: RenderTreeFrame campos públicos ReadOnly se tornaram Propriedades</span><span class="sxs-lookup"><span data-stu-id="f5878-125">Blazor: RenderTreeFrame readonly public fields have become properties</span></span>](#blazor-rendertreeframe-readonly-public-fields-have-become-properties)
- [<span data-ttu-id="f5878-126">Mais incrivelmente: estrutura de destino de pacotes NuGet alterada</span><span class="sxs-lookup"><span data-stu-id="f5878-126">Blazor: Target framework of NuGet packages changed</span></span>](#blazor-target-framework-of-nuget-packages-changed)
- [<span data-ttu-id="f5878-127">Mais incrivelmente: suporte a navegador atualizado</span><span class="sxs-lookup"><span data-stu-id="f5878-127">Blazor: Updated browser support</span></span>](#blazor-updated-browser-support)
- [<span data-ttu-id="f5878-128">Caching: Propriedade CompactOnMemoryPressure removida</span><span class="sxs-lookup"><span data-stu-id="f5878-128">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="f5878-129">Caching: o Microsoft. Extensions. Caching. SqlServer usa o novo pacote SqlClient</span><span class="sxs-lookup"><span data-stu-id="f5878-129">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="f5878-130">Caching: tipos de ResponseCaching "pubternal" alterados para interno</span><span class="sxs-lookup"><span data-stu-id="f5878-130">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="f5878-131">Proteção de dados: dataprotection. AzureStorage usa novas APIs de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="f5878-131">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="f5878-132">Extensões: alterações de referência de pacote que afetam alguns pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="f5878-132">Extensions: Package reference changes affecting some NuGet packages</span></span>](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [<span data-ttu-id="f5878-133">Hospedagem: AspNetCoreModule v1 removido do pacote de hospedagem do Windows</span><span class="sxs-lookup"><span data-stu-id="f5878-133">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="f5878-134">Hospedagem: host genérico restringe injeção de construtor de inicialização</span><span class="sxs-lookup"><span data-stu-id="f5878-134">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="f5878-135">Hospedagem: redirecionamento de HTTPS habilitado para aplicativos fora do processo do IIS</span><span class="sxs-lookup"><span data-stu-id="f5878-135">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="f5878-136">Hospedagem: tipos IHostingEnvironment e IApplicationLifetime substituídos</span><span class="sxs-lookup"><span data-stu-id="f5878-136">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="f5878-137">Hospedagem: objectpoolprovider removido de dependências WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="f5878-137">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="f5878-138">Tipos de BadHttpRequestException de HTTP: Kestrel e IIS marcados como obsoletos e substituídos</span><span class="sxs-lookup"><span data-stu-id="f5878-138">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="f5878-139">HTTP: navegador SameSite alterações de impacto na autenticação</span><span class="sxs-lookup"><span data-stu-id="f5878-139">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="f5878-140">HTTP: extensibilidade defaulthttpcontext removida</span><span class="sxs-lookup"><span data-stu-id="f5878-140">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="f5878-141">Campos HTTP: Headernames alterados para static readonly</span><span class="sxs-lookup"><span data-stu-id="f5878-141">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="f5878-142">HTTP: instâncias de HttpClient criadas por códigos de status de inteiro de log IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="f5878-142">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [<span data-ttu-id="f5878-143">HTTP: alterações de infraestrutura de corpo de resposta</span><span class="sxs-lookup"><span data-stu-id="f5878-143">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="f5878-144">HTTP: alguns SameSite de cookie foram alterados valores padrão</span><span class="sxs-lookup"><span data-stu-id="f5878-144">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="f5878-145">HTTP: e/s síncrona desabilitada por padrão</span><span class="sxs-lookup"><span data-stu-id="f5878-145">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="f5878-146">HttpS: renegociação de certificado de cliente desabilitada por padrão</span><span class="sxs-lookup"><span data-stu-id="f5878-146">HttpSys: Client certificate renegotiation disabled by default</span></span>](#httpsys-client-certificate-renegotiation-disabled-by-default)
- [<span data-ttu-id="f5878-147">Identidade: sobrecarga do método AddDefaultUI removida</span><span class="sxs-lookup"><span data-stu-id="f5878-147">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="f5878-148">Identidade: alteração da versão de inicialização da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f5878-148">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="f5878-149">Identidade: o SignInAsync gera uma exceção para a identidade não autenticada</span><span class="sxs-lookup"><span data-stu-id="f5878-149">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="f5878-150">Identity: o Construtor SignInManager aceita o novo parâmetro</span><span class="sxs-lookup"><span data-stu-id="f5878-150">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="f5878-151">Identidade: a interface do usuário usa o recurso de ativos da Web estáticos</span><span class="sxs-lookup"><span data-stu-id="f5878-151">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="f5878-152">IIS: cadeias de consulta de middleware UrlRewrite são preservadas</span><span class="sxs-lookup"><span data-stu-id="f5878-152">IIS: UrlRewrite middleware query strings are preserved</span></span>](#iis-urlrewrite-middleware-query-strings-are-preserved)
- [<span data-ttu-id="f5878-153">Kestrel: alterações de configuração em tempo de execução detectadas por padrão</span><span class="sxs-lookup"><span data-stu-id="f5878-153">Kestrel: Configuration changes at run time detected by default</span></span>](#kestrel-configuration-changes-at-run-time-detected-by-default)
- [<span data-ttu-id="f5878-154">Kestrel: adaptadores de conexão removidos</span><span class="sxs-lookup"><span data-stu-id="f5878-154">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="f5878-155">Kestrel: versões do protocolo TLS com suporte padrão alteradas</span><span class="sxs-lookup"><span data-stu-id="f5878-155">Kestrel: Default supported TLS protocol versions changed</span></span>](#kestrel-default-supported-tls-protocol-versions-changed)
- [<span data-ttu-id="f5878-156">Kestrel: assembly HTTPS vazio removido</span><span class="sxs-lookup"><span data-stu-id="f5878-156">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="f5878-157">Kestrel: HTTP/2 desabilitado via TLS em versões incompatíveis do Windows</span><span class="sxs-lookup"><span data-stu-id="f5878-157">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>](#kestrel-http2-disabled-over-tls-on-incompatible-windows-versions)
- [<span data-ttu-id="f5878-158">Kestrel: transporte Libuv marcado como obsoleto</span><span class="sxs-lookup"><span data-stu-id="f5878-158">Kestrel: Libuv transport marked as obsolete</span></span>](#kestrel-libuv-transport-marked-as-obsolete)
- [<span data-ttu-id="f5878-159">Kestrel: Solicitar cabeçalhos de trailer movidos para nova coleção</span><span class="sxs-lookup"><span data-stu-id="f5878-159">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="f5878-160">Kestrel: alterações na camada de abstração de transporte</span><span class="sxs-lookup"><span data-stu-id="f5878-160">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="f5878-161">Localização: APIs marcadas como obsoletas</span><span class="sxs-lookup"><span data-stu-id="f5878-161">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="f5878-162">Localização: APIs "Pubternal" removidas</span><span class="sxs-lookup"><span data-stu-id="f5878-162">Localization: "Pubternal" APIs removed</span></span>](#localization-pubternal-apis-removed)
- [<span data-ttu-id="f5878-163">Localização: Construtor obsoleto removido no middleware de localização de solicitação</span><span class="sxs-lookup"><span data-stu-id="f5878-163">Localization: Obsolete constructor removed in request localization middleware</span></span>](#localization-obsolete-constructor-removed-in-request-localization-middleware)
- [<span data-ttu-id="f5878-164">Localização: classe ResourceManagerWithCultureStringLocalizer e membro da interface WithCulture removidos</span><span class="sxs-lookup"><span data-stu-id="f5878-164">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [<span data-ttu-id="f5878-165">Log: classe DebugLogger criada internamente</span><span class="sxs-lookup"><span data-stu-id="f5878-165">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="f5878-166">Middleware: página de erro do banco de dados marcada como obsoleta</span><span class="sxs-lookup"><span data-stu-id="f5878-166">Middleware: Database error page marked as obsolete</span></span>](#middleware-database-error-page-marked-as-obsolete)
- [<span data-ttu-id="f5878-167">Middleware: o middleware do manipulador de exceção lança a exceção original se o manipulador não for encontrado</span><span class="sxs-lookup"><span data-stu-id="f5878-167">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>](#middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found)
- [<span data-ttu-id="f5878-168">MVC: sufixo assíncrono de ação do controlador removido</span><span class="sxs-lookup"><span data-stu-id="f5878-168">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="f5878-169">MVC: JsonResult movido para Microsoft. AspNetCore. Mvc. Core</span><span class="sxs-lookup"><span data-stu-id="f5878-169">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="f5878-170">MVC: ObjectModelValidator chama uma nova sobrecarga de ValidationVisitor. Validate</span><span class="sxs-lookup"><span data-stu-id="f5878-170">MVC: ObjectModelValidator calls a new overload of ValidationVisitor.Validate</span></span>](#mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate)
- [<span data-ttu-id="f5878-171">MVC: ferramenta de pré-compilação preterida</span><span class="sxs-lookup"><span data-stu-id="f5878-171">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="f5878-172">MVC: tipos alterados para interno</span><span class="sxs-lookup"><span data-stu-id="f5878-172">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="f5878-173">MVC: Shim de compatibilidade da API Web removido</span><span class="sxs-lookup"><span data-stu-id="f5878-173">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="f5878-174">Razor: API RazorTemplateEngine removida</span><span class="sxs-lookup"><span data-stu-id="f5878-174">Razor: RazorTemplateEngine API removed</span></span>](#razor-razortemplateengine-api-removed)
- [<span data-ttu-id="f5878-175">Razor: compilação de tempo de execução movida para um pacote</span><span class="sxs-lookup"><span data-stu-id="f5878-175">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="f5878-176">Segurança: codificação de nome de cookie removida</span><span class="sxs-lookup"><span data-stu-id="f5878-176">Security: Cookie name encoding removed</span></span>](#security-cookie-name-encoding-removed)
- [<span data-ttu-id="f5878-177">Segurança: versões do pacote NuGet do IdentityModel atualizadas</span><span class="sxs-lookup"><span data-stu-id="f5878-177">Security: IdentityModel NuGet package versions updated</span></span>](#security-identitymodel-nuget-package-versions-updated)
- [<span data-ttu-id="f5878-178">Estado da sessão: APIs obsoletas removidas</span><span class="sxs-lookup"><span data-stu-id="f5878-178">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="f5878-179">Estrutura compartilhada: remoção de assembly do Microsoft. AspNetCore. app</span><span class="sxs-lookup"><span data-stu-id="f5878-179">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="f5878-180">Estrutura compartilhada: Microsoft. AspNetCore. All removidas</span><span class="sxs-lookup"><span data-stu-id="f5878-180">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="f5878-181">Signalr: HandshakeProtocol. SuccessHandshakeData substituído</span><span class="sxs-lookup"><span data-stu-id="f5878-181">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="f5878-182">Signalr: métodos HubConnection removidos</span><span class="sxs-lookup"><span data-stu-id="f5878-182">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="f5878-183">Signalr: construtores HubConnectionContext alterados</span><span class="sxs-lookup"><span data-stu-id="f5878-183">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="f5878-184">Signalr: alteração de nome de pacote de cliente JavaScript</span><span class="sxs-lookup"><span data-stu-id="f5878-184">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="f5878-185">Signalr: protocolo Hub MessagePack movido para o pacote MessagePack 2. x</span><span class="sxs-lookup"><span data-stu-id="f5878-185">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="f5878-186">Signalr: tipo de opções de protocolo de Hub MessagePack alterado</span><span class="sxs-lookup"><span data-stu-id="f5878-186">SignalR: MessagePack Hub Protocol options type changed</span></span>](#signalr-messagepack-hub-protocol-options-type-changed)
- [<span data-ttu-id="f5878-187">Signalr: APIs obsoletas</span><span class="sxs-lookup"><span data-stu-id="f5878-187">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="f5878-188">Signalr: métodos UseSignalR e UseConnections removidos</span><span class="sxs-lookup"><span data-stu-id="f5878-188">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="f5878-189">SPAs: SpaServices e Nodeservices console agente de fallback alterar padrão</span><span class="sxs-lookup"><span data-stu-id="f5878-189">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="f5878-190">SPAs: SpaServices e Nodeservices marcados como obsoletos</span><span class="sxs-lookup"><span data-stu-id="f5878-190">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="f5878-191">Arquivos estáticos: tipo de conteúdo CSV alterado para compatível com padrões</span><span class="sxs-lookup"><span data-stu-id="f5878-191">Static files: CSV content type changed to standards-compliant</span></span>](#static-files-csv-content-type-changed-to-standards-compliant)
- [<span data-ttu-id="f5878-192">APIs de System. Security. Cryptography não têm suporte no Webassembly de mais incrivelmente</span><span class="sxs-lookup"><span data-stu-id="f5878-192">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly)
- [<span data-ttu-id="f5878-193">Estrutura de destino: .NET Framework sem suporte</span><span class="sxs-lookup"><span data-stu-id="f5878-193">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="f5878-194">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="f5878-194">ASP.NET Core 5.0</span></span>

[!INCLUDE[Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete](~/includes/core-changes/aspnetcore/5.0/authentication-aad-packages-obsolete.md)]

***

[!INCLUDE[Authorization: Resource in endpoint routing is HttpContext](~/includes/core-changes/aspnetcore/5.0/authorization-resource-in-endpoint-routing.md)]

***

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[Serialization: BinaryFormatter serialization obsolete](~/includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

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

[!INCLUDE[Blazor: Updated browser support](~/includes/core-changes/aspnetcore/5.0/blazor-browser-support-updated.md)]

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

[!INCLUDE[MVC: ObjectModelValidator calls a new overload of ValidationVisitor.Validate](~/includes/core-changes/aspnetcore/5.0/mvc-objectmodelvalidator-calls-new-overload.md)]

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

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a><span data-ttu-id="f5878-195">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="f5878-195">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="f5878-196">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="f5878-196">ASP.NET Core 3.0</span></span>

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
