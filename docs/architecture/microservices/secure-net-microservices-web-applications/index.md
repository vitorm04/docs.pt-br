---
title: Protegendo microsserviços e aplicativos Web .NET
description: Segurança nos Microsserviços do .NET e aplicativos Web – Conheça as opções de autenticação em aplicativos Web ASP.NET Core.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 0ac2591f8650e9f8cf29560735a9ec803d29ee4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628326"
---
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="7d241-103">Proteger microsserviços .NET e aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="7d241-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="7d241-104">Há muitos aspectos sobre segurança em microsserviços e aplicativos Web que o tópico poderia ter facilmente vários livros como este. Portanto, nesta seção, vamos nos concentrar na autenticação, na autorização e nos segredos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7d241-104">There are so many aspects about security in microservices and web applications that the topic could easy take several books like this one so, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="7d241-105">Implementar a autenticação em microsserviços .NET e aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="7d241-105">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="7d241-106">Geralmente é necessário que os recursos e as APIs publicados por um serviço sejam limitados a determinados usuários ou clientes confiáveis.</span><span class="sxs-lookup"><span data-stu-id="7d241-106">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="7d241-107">A primeira etapa para tomar esses tipos de decisões de confiança no nível da API é a autenticação.</span><span class="sxs-lookup"><span data-stu-id="7d241-107">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="7d241-108">Autenticação é o processo de confirmar a identidade do usuário de forma confiável.</span><span class="sxs-lookup"><span data-stu-id="7d241-108">Authentication is the process of reliably verify a user’s identity.</span></span>

<span data-ttu-id="7d241-109">Em cenários de microsserviço, a autenticação é normalmente feita de forma centralizada.</span><span class="sxs-lookup"><span data-stu-id="7d241-109">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="7d241-110">Se você estiver usando um Gateway de API, o gateway será um bom lugar para fazer a autenticação, conforme é mostrado na Figura 9-1.</span><span class="sxs-lookup"><span data-stu-id="7d241-110">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="7d241-111">Se você usar esta abordagem, verifique se os microsserviços individuais não podem ser acessados diretamente (sem o Gateway de API), a não ser que haja uma segurança adicional em vigor para autenticar mensagens que entram ou não pelo gateway.</span><span class="sxs-lookup"><span data-stu-id="7d241-111">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![Diagrama mostrando como o aplicativo móvel do cliente interage com o backend.](./media/index/api-gateway-centralized-authentication.png)

<span data-ttu-id="7d241-113">**Figura 9-1**.</span><span class="sxs-lookup"><span data-stu-id="7d241-113">**Figure 9-1**.</span></span> <span data-ttu-id="7d241-114">Autenticação centralizada com um Gateway de API</span><span class="sxs-lookup"><span data-stu-id="7d241-114">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="7d241-115">Quando o Gateway de API centraliza a autenticação, ele adiciona informações do usuário ao encaminhar solicitações para os microsserviços.</span><span class="sxs-lookup"><span data-stu-id="7d241-115">When the API Gateway centralizes authentication, it adds user information when forwarding requests to the microservices.</span></span> <span data-ttu-id="7d241-116">Se os serviços puderem ser acessados diretamente, um serviço de autenticação, como o Azure Active Directory ou um microsserviço de autenticação dedicado atuando como um serviço de token de segurança (STS), poderá ser usado para autenticar os usuários.</span><span class="sxs-lookup"><span data-stu-id="7d241-116">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="7d241-117">As decisões de confiança são compartilhadas entre os serviços com tokens de segurança ou cookies.</span><span class="sxs-lookup"><span data-stu-id="7d241-117">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="7d241-118">(Esses tokens podem ser compartilhados entre ASP.NET aplicativos Core, se necessário, implementando [o compartilhamento de cookies](/aspnet/core/security/cookie-sharing).) Este padrão é ilustrado na Figura 9-2.</span><span class="sxs-lookup"><span data-stu-id="7d241-118">(These tokens can be shared between ASP.NET Core applications, if needed, by implementing [cookie sharing](/aspnet/core/security/cookie-sharing).) This pattern is illustrated in Figure 9-2.</span></span>

![Diagrama mostrando autenticação através de microsserviços backend.](./media/index/identity-microservice-authentication.png)

