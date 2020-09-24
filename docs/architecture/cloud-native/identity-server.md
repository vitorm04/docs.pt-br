---
title: IdentityServer para aplicativos nativos de nuvem
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | IdentityServer
ms.date: 05/13/2020
ms.openlocfilehash: bdf193aac348b54f2ebf5b537beef5d61a1d5a1e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163824"
---
# <a name="identityserver-for-cloud-native-applications"></a><span data-ttu-id="27878-103">IdentityServer para aplicativos nativos de nuvem</span><span class="sxs-lookup"><span data-stu-id="27878-103">IdentityServer for cloud-native applications</span></span>

<span data-ttu-id="27878-104">IdentityServer é um servidor de autenticação de software livre que implementa os padrões do OIDC (OpenID Connect) e do OAuth 2,0 para ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="27878-104">IdentityServer is an open-source authentication server that implements OpenID Connect (OIDC) and OAuth 2.0 standards for ASP.NET Core.</span></span> <span data-ttu-id="27878-105">Ele foi projetado para fornecer uma maneira comum de autenticar solicitações para todos os seus aplicativos, sejam eles Web, nativos, móveis ou pontos de extremidade de API.</span><span class="sxs-lookup"><span data-stu-id="27878-105">It's designed to provide a common way to authenticate requests to all of your applications, whether they're web, native, mobile, or API endpoints.</span></span> <span data-ttu-id="27878-106">O IdentityServer pode ser usado para implementar o SSO (logon único) para vários aplicativos e tipos de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="27878-106">IdentityServer can be used to implement Single Sign-On (SSO) for multiple applications and application types.</span></span> <span data-ttu-id="27878-107">Ele pode ser usado para autenticar usuários reais por meio de formulários de entrada e interfaces de usuário semelhantes, bem como a autenticação baseada em serviço que normalmente envolve a emissão de tokens, a verificação e a renovação sem qualquer interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="27878-107">It can be used to authenticate actual users via sign-in forms and similar user interfaces as well as service-based authentication that typically involves token issuance, verification, and renewal without any user interface.</span></span> <span data-ttu-id="27878-108">O IdentityServer foi projetado para ser uma solução personalizável.</span><span class="sxs-lookup"><span data-stu-id="27878-108">IdentityServer is designed to be a customizable solution.</span></span> <span data-ttu-id="27878-109">Cada instância é normalmente personalizada para atender a uma organização individual e/ou a um conjunto de necessidades de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="27878-109">Each instance is typically customized to suit an individual organization and/or set of applications' needs.</span></span>

## <a name="common-web-app-scenarios"></a><span data-ttu-id="27878-110">Cenários comuns de aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="27878-110">Common web app scenarios</span></span>

<span data-ttu-id="27878-111">Normalmente, os aplicativos precisam dar suporte a alguns ou todos os seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="27878-111">Typically, applications need to support some or all of the following scenarios:</span></span>

- <span data-ttu-id="27878-112">Usuários humanos que acessam aplicativos Web com um navegador.</span><span class="sxs-lookup"><span data-stu-id="27878-112">Human users accessing web applications with a browser.</span></span>
- <span data-ttu-id="27878-113">Usuários humanos que acessam APIs Web de back-end de aplicativos baseados em navegador.</span><span class="sxs-lookup"><span data-stu-id="27878-113">Human users accessing back-end Web APIs from browser-based apps.</span></span>
- <span data-ttu-id="27878-114">Usuários humanos em clientes móveis/nativos que acessam APIs Web de back-end.</span><span class="sxs-lookup"><span data-stu-id="27878-114">Human users on mobile/native clients accessing back-end Web APIs.</span></span>
- <span data-ttu-id="27878-115">Outros aplicativos que acessam APIs Web de back-end (sem uma interface do usuário ou usuário ativo).</span><span class="sxs-lookup"><span data-stu-id="27878-115">Other applications accessing back-end Web APIs (without an active user or user interface).</span></span>
- <span data-ttu-id="27878-116">Qualquer aplicativo pode precisar interagir com outras APIs da Web, usando sua própria identidade ou delegando para a identidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="27878-116">Any application may need to interact with other Web APIs, using its own identity or delegating to the user's identity.</span></span>

![Tipos e cenários de aplicativos](./media/application-types.png)

