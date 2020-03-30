---
title: ASP.NET Core alterações
titleSuffix: ''
description: Lista as mudanças de quebra no núcleo ASP.NET.
ms.date: 03/27/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 95057425614d7c717154ecfb687db2b9a6ca4a18
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391241"
---
# <a name="aspnet-core-breaking-changes"></a>ASP.NET Core alterações

ASP.NET Core fornece os recursos de desenvolvimento de aplicativos web usados pelo .NET Core.

As seguintes alterações de quebra estão documentadas nesta página:

- [Antiforgery obsoleto, CORS, Diagnósticos, MVC e APIs de roteamento removidos](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [Autenticação: depreciação do Google+:](#authentication-google-deprecated-and-replaced)
- [Autenticação: httpcontext.authentication propriedade removido](#authentication-httpcontextauthentication-property-removed)
- [Autenticação: Tipos Newtonsoft.Json substituídos](#authentication-newtonsoftjson-types-replaced)
- [Autenticação: OAuthHandler ExchangeCodeAsync assinatura alterada](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [Autorização: Adicionar Sobrecarga de autorização movida para diferentes conjuntos](#authorization-addauthorization-overload-moved-to-different-assembly)
- [Autorização: IAllowAnonymous removido do AuthorizationFilterContext.Filters](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [Autorização: Implementações do IAuthorizationPolicyProvider exigem um novo método](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [Azure: pacotes de integração azure prefixados pela Microsoft removidos](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [Cache: CompactOnMemoryPressure propriedade removido](#caching-compactonmemorypressure-property-removed)
- [Cache: Microsoft.Extensions.Caching.SqlServer usa novo pacote SqlClient](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [Cache: ResponseCaching tipos "pubternal" alterados para internos](#caching-responsecaching-pubternal-types-changed-to-internal)
- [Proteção de dados: DataProtection.AzureStorage usa novas APIs de armazenamento do Azure](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [Hospedagem: AspNetCoreModule V1 removido do Pacote de Hospedagem do Windows](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [Hospedagem: Host genérico restringe injeção de construtor de inicialização](#hosting-generic-host-restricts-startup-constructor-injection)
- [Hospedagem: Redirecionamento HTTPS ativado para aplicativos fora de processo do IIS](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [Hospedagem: IHostingAmbiente e iAppLifetime tipos substituídos](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [Hospedagem: ObjectPoolProvider removido das dependências do WebHostBuilder](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [HTTP: O Navegador SameSite altera a autenticação de impacto](#http-browser-samesite-changes-impact-authentication)
- [HTTP: Extensibilidade padrãohttpcontext removido](#http-defaulthttpcontext-extensibility-removed)
- [HTTP: Os campos de cabeçalhonames alterados para leitura estática somente](#http-headernames-constants-changed-to-static-readonly)
- [HTTP: Mudanças na infra-estrutura do corpo de resposta](#http-response-body-infrastructure-changes)
- [HTTP: Alguns valores padrão do Cookie SameSite alterados](#http-some-cookie-samesite-defaults-changed-to-none)
- [HTTP: IO síncrono desativado por padrão](#http-synchronous-io-disabled-in-all-servers)
- [Identidade: Sobrecarga de método AddDefaultUI removida](#identity-adddefaultui-method-overload-removed)
- [Identidade: UI Bootstrap mudança de versão](#identity-default-bootstrap-version-of-ui-changed)
- [Identidade: SignInAsync lança exceção para identidade não autenticada](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [Identidade: O construtor SignInManager aceita novo parâmetro](#identity-signinmanager-constructor-accepts-new-parameter)
- [Identidade: A ui usa o recurso de ativos web estáticos](#identity-ui-uses-static-web-assets-feature)
- [Kestrel: Adaptadores de conexão removidos](#kestrel-connection-adapters-removed)
- [Kestrel: Conjunto HTTPS vazio removido](#kestrel-empty-https-assembly-removed)
- [Kestrel: Solicitar cabeçalhos de trailer movidos para nova coleção](#kestrel-request-trailer-headers-moved-to-new-collection)
- [Kestrel: Alterações na camada de abstração de transporte](#kestrel-transport-abstractions-removed-and-made-public)
- [Localização: APIs marcadas como obsoletas](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [Registro: Classe DebugLogger feita internamente](#logging-debuglogger-class-made-internal)
- [MVC: Sufixo de ação do controlador Async removido](#mvc-async-suffix-trimmed-from-controller-action-names)
- [MVC: JsonResult mudou-se para Microsoft.AspNetCore.Mvc.Core](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [MVC: Ferramenta de pré-compilação depreciada](#mvc-precompilation-tool-deprecated)
- [MVC: Tipos alterados para internos](#mvc-pubternal-types-changed-to-internal)
- [MVC: Shim de compatibilidade da API web removido](#mvc-web-api-compatibility-shim-removed)
- [Razor: Compilação runtime mudou-se para um pacote](#razor-runtime-compilation-moved-to-a-package)
- [Estado da sessão: APIs obsoletas removidas](#session-state-obsolete-apis-removed)
- [Estrutura compartilhada: Remoção de montagem do Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [Estrutura compartilhada: Microsoft.AspNetCore.Todos removidos](#shared-framework-removed-microsoftaspnetcoreall)
- [SignalR: HandshakeProtocol.SuccessHandshakeData substituído](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [SignalR: Métodos de hubConexão removidos](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [SignalR: Os construtores do HubConnectionContext mudaram](#signalr-hubconnectioncontext-constructors-changed)
- [SignalR: Alteração do nome do pacote do cliente JavaScript](#signalr-javascript-client-package-name-changed)
- [SignalR: MessagePack Hub Protocol mudou para o pacote MessagePack 2.x](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [Sinalizador: APIs obsoletas](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [SignalR: UseSignalR e UseConnections métodos removidos](#signalr-usesignalr-and-useconnections-methods-removed)
- [SPAs: SpaServices e NodeServices console logger recuo de forma padrão](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [SPAs: SpaServices e NodeServices marcados como obsoletos](#spas-spaservices-and-nodeservices-marked-obsolete)
- [Arquivos estáticos: tipo de conteúdo CSV alterado para compatível com padrões](#static-files-csv-content-type-changed-to-standards-compliant)
- [Estrutura de destino: .NET Framework não suportado](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a>núcleo ASP.NET 5.0

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a>núcleo de ASP.NET 3.1

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a>núcleo de ASP.NET 3.0

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