<span data-ttu-id="7d241-120">**Figura 9-2**.</span><span class="sxs-lookup"><span data-stu-id="7d241-120">**Figure 9-2**.</span></span> <span data-ttu-id="7d241-121">Autenticação por microsserviço de identidade; a confiança é compartilhada usando um token de autorização</span><span class="sxs-lookup"><span data-stu-id="7d241-121">Authentication by identity microservice; trust is shared using an authorization token</span></span>

<span data-ttu-id="7d241-122">Quando os microsserviços são acessados diretamente, a confiança, que inclui autenticação e autorização, é tratada por um token de segurança emitido por um microsserviço dedicado, compartilhado entre os microsserviços.</span><span class="sxs-lookup"><span data-stu-id="7d241-122">When microservices are accessed directly, trust, that includes authentication and authorization, is handled by a security token issued by a dedicated microservice, shared between microservices.</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="7d241-123">Autenticar usando o ASP.NET Core Identity</span><span class="sxs-lookup"><span data-stu-id="7d241-123">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="7d241-124">O mecanismo primário no ASP.NET Core para identificar os usuários de um aplicativo é sistema de associação [ASP.NET Core Identity](/aspnet/core/security/authentication/identity).</span><span class="sxs-lookup"><span data-stu-id="7d241-124">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="7d241-125">A Identidade do ASP.NET Core armazena informações de usuário (incluindo informações de logon, funções e declarações) em um repositório de dados configurado pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="7d241-125">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="7d241-126">Normalmente, o armazenamento de dados do ASP.NET Core Identity é um repositório do Entity Framework fornecido no pacote `Microsoft.AspNetCore.Identity.EntityFrameworkCore`.</span><span class="sxs-lookup"><span data-stu-id="7d241-126">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="7d241-127">No entanto, os repositórios personalizados ou outros pacotes de terceiros podem ser usados para armazenar informações de identidade no Armazenamento de Tabelas do Azure, no CosmosDB ou em outros locais.</span><span class="sxs-lookup"><span data-stu-id="7d241-127">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

> [!TIP]
> <span data-ttu-id="7d241-128">ASP.NET Core 2.1 e posteriormente fornece [ASP.NET Identidade Central](/aspnet/core/security/authentication/identity) como uma Biblioteca de Classe de [Navalha,](/aspnet/core/razor-pages/ui-class)para que você não veja muito do código necessário em seu projeto, como foi o caso das versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="7d241-128">ASP.NET Core 2.1 and later provides [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) as a [Razor Class Library](/aspnet/core/razor-pages/ui-class), so you won't see much of the necessary code in your project, as was the case for previous versions.</span></span> <span data-ttu-id="7d241-129">Para obter detalhes sobre como personalizar o código de identidade para atender às suas necessidades, consulte [Scaffold Identity em projetos ASP.NET Core](/aspnet/core/security/authentication/scaffold-identity).</span><span class="sxs-lookup"><span data-stu-id="7d241-129">For details on how to customize the Identity code to suit your needs, see [Scaffold Identity in ASP.NET Core projects](/aspnet/core/security/authentication/scaffold-identity).</span></span>

<span data-ttu-id="7d241-130">O código a seguir é retirado do modelo de projeto MVC 3.1 do Aplicativo Da Web ASP.NET com autenticação individual da conta de usuário selecionada.</span><span class="sxs-lookup"><span data-stu-id="7d241-130">The following code is taken from the ASP.NET Core Web Application MVC 3.1 project template with individual user account authentication selected.</span></span> <span data-ttu-id="7d241-131">Ele mostra como configurar ASP.NET Identidade Central usando `Startup.ConfigureServices` o Entity Framework Core no método.</span><span class="sxs-lookup"><span data-stu-id="7d241-131">It shows how to configure ASP.NET Core Identity using Entity Framework Core in the `Startup.ConfigureServices` method.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
    //...
}
```

<span data-ttu-id="7d241-132">Uma vez que ASP.NET Identidade Central estiver `app.UseAuthentication()` configurada, você a habilita adicionando o e `endpoints.MapRazorPages()` como mostrado no código a seguir no método do `Startup.Configure` serviço:</span><span class="sxs-lookup"><span data-stu-id="7d241-132">Once ASP.NET Core Identity is configured, you enable it by adding the `app.UseAuthentication()` and `endpoints.MapRazorPages()` as shown in the following code in the service's `Startup.Configure` method:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    //...
    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
    //...
}
```

