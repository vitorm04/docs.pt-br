---
title: Protegendo microsserviços e aplicativos Web .NET
description: Segurança nos Microsserviços do .NET e aplicativos Web – Conheça as opções de autenticação em aplicativos Web ASP.NET Core.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
---
# <a name="make-secure-net-microservices-and-web-applications"></a>Proteger microsserviços .NET e aplicativos Web

Há muitos aspectos sobre segurança em microsserviços e aplicativos Web que o tópico poderia ter facilmente vários livros como este. Portanto, nesta seção, vamos nos concentrar na autenticação, na autorização e nos segredos do aplicativo.

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>Implementar a autenticação em microsserviços .NET e aplicativos Web

Geralmente é necessário que os recursos e as APIs publicados por um serviço sejam limitados a determinados usuários ou clientes confiáveis. A primeira etapa para tomar esses tipos de decisões de confiança no nível da API é a autenticação. Autenticação é o processo de confirmar a identidade do usuário de forma confiável.

Em cenários de microsserviço, normalmente a autenticação é manipulada centralmente. Se você estiver usando um Gateway de API, o gateway será um bom lugar para fazer a autenticação, conforme é mostrado na Figura 9-1. Se você usar esta abordagem, verifique se os microsserviços individuais não podem ser acessados diretamente (sem o Gateway de API), a não ser que haja uma segurança adicional em vigor para autenticar mensagens que entram ou não pelo gateway.

![Quando o Gateway de API centraliza a autenticação, ele adiciona informações do usuário ao encaminhar solicitações para os microsserviços.](./media/image1.png)

**Figura 9-1**. Autenticação centralizada com um Gateway de API