<span data-ttu-id="27878-118">**Figura 8-1**.</span><span class="sxs-lookup"><span data-stu-id="27878-118">**Figure 8-1**.</span></span> <span data-ttu-id="27878-119">Tipos de aplicativos e cenários.</span><span class="sxs-lookup"><span data-stu-id="27878-119">Application types and scenarios.</span></span>

<span data-ttu-id="27878-120">Em cada um desses cenários, a funcionalidade exposta precisa ser protegida contra uso não autorizado.</span><span class="sxs-lookup"><span data-stu-id="27878-120">In each of these scenarios, the exposed functionality needs to be secured against unauthorized use.</span></span> <span data-ttu-id="27878-121">No mínimo, isso normalmente requer a autenticação do usuário ou entidade de segurança que faz uma solicitação para um recurso.</span><span class="sxs-lookup"><span data-stu-id="27878-121">At a minimum, this typically requires authenticating the user or principal making a request for a resource.</span></span> <span data-ttu-id="27878-122">Essa autenticação pode usar um dos vários protocolos comuns, como SAML2p, WS-enalimentado ou OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="27878-122">This authentication may use one of several common protocols such as SAML2p, WS-Fed, or OpenID Connect.</span></span> <span data-ttu-id="27878-123">A comunicação com APIs normalmente usa o protocolo OAuth2 e seu suporte para tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="27878-123">Communicating with APIs typically uses the OAuth2 protocol and its support for security tokens.</span></span> <span data-ttu-id="27878-124">Separar essas preocupações críticas de segurança abrangentes e seus detalhes de implementação dos próprios aplicativos garante a consistência e melhora a segurança e a facilidade de manutenção.</span><span class="sxs-lookup"><span data-stu-id="27878-124">Separating these critical cross-cutting security concerns and their implementation details from the applications themselves ensures consistency and improves security and maintainability.</span></span> <span data-ttu-id="27878-125">Terceirizar essas preocupações com um produto dedicado, como o IdentityServer, ajuda o requisito para cada aplicativo resolver esses problemas em si.</span><span class="sxs-lookup"><span data-stu-id="27878-125">Outsourcing these concerns to a dedicated product like IdentityServer helps the requirement for every application to solve these problems itself.</span></span>