> [!IMPORTANT]
> <span data-ttu-id="7d241-133">As linhas no código de preceito **devem estar na ordem mostrada** para que a identidade funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="7d241-133">The lines in the preceeding code **MUST BE IN THE ORDER SHOWN** for Identity to work correctly.</span></span>

<span data-ttu-id="7d241-134">Usar o ASP.NET Core Identity permite vários cenários:</span><span class="sxs-lookup"><span data-stu-id="7d241-134">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="7d241-135">Criar informações de novo usuário usando o tipo UserManager (userManager.CreateAsync).</span><span class="sxs-lookup"><span data-stu-id="7d241-135">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="7d241-136">Autenticar usuários usando o tipo SignInManager.</span><span class="sxs-lookup"><span data-stu-id="7d241-136">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="7d241-137">Você pode usar `signInManager.SignInAsync` para entrar diretamente ou `signInManager.PasswordSignInAsync` para confirmar se a senha do usuário está correta e, em seguida, assiná-las.</span><span class="sxs-lookup"><span data-stu-id="7d241-137">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user’s password is correct and then sign them in.</span></span>

- <span data-ttu-id="7d241-138">Identificar um usuário com base nas informações armazenadas em um cookie (que são lidas pelo middleware do ASP.NET Core Identity) para que as próximas solicitações de um navegador incluam a identidade e as declarações do usuário conectado.</span><span class="sxs-lookup"><span data-stu-id="7d241-138">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="7d241-139">O ASP.NET Core Identity também dá suporte à [autenticação de dois fatores](/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="7d241-139">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="7d241-140">Para cenários de autenticação que usam um armazenamento de dados de usuário local e que persistem a identidade entre solicitações usando cookies (como é comum para aplicativos Web MVC), o ASP.NET Core Identity é uma solução recomendada.</span><span class="sxs-lookup"><span data-stu-id="7d241-140">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="7d241-141">Autenticar com provedores externos</span><span class="sxs-lookup"><span data-stu-id="7d241-141">Authenticate with external providers</span></span>

<span data-ttu-id="7d241-142">O ASP.NET Core também dá suporte ao uso de [provedores de autenticação externos](/aspnet/core/security/authentication/social/) para permitir que os usuários entrem por meio de fluxos [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2).</span><span class="sxs-lookup"><span data-stu-id="7d241-142">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="7d241-143">Isso significa que os usuários podem entrar usando os processos de autenticação existentes de provedores como Microsoft, Google, Facebook ou Twitter e associar essas identidades a um ASP.NET Core Identity no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7d241-143">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="7d241-144">Para usar a autenticação externa, além de incluir o `app.UseAuthentication()` middleware de autenticação como `Startup` mencionado anteriormente, usando o método, você também precisa registrar o provedor externo no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="7d241-144">To use external authentication, besides including the authentication middleware as mentioned before, using the `app.UseAuthentication()` method, you also have to register the external provider in `Startup` as shown in the following example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddAuthentication()
        .AddMicrosoftAccount(microsoftOptions =>
        {
            microsoftOptions.ClientId = Configuration["Authentication:Microsoft:ClientId"];
            microsoftOptions.ClientSecret = Configuration["Authentication:Microsoft:ClientSecret"];
        })
        .AddGoogle(googleOptions => { ... })
        .AddTwitter(twitterOptions => { ... })
        .AddFacebook(facebookOptions => { ... });
    //...
}
```

<span data-ttu-id="7d241-145">Os provedores de autenticação externos populares e seus pacotes NuGet associados são mostrados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="7d241-145">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="7d241-146">**Provedor**</span><span class="sxs-lookup"><span data-stu-id="7d241-146">**Provider**</span></span>  | <span data-ttu-id="7d241-147">**Pacote**</span><span class="sxs-lookup"><span data-stu-id="7d241-147">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="7d241-148">**Microsoft**</span><span class="sxs-lookup"><span data-stu-id="7d241-148">**Microsoft**</span></span> | <span data-ttu-id="7d241-149">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="7d241-149">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="7d241-150">**Google**</span><span class="sxs-lookup"><span data-stu-id="7d241-150">**Google**</span></span>    | <span data-ttu-id="7d241-151">**Microsoft.AspNetCore.Authentication.Google**</span><span class="sxs-lookup"><span data-stu-id="7d241-151">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="7d241-152">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="7d241-152">**Facebook**</span></span>  | <span data-ttu-id="7d241-153">**Microsoft.AspNetCore.Authentication.Facebook**</span><span class="sxs-lookup"><span data-stu-id="7d241-153">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="7d241-154">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="7d241-154">**Twitter**</span></span>   | <span data-ttu-id="7d241-155">**Microsoft.AspNetCore.Authentication.Twitter**</span><span class="sxs-lookup"><span data-stu-id="7d241-155">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="7d241-156">Em todos os casos, você deve completar um procedimento de registro de solicitação que seja dependente do fornecedor e que geralmente envolva:</span><span class="sxs-lookup"><span data-stu-id="7d241-156">In all cases, you must complete an application registration procedure that is vendor dependent and that usually involves:</span></span>

1. <span data-ttu-id="7d241-157">Obtendo um ID de solicitação do cliente.</span><span class="sxs-lookup"><span data-stu-id="7d241-157">Getting a Client Application ID.</span></span>
2. <span data-ttu-id="7d241-158">Obtendo um segredo de aplicação do cliente.</span><span class="sxs-lookup"><span data-stu-id="7d241-158">Getting a Client Application Secret.</span></span>
3. <span data-ttu-id="7d241-159">Configurando uma URL de redirecionamento, que é tratada pelo middleware de autorização e pelo provedor registrado</span><span class="sxs-lookup"><span data-stu-id="7d241-159">Configuring an redirection URL, that's handled by the authorization middleware and the registered provider</span></span>
4. <span data-ttu-id="7d241-160">Opcionalmente, configurando uma URL de saída de saída para lidar adequadamente com a saída de saída em um cenário de SSO (Single Sign On).</span><span class="sxs-lookup"><span data-stu-id="7d241-160">Optionally, configuring a sign-out URL to properly handle sign out in a Single Sign On (SSO) scenario.</span></span>

<span data-ttu-id="7d241-161">Para obter detalhes sobre a configuração do aplicativo para um provedor externo, consulte a [autenticação do provedor externo na documentação ASP.NET Core](/aspnet/core/security/authentication/social/)).</span><span class="sxs-lookup"><span data-stu-id="7d241-161">For details on configuring your app for an external provider, see the [External provider authentication in the ASP.NET Core documentation](/aspnet/core/security/authentication/social/)).</span></span>

>[!TIP]
><span data-ttu-id="7d241-162">Todos os detalhes são tratados pelo middleware de autorização e serviços mencionados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7d241-162">All details are handled by the authorization middleware and services previously mentioned.</span></span> <span data-ttu-id="7d241-163">Assim, basta escolher a opção de autenticação **da Conta de Usuário Individual** ao criar o projeto de aplicativo web ASP.NET Code no Visual Studio, como mostrado na Figura 9-3, além de registrar os provedores de autenticação mencionados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7d241-163">So, you just have to choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, as shown in Figure 9-3, besides registering the authentication providers previously mentioned.</span></span>

![Captura de tela da caixa de diálogo Novo ASP.NET Do Aplicativo Web Do Núcleo.](./media/index/select-individual-user-account-authentication-option.png)

<span data-ttu-id="7d241-165">**Figura 9-3**.</span><span class="sxs-lookup"><span data-stu-id="7d241-165">**Figure 9-3**.</span></span> <span data-ttu-id="7d241-166">Selecionando a opção Contas de Usuário Individual, para uso de autenticação externa, ao criar um projeto de aplicativo web no Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="7d241-166">Selecting the Individual User Accounts option, for using external authentication, when creating a web application project in Visual Studio 2019.</span></span>

<span data-ttu-id="7d241-167">Além dos provedores de autenticação externos listados anteriormente, estão disponíveis pacotes de terceiros que fornecem middleware para o uso de vários outros provedores de autenticação externos.</span><span class="sxs-lookup"><span data-stu-id="7d241-167">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="7d241-168">Para obter uma lista, consulte o repositório [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="7d241-168">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repository on GitHub.</span></span>

<span data-ttu-id="7d241-169">Você também pode criar seu próprio middleware de autenticação externa para resolver alguma necessidade especial.</span><span class="sxs-lookup"><span data-stu-id="7d241-169">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="7d241-170">Autenticar com tokens de portador</span><span class="sxs-lookup"><span data-stu-id="7d241-170">Authenticate with bearer tokens</span></span>

<span data-ttu-id="7d241-171">Autenticar com o ASP.NET Core Identity (ou com Identity e também com provedores de autenticação externos) funciona bem para vários cenários de aplicativo Web nos quais é apropriado armazenar informações do usuário em um cookie.</span><span class="sxs-lookup"><span data-stu-id="7d241-171">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="7d241-172">Em outros cenários, no entanto, os cookies não são uma maneira natural de persistir e transmitir dados.</span><span class="sxs-lookup"><span data-stu-id="7d241-172">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="7d241-173">Por exemplo, em uma API Web do ASP.NET Core que expõe pontos de extremidade RESTful que podem ser acessados por SPAs (Aplicativos de Única Página), por clientes nativos ou até mesmo por outras APIs Web, geralmente é melhor usar a autenticação de token de portador.</span><span class="sxs-lookup"><span data-stu-id="7d241-173">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="7d241-174">Esses tipos de aplicativos não funcionam com cookies, mas podem facilmente recuperar um token de portador e incluí-lo no cabeçalho de autorização das próximas solicitações.</span><span class="sxs-lookup"><span data-stu-id="7d241-174">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="7d241-175">Para habilitar a autenticação de token, o ASP.NET Core dá suporte a várias opções para usar [OAuth 2.0](https://oauth.net/2/) e [OpenID Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="7d241-175">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="7d241-176">Autenticar com um provedor de identidade OAuth 2.0 ou OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="7d241-176">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="7d241-177">Se as informações de usuário estiverem armazenadas no Azure Active Directory ou em outra solução de identidade que dê suporte a OpenID Connect ou OAuth 2.0, você poderá usar o pacote **Microsoft.AspNetCore.Authentication.OpenIdConnect** para autenticar usando o fluxo de trabalho do OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="7d241-177">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="7d241-178">Por exemplo, para autenticar no microsserviço Identity.Api em eShopOnContainers, um aplicativo Web do ASP.NET Core pode usar o middleware desse pacote, conforme mostrado no seguinte exemplo simplificado em `Startup.cs`:</span><span class="sxs-lookup"><span data-stu-id="7d241-178">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");
    var sessionCookieLifetime = configuration.GetValue("SessionCookieLifetimeMinutes", 60);

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
    })
    .AddCookie(setup => setup.ExpireTimeSpan = TimeSpan.FromMinutes(sessionCookieLifetime))
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl.ToString();
        options.SignedOutRedirectUri = callBackUrl.ToString();
        options.ClientId = useLoadTest ? "mvctest" : "mvc";
        options.ClientSecret = "secret";
        options.ResponseType = useLoadTest ? "code id_token token" : "code id_token";
        options.SaveTokens = true;
        options.GetClaimsFromUserInfoEndpoint = true;
        options.RequireHttpsMetadata = false;
        options.Scope.Add("openid");
        options.Scope.Add("profile");
        options.Scope.Add("orders");
        options.Scope.Add("basket");
        options.Scope.Add("marketing");
        options.Scope.Add("locations");
        options.Scope.Add("webshoppingagg");
        options.Scope.Add("orders.signalrhub");
    });
}
```

