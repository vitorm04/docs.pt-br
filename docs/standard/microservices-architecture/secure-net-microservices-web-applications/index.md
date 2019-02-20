---
title: Protegendo microsserviços e aplicativos Web .NET
description: Segurança nos Microsserviços do .NET e aplicativos Web – Conheça as opções de autenticação em aplicativos Web ASP.NET Core.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
---
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="656d6-103">Proteger microsserviços .NET e aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="656d6-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="656d6-104">Há muitos aspectos sobre segurança em microsserviços e aplicativos Web que o tópico poderia ter facilmente vários livros como este. Portanto, nesta seção, vamos nos concentrar na autenticação, na autorização e nos segredos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="656d6-104">There are so many aspects about security in microservices and web applications that the topic could easy take several books like this one so, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="656d6-105">Implementar a autenticação em microsserviços .NET e aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="656d6-105">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="656d6-106">Geralmente é necessário que os recursos e as APIs publicados por um serviço sejam limitados a determinados usuários ou clientes confiáveis.</span><span class="sxs-lookup"><span data-stu-id="656d6-106">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="656d6-107">A primeira etapa para tomar esses tipos de decisões de confiança no nível da API é a autenticação.</span><span class="sxs-lookup"><span data-stu-id="656d6-107">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="656d6-108">Autenticação é o processo de confirmar a identidade do usuário de forma confiável.</span><span class="sxs-lookup"><span data-stu-id="656d6-108">Authentication is the process of reliably verify a user’s identity.</span></span>

<span data-ttu-id="656d6-109">Em cenários de microsserviço, normalmente a autenticação é manipulada centralmente.</span><span class="sxs-lookup"><span data-stu-id="656d6-109">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="656d6-110">Se você estiver usando um Gateway de API, o gateway será um bom lugar para fazer a autenticação, conforme é mostrado na Figura 9-1.</span><span class="sxs-lookup"><span data-stu-id="656d6-110">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="656d6-111">Se você usar esta abordagem, verifique se os microsserviços individuais não podem ser acessados diretamente (sem o Gateway de API), a não ser que haja uma segurança adicional em vigor para autenticar mensagens que entram ou não pelo gateway.</span><span class="sxs-lookup"><span data-stu-id="656d6-111">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![Quando o Gateway de API centraliza a autenticação, ele adiciona informações do usuário ao encaminhar solicitações para os microsserviços.](./media/image1.png)