<span data-ttu-id="27878-126">O IdentityServer fornece middleware que é executado em um aplicativo ASP.NET Core e adiciona suporte para OpenID Connect e OAuth2 (consulte [especificações com suporte](https://docs.identityserver.io/en/latest/intro/specs.html)).</span><span class="sxs-lookup"><span data-stu-id="27878-126">IdentityServer provides middleware that runs within an ASP.NET Core application and adds support for OpenID Connect and OAuth2 (see [supported specifications](https://docs.identityserver.io/en/latest/intro/specs.html)).</span></span> <span data-ttu-id="27878-127">As organizações criarão seu próprio aplicativo de ASP.NET Core usando o middleware IdentityServer para atuar como o STS para todos os seus protocolos de segurança baseados em token.</span><span class="sxs-lookup"><span data-stu-id="27878-127">Organizations would create their own ASP.NET Core app using IdentityServer middleware to act as the STS for all of their token-based security protocols.</span></span> <span data-ttu-id="27878-128">O middleware IdentityServer expõe pontos de extremidade para dar suporte à funcionalidade padrão, incluindo:</span><span class="sxs-lookup"><span data-stu-id="27878-128">The IdentityServer middleware exposes endpoints to support standard functionality, including:</span></span>

- <span data-ttu-id="27878-129">Autorizar (autenticar o usuário final)</span><span class="sxs-lookup"><span data-stu-id="27878-129">Authorize (authenticate the end user)</span></span>
- <span data-ttu-id="27878-130">Token (solicitar um token programaticamente)</span><span class="sxs-lookup"><span data-stu-id="27878-130">Token (request a token programmatically)</span></span>
- <span data-ttu-id="27878-131">Descoberta (metadados sobre o servidor)</span><span class="sxs-lookup"><span data-stu-id="27878-131">Discovery (metadata about the server)</span></span>
- <span data-ttu-id="27878-132">Informações do usuário (obter informações do usuário com um token de acesso válido)</span><span class="sxs-lookup"><span data-stu-id="27878-132">User Info (get user information with a valid access token)</span></span>
- <span data-ttu-id="27878-133">Autorização do dispositivo (usada para iniciar a autorização do fluxo do dispositivo)</span><span class="sxs-lookup"><span data-stu-id="27878-133">Device Authorization (used to start device flow authorization)</span></span>
- <span data-ttu-id="27878-134">Introspecção (validação de token)</span><span class="sxs-lookup"><span data-stu-id="27878-134">Introspection (token validation)</span></span>
- <span data-ttu-id="27878-135">Revogação (revogação de token)</span><span class="sxs-lookup"><span data-stu-id="27878-135">Revocation (token revocation)</span></span>
- <span data-ttu-id="27878-136">Encerrar sessão (disparar saída única em todos os aplicativos)</span><span class="sxs-lookup"><span data-stu-id="27878-136">End Session (trigger single sign-out across all apps)</span></span>

## <a name="getting-started"></a><span data-ttu-id="27878-137">Introdução</span><span class="sxs-lookup"><span data-stu-id="27878-137">Getting started</span></span>

<span data-ttu-id="27878-138">O IdentityServer4 é de código-fonte aberto e gratuito para uso.</span><span class="sxs-lookup"><span data-stu-id="27878-138">IdentityServer4 is open-source and free to use.</span></span> <span data-ttu-id="27878-139">Você pode adicioná-lo aos seus aplicativos usando seus pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="27878-139">You can add it to your applications using its NuGet packages.</span></span> <span data-ttu-id="27878-140">O pacote principal é [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) que foi baixado em mais de 4 milhões vezes.</span><span class="sxs-lookup"><span data-stu-id="27878-140">The main package is [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) that has been downloaded over four million times.</span></span> <span data-ttu-id="27878-141">O pacote base não inclui nenhum código de interface do usuário e só dá suporte à configuração da memória.</span><span class="sxs-lookup"><span data-stu-id="27878-141">The base package doesn't include any user interface code and only supports in memory configuration.</span></span> <span data-ttu-id="27878-142">Para usá-lo com um banco de dados, você também desejará um provedor de data como o [IdentityServer4. EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) que usa Entity Framework Core para armazenar a configuração e os dados operacionais do IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="27878-142">To use it with a database, you'll also want a data provider like [IdentityServer4.EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) that uses Entity Framework Core to store configuration and operational data for IdentityServer.</span></span> <span data-ttu-id="27878-143">Para a interface do usuário, você pode copiar arquivos do [repositório de IU de início rápido](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) para seu aplicativo ASP.NET Core MVC para adicionar suporte para entrar e sair usando o middleware IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="27878-143">For user interface, you can copy files from the [Quickstart UI repository](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) into your ASP.NET Core MVC application to add support for sign in and sign out using IdentityServer middleware.</span></span>

## <a name="configuration"></a><span data-ttu-id="27878-144">Configuração</span><span class="sxs-lookup"><span data-stu-id="27878-144">Configuration</span></span>

<span data-ttu-id="27878-145">O IdentityServer dá suporte a diferentes tipos de protocolos e provedores de autenticação social que podem ser configurados como parte de cada instalação personalizada.</span><span class="sxs-lookup"><span data-stu-id="27878-145">IdentityServer supports different kinds of protocols and social authentication providers that can be configured as part of each custom installation.</span></span> <span data-ttu-id="27878-146">Isso normalmente é feito na classe do aplicativo ASP.NET Core `Startup` no `ConfigureServices` método.</span><span class="sxs-lookup"><span data-stu-id="27878-146">This is typically done in the ASP.NET Core application's `Startup` class in the `ConfigureServices` method.</span></span> <span data-ttu-id="27878-147">A configuração envolve especificar os protocolos com suporte e os caminhos para os servidores e pontos de extremidade que serão usados.</span><span class="sxs-lookup"><span data-stu-id="27878-147">The configuration involves specifying the supported protocols and the paths to the servers and endpoints that will be used.</span></span> <span data-ttu-id="27878-148">A Figura 8-2 mostra uma configuração de exemplo obtida do projeto de interface do usuário do IdentityServer4 QuickStart:</span><span class="sxs-lookup"><span data-stu-id="27878-148">Figure 8-2 shows an example configuration taken from the IdentityServer4 Quickstart UI project:</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();

        // some details omitted
        services.AddIdentityServer();

          services.AddAuthentication()
            .AddGoogle("Google", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;

                options.ClientId = "<insert here>";
                options.ClientSecret = "<insert here>";
            })
            .AddOpenIdConnect("demoidsrv", "IdentityServer", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;
                options.SignOutScheme = IdentityServerConstants.SignoutScheme;

                options.Authority = "https://demo.identityserver.io/";
                options.ClientId = "implicit";
                options.ResponseType = "id_token";
                options.SaveTokens = true;
                options.CallbackPath = new PathString("/signin-idsrv");
                options.SignedOutCallbackPath = new PathString("/signout-callback-idsrv");
                options.RemoteSignOutPath = new PathString("/signout-idsrv");

                options.TokenValidationParameters = new TokenValidationParameters
                {
                    NameClaimType = "name",
                    RoleClaimType = "role"
                };
            });
    }
}
```

<span data-ttu-id="27878-149">**Figura 8-2**.</span><span class="sxs-lookup"><span data-stu-id="27878-149">**Figure 8-2**.</span></span> <span data-ttu-id="27878-150">Configurando o IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="27878-150">Configuring IdentityServer.</span></span>

<span data-ttu-id="27878-151">O IdentityServer também hospeda um site de demonstração pública que pode ser usado para testar vários protocolos e configurações.</span><span class="sxs-lookup"><span data-stu-id="27878-151">IdentityServer also hosts a public demo site that can be used to test various protocols and configurations.</span></span> <span data-ttu-id="27878-152">Ele está localizado em [https://demo.identityserver.io/](https://demo.identityserver.io/) e inclui informações sobre como configurar seu comportamento com base no `client_id` fornecido a ele.</span><span class="sxs-lookup"><span data-stu-id="27878-152">It's located at [https://demo.identityserver.io/](https://demo.identityserver.io/) and includes information on how to configure its behavior based on the `client_id` provided to it.</span></span>

## <a name="javascript-clients"></a><span data-ttu-id="27878-153">Clientes JavaScript</span><span class="sxs-lookup"><span data-stu-id="27878-153">JavaScript clients</span></span>

<span data-ttu-id="27878-154">Muitos aplicativos nativos de nuvem aproveitam as APIs do lado do servidor e os aplicativos de página única (SPAs) de cliente avançado no front-end.</span><span class="sxs-lookup"><span data-stu-id="27878-154">Many cloud-native applications leverage server-side APIs and rich client single page applications (SPAs) on the front end.</span></span> <span data-ttu-id="27878-155">O IdentityServer envia um [cliente JavaScript](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) ( `oidc-client.js` ) por meio de NPM que pode ser adicionado ao spas para permitir que eles usem o IdentityServer para entrar, sair e autenticação baseada em token de APIs da Web.</span><span class="sxs-lookup"><span data-stu-id="27878-155">IdentityServer ships a [JavaScript client](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) (`oidc-client.js`) via NPM that can be added to SPAs to enable them to use IdentityServer for sign in, sign out, and token-based authentication of web APIs.</span></span>

## <a name="references"></a><span data-ttu-id="27878-156">Referências</span><span class="sxs-lookup"><span data-stu-id="27878-156">References</span></span>

- [<span data-ttu-id="27878-157">Documentação do IdentityServer</span><span class="sxs-lookup"><span data-stu-id="27878-157">IdentityServer documentation</span></span>](https://docs.identityserver.io/en/latest/)
- [<span data-ttu-id="27878-158">Tipos de aplicativos</span><span class="sxs-lookup"><span data-stu-id="27878-158">Application types</span></span>](/azure/active-directory/develop/app-types)
- [<span data-ttu-id="27878-159">Cliente OIDC do JavaScript</span><span class="sxs-lookup"><span data-stu-id="27878-159">JavaScript OIDC client</span></span>](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html)

>[!div class="step-by-step"]
><span data-ttu-id="27878-160">[Anterior](azure-active-directory.md) 
> [Avançar](security.md)</span><span class="sxs-lookup"><span data-stu-id="27878-160">[Previous](azure-active-directory.md)
[Next](security.md)</span></span>