<span data-ttu-id="7d241-179">Observe que quando você usa este fluxo de trabalho, o middleware do ASP.NET Core Identity não é necessário, porque todo o armazenamento de informações de usuário e toda a autenticação são manipulados pelo serviço de identidade.</span><span class="sxs-lookup"><span data-stu-id="7d241-179">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="7d241-180">Emitir tokens de segurança de um serviço do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7d241-180">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="7d241-181">Se preferir emitir tokens de segurança para usuários do ASP.NET Core Identity local em vez de usar um provedor de identidade externo, você poderá usufruir de algumas boas bibliotecas de terceiros.</span><span class="sxs-lookup"><span data-stu-id="7d241-181">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="7d241-182">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) e [OpenIddict](https://github.com/openiddict/openiddict-core) são provedores do OpenID Connect que se integram facilmente ao ASP.NET Core Identity para permitir que você emita tokens de segurança de um serviço do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7d241-182">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="7d241-183">A [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) (Documentação do IdentityServer4) tem instruções detalhadas para usar a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="7d241-183">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="7d241-184">No entanto, as etapas básicas para usar o IdentityServer4 para emitir tokens são as seguintes.</span><span class="sxs-lookup"><span data-stu-id="7d241-184">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="7d241-185">Chame app.UseIdentityServer no método Startup.Configure para adicionar o IdentityServer4 ao pipeline de processamento de solicitação HTTP do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7d241-185">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="7d241-186">Isso permite que a biblioteca atenda solicitações dos pontos de extremidade do OpenID Connect e do OAuth2 como /connect/token.</span><span class="sxs-lookup"><span data-stu-id="7d241-186">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="7d241-187">Você pode configurar o IdentityServer4 no Startup.ConfigureServices fazendo uma chamada para services.AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="7d241-187">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="7d241-188">Configure o servidor de identidade definindo os seguintes dados:</span><span class="sxs-lookup"><span data-stu-id="7d241-188">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="7d241-189">As [credenciais](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) a serem usadas para assinar.</span><span class="sxs-lookup"><span data-stu-id="7d241-189">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="7d241-190">Os [recursos de identidade e da API](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) aos quais os usuários podem solicitar acesso:</span><span class="sxs-lookup"><span data-stu-id="7d241-190">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="7d241-191">Os recursos da API representam dados ou funcionalidades protegidos que o usuário pode acessar com um token de acesso.</span><span class="sxs-lookup"><span data-stu-id="7d241-191">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="7d241-192">Um exemplo de um recurso da API seria uma API Web (ou conjunto de APIs) que exige autorização.</span><span class="sxs-lookup"><span data-stu-id="7d241-192">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="7d241-193">Os recursos de identidade representam informações (declarações) que são concedidas a um cliente para identificar um usuário.</span><span class="sxs-lookup"><span data-stu-id="7d241-193">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="7d241-194">As declarações podem incluir o nome de usuário, o endereço de email e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="7d241-194">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="7d241-195">Os [clientes](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) que se conectarão para solicitar tokens.</span><span class="sxs-lookup"><span data-stu-id="7d241-195">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="7d241-196">O mecanismo de armazenamento de informações do usuário, como o [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) ou um outro.</span><span class="sxs-lookup"><span data-stu-id="7d241-196">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="7d241-197">Ao especificar os clientes e os recursos para o IdentityServer4 usar, você pode passar uma coleção <xref:System.Collections.Generic.IEnumerable%601> do tipo apropriado aos métodos que usam os repositórios de clientes ou de recursos na memória.</span><span class="sxs-lookup"><span data-stu-id="7d241-197">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="7d241-198">Ou, para cenários mais complexos, você pode fornecer os tipos de provedor de clientes ou de recursos por meio de injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="7d241-198">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="7d241-199">Um exemplo de configuração para o IdentityServer4 usar recursos e clientes na memória fornecidos por um tipo IClientStore personalizado pode ser semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="7d241-199">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //...
    services.AddSingleton<IClientStore, CustomClientStore>();
    services.AddIdentityServer()
        .AddSigningCredential("CN=sts")
        .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
        .AddAspNetIdentity<ApplicationUser>();
    //...
}
```

### <a name="consume-security-tokens"></a><span data-ttu-id="7d241-200">Consumir tokens de segurança</span><span class="sxs-lookup"><span data-stu-id="7d241-200">Consume security tokens</span></span>

<span data-ttu-id="7d241-201">Autenticar em relação a um ponto de extremidade do OpenID Connect ou emitir seus próprios tokens de segurança cobre alguns cenários.</span><span class="sxs-lookup"><span data-stu-id="7d241-201">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="7d241-202">Mas, e um serviço que apenas precisa limitar o acesso a esses usuários que têm tokens de segurança válidos que foram fornecidos por um serviço diferente?</span><span class="sxs-lookup"><span data-stu-id="7d241-202">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="7d241-203">Para esse cenário, o middleware de autenticação que manipula os tokens JWT está disponível no pacote **Microsoft.AspNetCore.Authentication.JwtBearer**.</span><span class="sxs-lookup"><span data-stu-id="7d241-203">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="7d241-204">JWT representa "[Token Web JSON](https://tools.ietf.org/html/rfc7519)" e é um formato de token de segurança comum (definido pelo RFC 7519) para comunicação de declarações de segurança.</span><span class="sxs-lookup"><span data-stu-id="7d241-204">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="7d241-205">Um exemplo simplificado de como usar o middleware para consumir esses tokens pode parecer com este fragmento de código, tirado do microsserviço Ordering.API de eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="7d241-205">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;

    }).AddJwtBearer(options =>
    {
        options.Authority = identityUrl;
        options.RequireHttpsMetadata = false;
        options.Audience = "orders";
    });
}
```

