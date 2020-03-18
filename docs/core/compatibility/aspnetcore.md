---
title: ASP.NET Core alterações
titleSuffix: ''
description: Lista as mudanças de quebra no núcleo ASP.NET.
ms.date: 01/10/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: c54735cd53fb9cb48eb84045791ccc559fe683cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093169"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="c9650-103">ASP.NET Core alterações</span><span class="sxs-lookup"><span data-stu-id="c9650-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="c9650-104">ASP.NET Core fornece os recursos de desenvolvimento de aplicativos web usados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c9650-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="c9650-105">As seguintes alterações de quebra estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="c9650-105">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="c9650-106">HTTP: O Navegador SameSite altera a autenticação de impacto</span><span class="sxs-lookup"><span data-stu-id="c9650-106">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="c9650-107">Antiforgery obsoleto, CORS, Diagnósticos, MVC e APIs de roteamento removidos</span><span class="sxs-lookup"><span data-stu-id="c9650-107">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="c9650-108">Autenticação: depreciação do Google+:</span><span class="sxs-lookup"><span data-stu-id="c9650-108">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="c9650-109">Autenticação: httpcontext.authentication propriedade removido</span><span class="sxs-lookup"><span data-stu-id="c9650-109">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="c9650-110">Autenticação: Tipos Newtonsoft.Json substituídos</span><span class="sxs-lookup"><span data-stu-id="c9650-110">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="c9650-111">Autenticação: OAuthHandler ExchangeCodeAsync assinatura alterada</span><span class="sxs-lookup"><span data-stu-id="c9650-111">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="c9650-112">Autorização: Adicionar Sobrecarga de autorização movida para diferentes conjuntos</span><span class="sxs-lookup"><span data-stu-id="c9650-112">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="c9650-113">Autorização: IAllowAnonymous removido do AuthorizationFilterContext.Filters</span><span class="sxs-lookup"><span data-stu-id="c9650-113">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="c9650-114">Autorização: Implementações do IAuthorizationPolicyProvider exigem um novo método</span><span class="sxs-lookup"><span data-stu-id="c9650-114">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="c9650-115">Cache: CompactOnMemoryPressure propriedade removido</span><span class="sxs-lookup"><span data-stu-id="c9650-115">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="c9650-116">Cache: Microsoft.Extensions.Caching.SqlServer usa novo pacote SqlClient</span><span class="sxs-lookup"><span data-stu-id="c9650-116">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="c9650-117">Cache: ResponseCaching tipos "pubternal" alterados para internos</span><span class="sxs-lookup"><span data-stu-id="c9650-117">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="c9650-118">Proteção de dados: DataProtection.AzureStorage usa novas APIs de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="c9650-118">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="c9650-119">Hospedagem: AspNetCoreModule V1 removido do Pacote de Hospedagem do Windows</span><span class="sxs-lookup"><span data-stu-id="c9650-119">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="c9650-120">Hospedagem: Host genérico restringe injeção de construtor de inicialização</span><span class="sxs-lookup"><span data-stu-id="c9650-120">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="c9650-121">Hospedagem: Redirecionamento HTTPS ativado para aplicativos fora de processo do IIS</span><span class="sxs-lookup"><span data-stu-id="c9650-121">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="c9650-122">Hospedagem: IHostingAmbiente e iAppLifetime tipos substituídos</span><span class="sxs-lookup"><span data-stu-id="c9650-122">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="c9650-123">Hospedagem: ObjectPoolProvider removido das dependências do WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="c9650-123">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="c9650-124">HTTP: Extensibilidade padrãohttpcontext removido</span><span class="sxs-lookup"><span data-stu-id="c9650-124">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="c9650-125">HTTP: Os campos de cabeçalhonames alterados para leitura estática somente</span><span class="sxs-lookup"><span data-stu-id="c9650-125">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="c9650-126">HTTP: Mudanças na infra-estrutura do corpo de resposta</span><span class="sxs-lookup"><span data-stu-id="c9650-126">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="c9650-127">HTTP: Alguns valores padrão do Cookie SameSite alterados</span><span class="sxs-lookup"><span data-stu-id="c9650-127">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="c9650-128">HTTP: IO síncrono desativado por padrão</span><span class="sxs-lookup"><span data-stu-id="c9650-128">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="c9650-129">Identidade: Sobrecarga de método AddDefaultUI removida</span><span class="sxs-lookup"><span data-stu-id="c9650-129">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="c9650-130">Identidade: UI Bootstrap mudança de versão</span><span class="sxs-lookup"><span data-stu-id="c9650-130">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="c9650-131">Identidade: SignInAsync lança exceção para identidade não autenticada</span><span class="sxs-lookup"><span data-stu-id="c9650-131">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="c9650-132">Identidade: O construtor SignInManager aceita novo parâmetro</span><span class="sxs-lookup"><span data-stu-id="c9650-132">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="c9650-133">Identidade: A ui usa o recurso de ativos web estáticos</span><span class="sxs-lookup"><span data-stu-id="c9650-133">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="c9650-134">Kestrel: Adaptadores de conexão removidos</span><span class="sxs-lookup"><span data-stu-id="c9650-134">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="c9650-135">Kestrel: Conjunto HTTPS vazio removido</span><span class="sxs-lookup"><span data-stu-id="c9650-135">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="c9650-136">Kestrel: Solicitar cabeçalhos de trailer movidos para nova coleção</span><span class="sxs-lookup"><span data-stu-id="c9650-136">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="c9650-137">Kestrel: Alterações na camada de abstração de transporte</span><span class="sxs-lookup"><span data-stu-id="c9650-137">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="c9650-138">Localização: APIs marcadas como obsoletas</span><span class="sxs-lookup"><span data-stu-id="c9650-138">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="c9650-139">Registro: Classe DebugLogger feita internamente</span><span class="sxs-lookup"><span data-stu-id="c9650-139">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="c9650-140">MVC: Sufixo de ação do controlador Async removido</span><span class="sxs-lookup"><span data-stu-id="c9650-140">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="c9650-141">MVC: JsonResult mudou-se para Microsoft.AspNetCore.Mvc.Core</span><span class="sxs-lookup"><span data-stu-id="c9650-141">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="c9650-142">MVC: Ferramenta de pré-compilação depreciada</span><span class="sxs-lookup"><span data-stu-id="c9650-142">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="c9650-143">MVC: Tipos alterados para internos</span><span class="sxs-lookup"><span data-stu-id="c9650-143">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="c9650-144">MVC: Shim de compatibilidade da API web removido</span><span class="sxs-lookup"><span data-stu-id="c9650-144">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="c9650-145">Razor: Compilação runtime mudou-se para um pacote</span><span class="sxs-lookup"><span data-stu-id="c9650-145">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="c9650-146">Estado da sessão: APIs obsoletas removidas</span><span class="sxs-lookup"><span data-stu-id="c9650-146">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="c9650-147">Estrutura compartilhada: Remoção de montagem do Microsoft.AspNetCore.App</span><span class="sxs-lookup"><span data-stu-id="c9650-147">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="c9650-148">Estrutura compartilhada: Microsoft.AspNetCore.Todos removidos</span><span class="sxs-lookup"><span data-stu-id="c9650-148">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="c9650-149">SignalR: HandshakeProtocol.SuccessHandshakeData substituído</span><span class="sxs-lookup"><span data-stu-id="c9650-149">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="c9650-150">SignalR: Métodos de hubConexão removidos</span><span class="sxs-lookup"><span data-stu-id="c9650-150">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="c9650-151">SignalR: Os construtores do HubConnectionContext mudaram</span><span class="sxs-lookup"><span data-stu-id="c9650-151">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="c9650-152">SignalR: Alteração do nome do pacote do cliente JavaScript</span><span class="sxs-lookup"><span data-stu-id="c9650-152">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="c9650-153">Sinalizador: APIs obsoletas</span><span class="sxs-lookup"><span data-stu-id="c9650-153">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="c9650-154">SPAs: SpaServices e NodeServices marcados como obsoletos</span><span class="sxs-lookup"><span data-stu-id="c9650-154">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="c9650-155">SPAs: SpaServices e NodeServices console logger recuo de forma padrão</span><span class="sxs-lookup"><span data-stu-id="c9650-155">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="c9650-156">Estrutura de destino: .NET Framework não suportado</span><span class="sxs-lookup"><span data-stu-id="c9650-156">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-31"></a><span data-ttu-id="c9650-157">núcleo de ASP.NET 3.1</span><span class="sxs-lookup"><span data-stu-id="c9650-157">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="c9650-158">núcleo de ASP.NET 3.0</span><span class="sxs-lookup"><span data-stu-id="c9650-158">ASP.NET Core 3.0</span></span>

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