Se os serviços puderem ser acessados diretamente, um serviço de autenticação como o Azure Active Directory ou um microsserviço de autenticação dedicado agindo como um STS (serviço de token de segurança) poderá ser usado para autenticar os usuários. As decisões de confiança são compartilhadas entre os serviços com tokens de segurança ou cookies. (Esses tokens podem ser compartilhados entre aplicativos, se necessário, no ASP.NET Core com [serviços de proteção de dados](/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Esse padrão é ilustrado na Figura 9-2.

![Quando os microsserviços são acessados diretamente, a confiança, que inclui autenticação e autorização, é tratada por um token de segurança emitido por um microsserviço dedicado, compartilhado entre os microsserviços.](./media/image2.png)

**Figura 9-2**. Autenticação por microsserviço de identidade; a confiança é compartilhada usando um token de autorização

### <a name="authenticate-with-aspnet-core-identity"></a>Autenticar usando o ASP.NET Core Identity

O mecanismo primário no ASP.NET Core para identificar os usuários de um aplicativo é sistema de associação [ASP.NET Core Identity](/aspnet/core/security/authentication/identity). O ASP.NET Core Identity armazena as informações do usuário (incluindo informações de logon, funções e declarações) em um armazenamento de dados configurado pelo desenvolvedor. Normalmente, o armazenamento de dados do ASP.NET Core Identity é um repositório do Entity Framework fornecido no pacote `Microsoft.AspNetCore.Identity.EntityFrameworkCore`. No entanto, os repositórios personalizados ou outros pacotes de terceiros podem ser usados para armazenar informações de identidade no Armazenamento de Tabelas do Azure, no CosmosDB ou em outros locais.

O código a seguir foi obtido no modelo de projeto de aplicativo Web do ASP.NET Core com a autenticação de conta de usuário individual selecionada. Ele mostra como configurar o ASP.NET Core Identity usando o EntityFramework.Core no método Startup.ConfigureServices.

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

Após configurar o ASP.NET Core Identity, você pode habilitá-lo chamando app.UseIdentity no método `Startup.Configure` do serviço.

Usar o ASP.NET Core Identity permite vários cenários:

- Criar informações de novo usuário usando o tipo UserManager (userManager.CreateAsync).

- Autenticar usuários usando o tipo SignInManager. Você pode usar `signInManager.SignInAsync` para entrar diretamente ou `signInManager.PasswordSignInAsync` para confirmar se a senha do usuário está correta e, em seguida, assiná-las.

- Identificar um usuário com base nas informações armazenadas em um cookie (que são lidas pelo middleware do ASP.NET Core Identity) para que as próximas solicitações de um navegador incluam a identidade e as declarações do usuário conectado.

O ASP.NET Core Identity também dá suporte à [autenticação de dois fatores](/aspnet/core/security/authentication/2fa).

Para cenários de autenticação que usam um armazenamento de dados de usuário local e que persistem a identidade entre solicitações usando cookies (como é comum para aplicativos Web MVC), o ASP.NET Core Identity é uma solução recomendada.

### <a name="authenticate-with-external-providers"></a>Autenticar com provedores externos

O ASP.NET Core também dá suporte ao uso de [provedores de autenticação externos](/aspnet/core/security/authentication/social/) para permitir que os usuários entrem por meio de fluxos [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2). Isso significa que os usuários podem entrar usando os processos de autenticação existentes de provedores como Microsoft, Google, Facebook ou Twitter e associar essas identidades a um ASP.NET Core Identity no seu aplicativo.

Para usar a autenticação externa, você pode incluir o middleware de autenticação apropriado no pipeline de processamento de solicitação HTTP do aplicativo. Este middleware é responsável por manipular solicitações para retornar as rotas de URI do provedor de autenticação, capturando informações de identidade e disponibilizando-as por meio do método SignInManager.GetExternalLoginInfo.

Os provedores de autenticação externos populares e seus pacotes NuGet associados são mostrados na tabela a seguir:

| **Provedor**  | **Pacote**                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Microsoft.AspNetCore.Authentication.MicrosoftAccount** |
| **Google**    | **Microsoft.AspNetCore.Authentication.Google**           |
| **Facebook**  | **Microsoft.AspNetCore.Authentication.Facebook**         |
| **Twitter**   | **Microsoft.AspNetCore.Authentication.Twitter**          |

Em todos os casos, o middleware é registrado com uma chamada para um método de registro semelhante a `app.Use{ExternalProvider}Authentication` em `Startup.Configure`. Esses métodos de registro usam um objeto de opções que contém uma ID do aplicativo e informações secretas (uma senha, por exemplo), conforme o provedor exigir. Os provedores de autenticação externos requerem que o aplicativo seja registrado [conforme é explicado em [ASP.NET Documentation](/aspnet/core/security/authentication/social/) (documentação do ASP.NET Core)] para que eles possam informar ao usuário qual aplicativo está solicitando acesso à sua identidade.

Depois que o middleware é registrado em `Startup.Configure`, você pode solicitar que os usuários entrem usando qualquer ação do controlador. Para isso, crie um objeto `AuthenticationProperties` que inclui o nome do provedor de autenticação e uma URL de redirecionamento. Em seguida, você retorna uma resposta de desafio que passa o objeto `AuthenticationProperties`. O código a seguir mostra um exemplo disso.

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

O parâmetro redirectUrl inclui a URL para a qual o provedor externo deverá ser redirecionado quando o usuário for autenticado. A URL deve representar uma ação que conectará o usuário com base nas informações de identidade externas, como no seguinte exemplo simplificado:

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

Se você escolher a opção de autenticação **Conta de Usuário Individual** ao criar o projeto de aplicativo Web do ASP.NET Code no Visual Studio, todo o código necessário para entrar com um provedor externo já estará no projeto, conforme mostrado na Figura 9-3.

![Caixa de diálogo para o novo aplicativo Web do ASP.NET Core, realçando o botão para alterar a autenticação.](./media/image3.png)

**Figura 9-3**. Selecionando uma opção para usar a autenticação externa ao criar um projeto de aplicativo Web

Além dos provedores de autenticação externos listados anteriormente, estão disponíveis pacotes de terceiros que fornecem middleware para o uso de vários outros provedores de autenticação externos. Para obter uma lista, consulte o repositório [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) no GitHub.

Você também pode criar seu próprio middleware de autenticação externa para resolver alguma necessidade especial.

### <a name="authenticate-with-bearer-tokens"></a>Autenticar com tokens de portador

Autenticar com o ASP.NET Core Identity (ou com Identity e também com provedores de autenticação externos) funciona bem para vários cenários de aplicativo Web nos quais é apropriado armazenar informações do usuário em um cookie. Em outros cenários, no entanto, os cookies não são uma maneira natural de persistir e transmitir dados.

Por exemplo, em uma API Web do ASP.NET Core que expõe pontos de extremidade RESTful que podem ser acessados por SPAs (Aplicativos de Única Página), por clientes nativos ou até mesmo por outras APIs Web, geralmente é melhor usar a autenticação de token de portador. Esses tipos de aplicativos não funcionam com cookies, mas podem facilmente recuperar um token de portador e incluí-lo no cabeçalho de autorização das próximas solicitações. Para habilitar a autenticação de token, o ASP.NET Core dá suporte a várias opções para usar [OAuth 2.0](https://oauth.net/2/) e [OpenID Connect](https://openid.net/connect/).

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>Autenticar com um provedor de identidade OAuth 2.0 ou OpenID Connect

Se as informações de usuário estiverem armazenadas no Azure Active Directory ou em outra solução de identidade que dê suporte a OpenID Connect ou OAuth 2.0, você poderá usar o pacote **Microsoft.AspNetCore.Authentication.OpenIdConnect** para autenticar usando o fluxo de trabalho do OpenID Connect. Por exemplo, para autenticar no microsserviço Identity.Api em eShopOnContainers, um aplicativo Web do ASP.NET Core pode usar o middleware desse pacote, conforme mostrado no seguinte exemplo simplificado em `Startup.cs`:

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

Observe que quando você usa este fluxo de trabalho, o middleware do ASP.NET Core Identity não é necessário, porque todo o armazenamento de informações de usuário e toda a autenticação são manipulados pelo serviço de identidade.

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>Emitir tokens de segurança de um serviço do ASP.NET Core

Se preferir emitir tokens de segurança para usuários do ASP.NET Core Identity local em vez de usar um provedor de identidade externo, você poderá usufruir de algumas boas bibliotecas de terceiros.

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) e [OpenIddict](https://github.com/openiddict/openiddict-core) são provedores do OpenID Connect que se integram facilmente ao ASP.NET Core Identity para permitir que você emita tokens de segurança de um serviço do ASP.NET Core. A [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) (Documentação do IdentityServer4) tem instruções detalhadas para usar a biblioteca. No entanto, as etapas básicas para usar o IdentityServer4 para emitir tokens são as seguintes.

1. Chame app.UseIdentityServer no método Startup.Configure para adicionar o IdentityServer4 ao pipeline de processamento de solicitação HTTP do aplicativo. Isso permite que a biblioteca atenda solicitações dos pontos de extremidade do OpenID Connect e do OAuth2 como /connect/token.

2. Você pode configurar o IdentityServer4 no Startup.ConfigureServices fazendo uma chamada para services.AddIdentityServer.

3. Configure o servidor de identidade definindo os seguintes dados:

   - As [credenciais](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) a serem usadas para assinar.

   - Os [recursos de identidade e da API](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) aos quais os usuários podem solicitar acesso:

      - Os recursos da API representam dados ou funcionalidades protegidos que o usuário pode acessar com um token de acesso. Um exemplo de um recurso da API seria uma API Web (ou conjunto de APIs) que exige autorização.

      - Os recursos de identidade representam informações (declarações) que são concedidas a um cliente para identificar um usuário. As declarações podem incluir o nome de usuário, o endereço de email e assim por diante.

   - Os [clientes](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) que se conectarão para solicitar tokens.

   - O mecanismo de armazenamento de informações do usuário, como o [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) ou um outro.

Ao especificar os clientes e os recursos para o IdentityServer4 usar, você pode passar uma coleção <xref:System.Collections.Generic.IEnumerable%601> do tipo apropriado aos métodos que usam os repositórios de clientes ou de recursos na memória. Ou, para cenários mais complexos, você pode fornecer os tipos de provedor de clientes ou de recursos por meio de injeção de dependência.

Um exemplo de configuração para o IdentityServer4 usar recursos e clientes na memória fornecidos por um tipo IClientStore personalizado pode ser semelhante ao exemplo a seguir:

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a>Consumir tokens de segurança

Autenticar em relação a um ponto de extremidade do OpenID Connect ou emitir seus próprios tokens de segurança cobre alguns cenários. Mas, e um serviço que apenas precisa limitar o acesso a esses usuários que têm tokens de segurança válidos que foram fornecidos por um serviço diferente?

Para esse cenário, o middleware de autenticação que manipula os tokens JWT está disponível no pacote **Microsoft.AspNetCore.Authentication.JwtBearer**. JWT representa "[Token Web JSON](https://tools.ietf.org/html/rfc7519)" e é um formato de token de segurança comum (definido pelo RFC 7519) para comunicação de declarações de segurança. Um exemplo simplificado de como usar o middleware para consumir esses tokens pode parecer com este fragmento de código, tirado do microsserviço Ordering.API de eShopOnContainers.

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

Os parâmetros nesse tipo de uso são:

- `Audience` representa o receptor do token ou do recurso de entrada ao qual o token concede acesso. Se o valor especificado nesse parâmetro não corresponder ao parâmetro no token, o token será rejeitado.

- `Authority` é o endereço do servidor de autenticação que emite o token. O middleware de portador do JWT usa esse URI para obter a chave pública que pode ser usada para validar a assinatura do token. O middleware também confirma se o parâmetro `iss` no token corresponde a esse URI.

Outro parâmetro, `RequireHttpsMetadata`, é útil para testes. Defina esse parâmetro como false para poder testar em ambientes nos quais você não tenha certificados. Em implantações reais, os tokens de portador do JWT sempre devem ser passados apenas por HTTPS.

Com este middleware em vigor, os tokens JWT são extraídos automaticamente dos cabeçalhos de autorização. Eles são desserializados, validados (usando os valores nos parâmetros `Audience` e `Authority`) e armazenados como informações de usuário a serem referenciadas posteriormente por ações de MVC ou filtros de autorização.

O middleware de autenticação de portador do JWT também pode dar suporte a cenários mais avançados, como o uso de um certificado local para validar um token se a autoridade não estiver disponível. Para este cenário, você pode especificar um objeto `TokenValidationParameters` no objeto `JwtBearerOptions`.

## <a name="additional-resources"></a>Recursos adicionais

- **Compartilhamento de cookies entre aplicativos** \
  [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)

- **Introdução ao Identity** \
  [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](/aspnet/core/security/authentication/identity)

- **Rick Anderson. Autenticação de dois fatores com SMS** \
  [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](/aspnet/core/security/authentication/2fa)

- **Habilitando a autenticação usando o Facebook, o Google e outros provedores externos** \
  [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](/aspnet/core/security/authentication/social/)

- **Michell Anicas. Uma introdução ao OAuth 2** \
  [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

- **AspNet.Security.OAuth.Providers** (repositório do GitHub para provedores do ASP.NET OAuth.) \
  [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

- **Danny Strockis. Integrando o Azure AD em um aplicativo Web do ASP.NET Core** \
  [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

- **IdentityServer4. Documentação oficial** \
  *<https://identityserver4.readthedocs.io/en/latest/>*

>[!div class="step-by-step"]
>[Anterior](../implement-resilient-applications/monitor-app-health.md)
>[Próximo](authorization-net-microservices-web-applications.md)