<span data-ttu-id="7d241-206">Os parâmetros nesse tipo de uso são:</span><span class="sxs-lookup"><span data-stu-id="7d241-206">The parameters in this usage are:</span></span>

- <span data-ttu-id="7d241-207">`Audience` representa o receptor do token ou do recurso de entrada ao qual o token concede acesso.</span><span class="sxs-lookup"><span data-stu-id="7d241-207">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="7d241-208">Se o valor especificado nesse parâmetro não corresponder ao parâmetro no token, o token será rejeitado.</span><span class="sxs-lookup"><span data-stu-id="7d241-208">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="7d241-209">`Authority` é o endereço do servidor de autenticação que emite o token.</span><span class="sxs-lookup"><span data-stu-id="7d241-209">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="7d241-210">O middleware de portador do JWT usa esse URI para obter a chave pública que pode ser usada para validar a assinatura do token.</span><span class="sxs-lookup"><span data-stu-id="7d241-210">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="7d241-211">O middleware também confirma se o parâmetro `iss` no token corresponde a esse URI.</span><span class="sxs-lookup"><span data-stu-id="7d241-211">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="7d241-212">Outro parâmetro, `RequireHttpsMetadata`, é útil para testes. Defina esse parâmetro como false para poder testar em ambientes nos quais você não tenha certificados.</span><span class="sxs-lookup"><span data-stu-id="7d241-212">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="7d241-213">Em implantações reais, os tokens de portador do JWT sempre devem ser passados apenas por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7d241-213">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="7d241-214">Com este middleware em vigor, os tokens JWT são extraídos automaticamente dos cabeçalhos de autorização.</span><span class="sxs-lookup"><span data-stu-id="7d241-214">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="7d241-215">Eles são desserializados, validados (usando os valores nos parâmetros `Audience` e `Authority`) e armazenados como informações de usuário a serem referenciadas posteriormente por ações de MVC ou filtros de autorização.</span><span class="sxs-lookup"><span data-stu-id="7d241-215">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="7d241-216">O middleware de autenticação de portador do JWT também pode dar suporte a cenários mais avançados, como o uso de um certificado local para validar um token se a autoridade não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="7d241-216">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="7d241-217">Para este cenário, você pode especificar um objeto `TokenValidationParameters` no objeto `JwtBearerOptions`.</span><span class="sxs-lookup"><span data-stu-id="7d241-217">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7d241-218">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="7d241-218">Additional resources</span></span>