<span data-ttu-id="656d6-113">**Figura 9-1**.</span><span class="sxs-lookup"><span data-stu-id="656d6-113">**Figure 9-1**.</span></span> <span data-ttu-id="656d6-114">Autenticação centralizada com um Gateway de API</span><span class="sxs-lookup"><span data-stu-id="656d6-114">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="656d6-115">Se os serviços puderem ser acessados diretamente, um serviço de autenticação como o Azure Active Directory ou um microsserviço de autenticação dedicado agindo como um STS (serviço de token de segurança) poderá ser usado para autenticar os usuários.</span><span class="sxs-lookup"><span data-stu-id="656d6-115">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="656d6-116">As decisões de confiança são compartilhadas entre os serviços com tokens de segurança ou cookies.</span><span class="sxs-lookup"><span data-stu-id="656d6-116">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="656d6-117">(Esses tokens podem ser compartilhados entre aplicativos, se necessário, no ASP.NET Core com [serviços de proteção de dados](/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Esse padrão é ilustrado na Figura 9-2.</span><span class="sxs-lookup"><span data-stu-id="656d6-117">(These tokens can be shared between applications, if needed, in ASP.NET Core with [data protection services](/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) This pattern is illustrated in Figure 9-2.</span></span>

![Quando os microsserviços são acessados diretamente, a confiança, que inclui autenticação e autorização, é tratada por um token de segurança emitido por um microsserviço dedicado, compartilhado entre os microsserviços.](./media/image2.png)

<span data-ttu-id="656d6-119">**Figura 9-2**.</span><span class="sxs-lookup"><span data-stu-id="656d6-119">**Figure 9-2**.</span></span> <span data-ttu-id="656d6-120">Autenticação por microsserviço de identidade; a confiança é compartilhada usando um token de autorização</span><span class="sxs-lookup"><span data-stu-id="656d6-120">Authentication by identity microservice; trust is shared using an authorization token</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="656d6-121">Autenticar usando o ASP.NET Core Identity</span><span class="sxs-lookup"><span data-stu-id="656d6-121">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="656d6-122">O mecanismo primário no ASP.NET Core para identificar os usuários de um aplicativo é sistema de associação [ASP.NET Core Identity](/aspnet/core/security/authentication/identity).</span><span class="sxs-lookup"><span data-stu-id="656d6-122">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="656d6-123">O ASP.NET Core Identity armazena as informações do usuário (incluindo informações de logon, funções e declarações) em um armazenamento de dados configurado pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="656d6-123">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="656d6-124">Normalmente, o armazenamento de dados do ASP.NET Core Identity é um repositório do Entity Framework fornecido no pacote `Microsoft.AspNetCore.Identity.EntityFrameworkCore`.</span><span class="sxs-lookup"><span data-stu-id="656d6-124">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="656d6-125">No entanto, os repositórios personalizados ou outros pacotes de terceiros podem ser usados para armazenar informações de identidade no Armazenamento de Tabelas do Azure, no CosmosDB ou em outros locais.</span><span class="sxs-lookup"><span data-stu-id="656d6-125">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

<span data-ttu-id="656d6-126">O código a seguir foi obtido no modelo de projeto de aplicativo Web do ASP.NET Core com a autenticação de conta de usuário individual selecionada.</span><span class="sxs-lookup"><span data-stu-id="656d6-126">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="656d6-127">Ele mostra como configurar o ASP.NET Core Identity usando o EntityFramework.Core no método Startup.ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="656d6-127">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="656d6-128">Após configurar o ASP.NET Core Identity, você pode habilitá-lo chamando app.UseIdentity no método `Startup.Configure` do serviço.</span><span class="sxs-lookup"><span data-stu-id="656d6-128">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s `Startup.Configure` method.</span></span>

<span data-ttu-id="656d6-129">Usar o ASP.NET Core Identity permite vários cenários:</span><span class="sxs-lookup"><span data-stu-id="656d6-129">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="656d6-130">Criar informações de novo usuário usando o tipo UserManager (userManager.CreateAsync).</span><span class="sxs-lookup"><span data-stu-id="656d6-130">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="656d6-131">Autenticar usuários usando o tipo SignInManager.</span><span class="sxs-lookup"><span data-stu-id="656d6-131">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="656d6-132">Você pode usar `signInManager.SignInAsync` para entrar diretamente ou `signInManager.PasswordSignInAsync` para confirmar se a senha do usuário está correta e, em seguida, assiná-las.</span><span class="sxs-lookup"><span data-stu-id="656d6-132">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user’s password is correct and then sign them in.</span></span>

- <span data-ttu-id="656d6-133">Identificar um usuário com base nas informações armazenadas em um cookie (que são lidas pelo middleware do ASP.NET Core Identity) para que as próximas solicitações de um navegador incluam a identidade e as declarações do usuário conectado.</span><span class="sxs-lookup"><span data-stu-id="656d6-133">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="656d6-134">O ASP.NET Core Identity também dá suporte à [autenticação de dois fatores](/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="656d6-134">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="656d6-135">Para cenários de autenticação que usam um armazenamento de dados de usuário local e que persistem a identidade entre solicitações usando cookies (como é comum para aplicativos Web MVC), o ASP.NET Core Identity é uma solução recomendada.</span><span class="sxs-lookup"><span data-stu-id="656d6-135">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="656d6-136">Autenticar com provedores externos</span><span class="sxs-lookup"><span data-stu-id="656d6-136">Authenticate with external providers</span></span>

<span data-ttu-id="656d6-137">O ASP.NET Core também dá suporte ao uso de [provedores de autenticação externos](/aspnet/core/security/authentication/social/) para permitir que os usuários entrem por meio de fluxos [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2).</span><span class="sxs-lookup"><span data-stu-id="656d6-137">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="656d6-138">Isso significa que os usuários podem entrar usando os processos de autenticação existentes de provedores como Microsoft, Google, Facebook ou Twitter e associar essas identidades a um ASP.NET Core Identity no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="656d6-138">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="656d6-139">Para usar a autenticação externa, você pode incluir o middleware de autenticação apropriado no pipeline de processamento de solicitação HTTP do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="656d6-139">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="656d6-140">Este middleware é responsável por manipular solicitações para retornar as rotas de URI do provedor de autenticação, capturando informações de identidade e disponibilizando-as por meio do método SignInManager.GetExternalLoginInfo.</span><span class="sxs-lookup"><span data-stu-id="656d6-140">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="656d6-141">Os provedores de autenticação externos populares e seus pacotes NuGet associados são mostrados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="656d6-141">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="656d6-142">**Provedor**</span><span class="sxs-lookup"><span data-stu-id="656d6-142">**Provider**</span></span>  | <span data-ttu-id="656d6-143">**Pacote**</span><span class="sxs-lookup"><span data-stu-id="656d6-143">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="656d6-144">**Microsoft**</span><span class="sxs-lookup"><span data-stu-id="656d6-144">**Microsoft**</span></span> | <span data-ttu-id="656d6-145">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="656d6-145">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="656d6-146">**Google**</span><span class="sxs-lookup"><span data-stu-id="656d6-146">**Google**</span></span>    | <span data-ttu-id="656d6-147">**Microsoft.AspNetCore.Authentication.Google**</span><span class="sxs-lookup"><span data-stu-id="656d6-147">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="656d6-148">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="656d6-148">**Facebook**</span></span>  | <span data-ttu-id="656d6-149">**Microsoft.AspNetCore.Authentication.Facebook**</span><span class="sxs-lookup"><span data-stu-id="656d6-149">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="656d6-150">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="656d6-150">**Twitter**</span></span>   | <span data-ttu-id="656d6-151">**Microsoft.AspNetCore.Authentication.Twitter**</span><span class="sxs-lookup"><span data-stu-id="656d6-151">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="656d6-152">Em todos os casos, o middleware é registrado com uma chamada para um método de registro semelhante a `app.Use{ExternalProvider}Authentication` em `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="656d6-152">In all cases, the middleware is registered with a call to a registration method similar to `app.Use{ExternalProvider}Authentication` in `Startup.Configure`.</span></span> <span data-ttu-id="656d6-153">Esses métodos de registro usam um objeto de opções que contém uma ID do aplicativo e informações secretas (uma senha, por exemplo), conforme o provedor exigir.</span><span class="sxs-lookup"><span data-stu-id="656d6-153">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="656d6-154">Os provedores de autenticação externos requerem que o aplicativo seja registrado [conforme é explicado em [ASP.NET Documentation](/aspnet/core/security/authentication/social/) (documentação do ASP.NET Core)] para que eles possam informar ao usuário qual aplicativo está solicitando acesso à sua identidade.</span><span class="sxs-lookup"><span data-stu-id="656d6-154">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="656d6-155">Depois que o middleware é registrado em `Startup.Configure`, você pode solicitar que os usuários entrem usando qualquer ação do controlador.</span><span class="sxs-lookup"><span data-stu-id="656d6-155">Once the middleware is registered in `Startup.Configure`, you can prompt users to sign in from any controller action.</span></span> <span data-ttu-id="656d6-156">Para isso, crie um objeto `AuthenticationProperties` que inclui o nome do provedor de autenticação e uma URL de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="656d6-156">To do this, you create an `AuthenticationProperties` object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="656d6-157">Em seguida, você retorna uma resposta de desafio que passa o objeto `AuthenticationProperties`.</span><span class="sxs-lookup"><span data-stu-id="656d6-157">You then return a Challenge response that passes the `AuthenticationProperties` object.</span></span> <span data-ttu-id="656d6-158">O código a seguir mostra um exemplo disso.</span><span class="sxs-lookup"><span data-stu-id="656d6-158">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="656d6-159">O parâmetro redirectUrl inclui a URL para a qual o provedor externo deverá ser redirecionado quando o usuário for autenticado.</span><span class="sxs-lookup"><span data-stu-id="656d6-159">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="656d6-160">A URL deve representar uma ação que conectará o usuário com base nas informações de identidade externas, como no seguinte exemplo simplificado:</span><span class="sxs-lookup"><span data-stu-id="656d6-160">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

```csharp
// Sign in the user with this external login provider if the user
// already has a login.
var result = await _signInManager.ExternalLoginSignInAsync(info.LoginProvider, info.ProviderKey, isPersistent: false);

if (result.Succeeded)
{
    return RedirectToLocal(returnUrl);
}
else
{
    ApplicationUser newUser = new ApplicationUser
    {
        // The user object can be constructed with claims from the
        // external authentication provider, combined with information
        // supplied by the user after they have authenticated with
        // the external provider.
        UserName = info.Principal.FindFirstValue(ClaimTypes.Name),
        Email = info.Principal.FindFirstValue(ClaimTypes.Email)
    };
    var identityResult = await _userManager.CreateAsync(newUser);
    if (identityResult.Succeeded)
    {
        identityResult = await _userManager.AddLoginAsync(newUser, info);
        if (identityResult.Succeeded)
        {
            await _signInManager.SignInAsync(newUser, isPersistent: false);
        }
        return RedirectToLocal(returnUrl);
    }
}
```

<span data-ttu-id="656d6-161">Se você escolher a opção de autenticação **Conta de Usuário Individual** ao criar o projeto de aplicativo Web do ASP.NET Code no Visual Studio, todo o código necessário para entrar com um provedor externo já estará no projeto, conforme mostrado na Figura 9-3.</span><span class="sxs-lookup"><span data-stu-id="656d6-161">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 9-3.</span></span>

![Caixa de diálogo para o novo aplicativo Web do ASP.NET Core, realçando o botão para alterar a autenticação.](./media/image3.png)

<span data-ttu-id="656d6-163">**Figura 9-3**.</span><span class="sxs-lookup"><span data-stu-id="656d6-163">**Figure 9-3**.</span></span> <span data-ttu-id="656d6-164">Selecionando uma opção para usar a autenticação externa ao criar um projeto de aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="656d6-164">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="656d6-165">Além dos provedores de autenticação externos listados anteriormente, estão disponíveis pacotes de terceiros que fornecem middleware para o uso de vários outros provedores de autenticação externos.</span><span class="sxs-lookup"><span data-stu-id="656d6-165">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="656d6-166">Para obter uma lista, consulte o repositório [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="656d6-166">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="656d6-167">Você também pode criar seu próprio middleware de autenticação externa para resolver alguma necessidade especial.</span><span class="sxs-lookup"><span data-stu-id="656d6-167">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="656d6-168">Autenticar com tokens de portador</span><span class="sxs-lookup"><span data-stu-id="656d6-168">Authenticate with bearer tokens</span></span>

<span data-ttu-id="656d6-169">Autenticar com o ASP.NET Core Identity (ou com Identity e também com provedores de autenticação externos) funciona bem para vários cenários de aplicativo Web nos quais é apropriado armazenar informações do usuário em um cookie.</span><span class="sxs-lookup"><span data-stu-id="656d6-169">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="656d6-170">Em outros cenários, no entanto, os cookies não são uma maneira natural de persistir e transmitir dados.</span><span class="sxs-lookup"><span data-stu-id="656d6-170">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="656d6-171">Por exemplo, em uma API Web do ASP.NET Core que expõe pontos de extremidade RESTful que podem ser acessados por SPAs (Aplicativos de Única Página), por clientes nativos ou até mesmo por outras APIs Web, geralmente é melhor usar a autenticação de token de portador.</span><span class="sxs-lookup"><span data-stu-id="656d6-171">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="656d6-172">Esses tipos de aplicativos não funcionam com cookies, mas podem facilmente recuperar um token de portador e incluí-lo no cabeçalho de autorização das próximas solicitações.</span><span class="sxs-lookup"><span data-stu-id="656d6-172">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="656d6-173">Para habilitar a autenticação de token, o ASP.NET Core dá suporte a várias opções para usar [OAuth 2.0](https://oauth.net/2/) e [OpenID Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="656d6-173">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="656d6-174">Autenticar com um provedor de identidade OAuth 2.0 ou OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="656d6-174">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="656d6-175">Se as informações de usuário estiverem armazenadas no Azure Active Directory ou em outra solução de identidade que dê suporte a OpenID Connect ou OAuth 2.0, você poderá usar o pacote **Microsoft.AspNetCore.Authentication.OpenIdConnect** para autenticar usando o fluxo de trabalho do OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="656d6-175">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="656d6-176">Por exemplo, para autenticar no microsserviço Identity.Api em eShopOnContainers, um aplicativo Web do ASP.NET Core pode usar o middleware desse pacote, conforme mostrado no seguinte exemplo simplificado em `Startup.cs`:</span><span class="sxs-lookup"><span data-stu-id="656d6-176">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseMvc();
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = OpenIdConnectDefaults.AuthenticationScheme;
    })
    .AddCookie()
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl;
        options.SignedOutRedirectUri = callBackUrl;
        options.ClientSecret = "secret";
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

<span data-ttu-id="656d6-177">Observe que quando você usa este fluxo de trabalho, o middleware do ASP.NET Core Identity não é necessário, porque todo o armazenamento de informações de usuário e toda a autenticação são manipulados pelo serviço de identidade.</span><span class="sxs-lookup"><span data-stu-id="656d6-177">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="656d6-178">Emitir tokens de segurança de um serviço do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="656d6-178">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="656d6-179">Se preferir emitir tokens de segurança para usuários do ASP.NET Core Identity local em vez de usar um provedor de identidade externo, você poderá usufruir de algumas boas bibliotecas de terceiros.</span><span class="sxs-lookup"><span data-stu-id="656d6-179">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="656d6-180">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) e [OpenIddict](https://github.com/openiddict/openiddict-core) são provedores do OpenID Connect que se integram facilmente ao ASP.NET Core Identity para permitir que você emita tokens de segurança de um serviço do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="656d6-180">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="656d6-181">A [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) (Documentação do IdentityServer4) tem instruções detalhadas para usar a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="656d6-181">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="656d6-182">No entanto, as etapas básicas para usar o IdentityServer4 para emitir tokens são as seguintes.</span><span class="sxs-lookup"><span data-stu-id="656d6-182">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="656d6-183">Chame app.UseIdentityServer no método Startup.Configure para adicionar o IdentityServer4 ao pipeline de processamento de solicitação HTTP do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="656d6-183">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="656d6-184">Isso permite que a biblioteca atenda solicitações dos pontos de extremidade do OpenID Connect e do OAuth2 como /connect/token.</span><span class="sxs-lookup"><span data-stu-id="656d6-184">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="656d6-185">Você pode configurar o IdentityServer4 no Startup.ConfigureServices fazendo uma chamada para services.AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="656d6-185">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="656d6-186">Configure o servidor de identidade definindo os seguintes dados:</span><span class="sxs-lookup"><span data-stu-id="656d6-186">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="656d6-187">As [credenciais](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) a serem usadas para assinar.</span><span class="sxs-lookup"><span data-stu-id="656d6-187">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="656d6-188">Os [recursos de identidade e da API](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) aos quais os usuários podem solicitar acesso:</span><span class="sxs-lookup"><span data-stu-id="656d6-188">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="656d6-189">Os recursos da API representam dados ou funcionalidades protegidos que o usuário pode acessar com um token de acesso.</span><span class="sxs-lookup"><span data-stu-id="656d6-189">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="656d6-190">Um exemplo de um recurso da API seria uma API Web (ou conjunto de APIs) que exige autorização.</span><span class="sxs-lookup"><span data-stu-id="656d6-190">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="656d6-191">Os recursos de identidade representam informações (declarações) que são concedidas a um cliente para identificar um usuário.</span><span class="sxs-lookup"><span data-stu-id="656d6-191">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="656d6-192">As declarações podem incluir o nome de usuário, o endereço de email e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="656d6-192">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="656d6-193">Os [clientes](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) que se conectarão para solicitar tokens.</span><span class="sxs-lookup"><span data-stu-id="656d6-193">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="656d6-194">O mecanismo de armazenamento de informações do usuário, como o [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) ou um outro.</span><span class="sxs-lookup"><span data-stu-id="656d6-194">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="656d6-195">Ao especificar os clientes e os recursos para o IdentityServer4 usar, você pode passar uma coleção <xref:System.Collections.Generic.IEnumerable%601> do tipo apropriado aos métodos que usam os repositórios de clientes ou de recursos na memória.</span><span class="sxs-lookup"><span data-stu-id="656d6-195">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="656d6-196">Ou, para cenários mais complexos, você pode fornecer os tipos de provedor de clientes ou de recursos por meio de injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="656d6-196">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="656d6-197">Um exemplo de configuração para o IdentityServer4 usar recursos e clientes na memória fornecidos por um tipo IClientStore personalizado pode ser semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="656d6-197">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a><span data-ttu-id="656d6-198">Consumir tokens de segurança</span><span class="sxs-lookup"><span data-stu-id="656d6-198">Consume security tokens</span></span>

<span data-ttu-id="656d6-199">Autenticar em relação a um ponto de extremidade do OpenID Connect ou emitir seus próprios tokens de segurança cobre alguns cenários.</span><span class="sxs-lookup"><span data-stu-id="656d6-199">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="656d6-200">Mas, e um serviço que apenas precisa limitar o acesso a esses usuários que têm tokens de segurança válidos que foram fornecidos por um serviço diferente?</span><span class="sxs-lookup"><span data-stu-id="656d6-200">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="656d6-201">Para esse cenário, o middleware de autenticação que manipula os tokens JWT está disponível no pacote **Microsoft.AspNetCore.Authentication.JwtBearer**.</span><span class="sxs-lookup"><span data-stu-id="656d6-201">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="656d6-202">JWT representa "[Token Web JSON](https://tools.ietf.org/html/rfc7519)" e é um formato de token de segurança comum (definido pelo RFC 7519) para comunicação de declarações de segurança.</span><span class="sxs-lookup"><span data-stu-id="656d6-202">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="656d6-203">Um exemplo simplificado de como usar o middleware para consumir esses tokens pode parecer com este fragmento de código, tirado do microsserviço Ordering.API de eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="656d6-203">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseMvc();
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

    }).AddJwtBearer(options =>
    {
        options.Authority = identityUrl;
        options.RequireHttpsMetadata = false;
        options.Audience = "orders";
    });
}
```

<span data-ttu-id="656d6-204">Os parâmetros nesse tipo de uso são:</span><span class="sxs-lookup"><span data-stu-id="656d6-204">The parameters in this usage are:</span></span>

- <span data-ttu-id="656d6-205">`Audience` representa o receptor do token ou do recurso de entrada ao qual o token concede acesso.</span><span class="sxs-lookup"><span data-stu-id="656d6-205">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="656d6-206">Se o valor especificado nesse parâmetro não corresponder ao parâmetro no token, o token será rejeitado.</span><span class="sxs-lookup"><span data-stu-id="656d6-206">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="656d6-207">`Authority` é o endereço do servidor de autenticação que emite o token.</span><span class="sxs-lookup"><span data-stu-id="656d6-207">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="656d6-208">O middleware de portador do JWT usa esse URI para obter a chave pública que pode ser usada para validar a assinatura do token.</span><span class="sxs-lookup"><span data-stu-id="656d6-208">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="656d6-209">O middleware também confirma se o parâmetro `iss` no token corresponde a esse URI.</span><span class="sxs-lookup"><span data-stu-id="656d6-209">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="656d6-210">Outro parâmetro, `RequireHttpsMetadata`, é útil para testes. Defina esse parâmetro como false para poder testar em ambientes nos quais você não tenha certificados.</span><span class="sxs-lookup"><span data-stu-id="656d6-210">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="656d6-211">Em implantações reais, os tokens de portador do JWT sempre devem ser passados apenas por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="656d6-211">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="656d6-212">Com este middleware em vigor, os tokens JWT são extraídos automaticamente dos cabeçalhos de autorização.</span><span class="sxs-lookup"><span data-stu-id="656d6-212">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="656d6-213">Eles são desserializados, validados (usando os valores nos parâmetros `Audience` e `Authority`) e armazenados como informações de usuário a serem referenciadas posteriormente por ações de MVC ou filtros de autorização.</span><span class="sxs-lookup"><span data-stu-id="656d6-213">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="656d6-214">O middleware de autenticação de portador do JWT também pode dar suporte a cenários mais avançados, como o uso de um certificado local para validar um token se a autoridade não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="656d6-214">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="656d6-215">Para este cenário, você pode especificar um objeto `TokenValidationParameters` no objeto `JwtBearerOptions`.</span><span class="sxs-lookup"><span data-stu-id="656d6-215">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="656d6-216">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="656d6-216">Additional resources</span></span>

- <span data-ttu-id="656d6-217">**Compartilhamento de cookies entre aplicativos** \\</span><span class="sxs-lookup"><span data-stu-id="656d6-217">**Sharing cookies between applications** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)

- <span data-ttu-id="656d6-218">**Introdução ao Identity** \\</span><span class="sxs-lookup"><span data-stu-id="656d6-218">**Introduction to Identity** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="656d6-219">**Rick Anderson. Autenticação de dois fatores com SMS** \\</span><span class="sxs-lookup"><span data-stu-id="656d6-219">**Rick Anderson. Two-factor authentication with SMS** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="656d6-220">**Habilitando a autenticação usando o Facebook, o Google e outros provedores externos** \\</span><span class="sxs-lookup"><span data-stu-id="656d6-220">**Enabling authentication using Facebook, Google and other external providers** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="656d6-221">**Michell Anicas. Uma introdução ao OAuth 2** \\</span><span class="sxs-lookup"><span data-stu-id="656d6-221">**Michell Anicas. An Introduction to OAuth 2** \\</span></span>
  [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

- <span data-ttu-id="656d6-222">**AspNet.Security.OAuth.Providers** (repositório do GitHub para provedores do ASP.NET OAuth.)</span><span class="sxs-lookup"><span data-stu-id="656d6-222">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers.</span></span> \
  [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

- <span data-ttu-id="656d6-223">**Danny Strockis. Integrando o Azure AD em um aplicativo Web do ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="656d6-223">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app** \\</span></span>
  [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

- <span data-ttu-id="656d6-224">**IdentityServer4. Documentação oficial** \\</span><span class="sxs-lookup"><span data-stu-id="656d6-224">**IdentityServer4. Official documentation** \\</span></span>
  *<https://identityserver4.readthedocs.io/en/latest/>*

>[!div class="step-by-step"]
><span data-ttu-id="656d6-225">[Anterior](../implement-resilient-applications/monitor-app-health.md)
>[Próximo](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="656d6-225">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