- <span data-ttu-id="7d241-219">**Compartilhamento de cookies entre aplicativos** </span><span class="sxs-lookup"><span data-stu-id="7d241-219">**Sharing cookies between applications** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- <span data-ttu-id="7d241-220">**Introdução à Identidade** </span><span class="sxs-lookup"><span data-stu-id="7d241-220">**Introduction to Identity** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="7d241-221">**Rick Anderson. Autenticação de dois fatores com SMS** </span><span class="sxs-lookup"><span data-stu-id="7d241-221">**Rick Anderson. Two-factor authentication with SMS** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="7d241-222">**Habilitando a autenticação usando facebook, Google e outros provedores externos** </span><span class="sxs-lookup"><span data-stu-id="7d241-222">**Enabling authentication using Facebook, Google and other external providers** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="7d241-223">**Michell Anicas. Uma Introdução ao OAuth 2** </span><span class="sxs-lookup"><span data-stu-id="7d241-223">**Michell Anicas. An Introduction to OAuth 2** </span></span>\
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- <span data-ttu-id="7d241-224">**AspNet.Security.OAuth.Providers** (repositório do GitHub para provedores do ASP.NET OAuth) </span><span class="sxs-lookup"><span data-stu-id="7d241-224">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers) </span></span>\
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- <span data-ttu-id="7d241-225">**IdentityServer4. Documentação oficial** </span><span class="sxs-lookup"><span data-stu-id="7d241-225">**IdentityServer4. Official documentation** </span></span>\
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
><span data-ttu-id="7d241-226">[Próximo](../implement-resilient-applications/monitor-app-health.md)
>[anterior](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="7d241-226">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
