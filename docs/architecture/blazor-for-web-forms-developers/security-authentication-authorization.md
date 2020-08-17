---
title: 'Segurança: autenticação e autorização no ASP.NET Web Forms e Blazor'
description: Saiba como lidar com autenticação e autorização no ASP.NET Web Forms e Blazor .
author: ardalis
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/11/2019
ms.openlocfilehash: 1cc82b14a940465c26377f9181a2e20b46b0783f
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267812"
---
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-no-locblazor"></a><span data-ttu-id="ff05d-103">Segurança: autenticação e autorização no ASP.NET Web Forms e Blazor</span><span class="sxs-lookup"><span data-stu-id="ff05d-103">Security: Authentication and Authorization in ASP.NET Web Forms and Blazor</span></span>

<span data-ttu-id="ff05d-104">A migração de um aplicativo ASP.NET Web Forms para Blazor quase certamente exigirá a atualização de como a autenticação e a autorização são executadas, supondo que o aplicativo tenha a autenticação configurada.</span><span class="sxs-lookup"><span data-stu-id="ff05d-104">Migrating from an ASP.NET Web Forms application to Blazor will almost certainly require updating how authentication and authorization is performed, assuming the application had authentication configured.</span></span> <span data-ttu-id="ff05d-105">Este capítulo explicará como migrar do modelo de provedor universal do ASP.NET Web Forms (para associação, funções e perfis de usuário) e como trabalhar com ASP.NET Core identidade de Blazor aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ff05d-105">This chapter will cover how to migrate from the ASP.NET Web Forms universal provider model (for membership, roles, and user profiles) and how to work with ASP.NET Core Identity from Blazor apps.</span></span> <span data-ttu-id="ff05d-106">Embora este capítulo aborde as etapas e considerações de alto nível, as etapas e os scripts detalhados podem ser encontrados na documentação referenciada.</span><span class="sxs-lookup"><span data-stu-id="ff05d-106">While this chapter will cover the high level steps and considerations, the detailed steps and scripts may be found in the referenced documentation.</span></span>

## <a name="aspnet-universal-providers"></a><span data-ttu-id="ff05d-107">Provedores universais ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ff05d-107">ASP.NET universal providers</span></span>

<span data-ttu-id="ff05d-108">Desde ASP.NET 2,0, a plataforma de Web Forms ASP.NET tem suporte para um modelo de provedor para uma variedade de recursos, incluindo associação.</span><span class="sxs-lookup"><span data-stu-id="ff05d-108">Since ASP.NET 2.0, the ASP.NET Web Forms platform has supported a provider model for a variety of features, including membership.</span></span> <span data-ttu-id="ff05d-109">O provedor de Associação Universal, junto com o provedor de função opcional, é muito comumente implantado com aplicativos de Web Forms de ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ff05d-109">The universal membership provider, along with the optional role provider, is very commonly deployed with ASP.NET Web Forms applications.</span></span> <span data-ttu-id="ff05d-110">Ele oferece uma maneira robusta e segura de gerenciar a autenticação e a autorização que continuam funcionando bem hoje.</span><span class="sxs-lookup"><span data-stu-id="ff05d-110">It offers a robust and secure way to manage authentication and authorization that continues to work well today.</span></span> <span data-ttu-id="ff05d-111">A oferta mais recente desses provedores universais está disponível como um pacote NuGet, [Microsoft. AspNet. Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).</span><span class="sxs-lookup"><span data-stu-id="ff05d-111">The most recent offering of these universal providers is available as a NuGet package, [Microsoft.AspNet.Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).</span></span>

<span data-ttu-id="ff05d-112">O provedores universais trabalhar com um esquema de banco de dados SQL que inclui tabelas como `aspnet_Applications` ,, `aspnet_Membership` `aspnet_Roles` e `aspnet_Users` .</span><span class="sxs-lookup"><span data-stu-id="ff05d-112">The Universal Providers work with a SQL database schema that includes tables like `aspnet_Applications`, `aspnet_Membership`, `aspnet_Roles`, and `aspnet_Users`.</span></span> <span data-ttu-id="ff05d-113">Quando configurado executando o [ comandoaspnet_regsql.exe](https://docs.microsoft.com/previous-versions/ms229862(v=vs.140)), os provedores instalam tabelas e procedimentos armazenados que fornecem todas as consultas necessárias e os comandos necessários para trabalhar com os dados subjacentes.</span><span class="sxs-lookup"><span data-stu-id="ff05d-113">When configured by running the [aspnet_regsql.exe command](https://docs.microsoft.com/previous-versions/ms229862(v=vs.140)), the providers install tables and stored procedures that provide all of the necessary queries and commands necessary to work with the underlying data.</span></span> <span data-ttu-id="ff05d-114">O esquema de banco de dados e esses procedimentos armazenados não são compatíveis com os sistemas de identidade ASP.NET Identity e ASP.NET Core mais recentes, portanto, os dados existentes devem ser migrados para o novo sistema.</span><span class="sxs-lookup"><span data-stu-id="ff05d-114">The database schema and these stored procedures are not compatible with newer ASP.NET Identity and ASP.NET Core Identity systems, so existing data must be migrated into the new system.</span></span> <span data-ttu-id="ff05d-115">A Figura 1 mostra um esquema de tabela de exemplo configurado para provedores universais.</span><span class="sxs-lookup"><span data-stu-id="ff05d-115">Figure 1 shows an example table schema configured for universal providers.</span></span>

![esquema de provedores universais](./media/security/membership-tables.png)

<span data-ttu-id="ff05d-117">O provedor universal trata usuários, associação, funções e perfis.</span><span class="sxs-lookup"><span data-stu-id="ff05d-117">The universal provider handles users, membership, roles, and profiles.</span></span> <span data-ttu-id="ff05d-118">Os usuários recebem identificadores globais exclusivos e as informações muito básicas (userId, userName) são armazenadas na `aspnet_Users` tabela.</span><span class="sxs-lookup"><span data-stu-id="ff05d-118">Users are assigned globally unique identifiers and very basic information (userId, userName) is stored in the `aspnet_Users` table.</span></span> <span data-ttu-id="ff05d-119">As informações de autenticação, como senha, formato de senha, Salt de senha, contadores de bloqueio e detalhes, etc., são armazenadas na `aspnet_Membership` tabela.</span><span class="sxs-lookup"><span data-stu-id="ff05d-119">Authentication information, such as password, password format, password salt, lockout counters and details, etc. are stored in the `aspnet_Membership` table.</span></span> <span data-ttu-id="ff05d-120">As funções consistem simplesmente em nomes e identificadores exclusivos, que são atribuídos aos usuários por meio da `aspnet_UsersInRoles` tabela de associação, fornecendo uma relação muitos-para-muitos.</span><span class="sxs-lookup"><span data-stu-id="ff05d-120">Roles consist simply of names and unique identifiers, which are assigned to users via the `aspnet_UsersInRoles` association table, providing a many-to-many relationship.</span></span>

<span data-ttu-id="ff05d-121">Se o sistema existente estiver usando funções além da associação, você precisará migrar as contas de usuário, as senhas associadas, as funções e a associação de função em ASP.NET Core identidade.</span><span class="sxs-lookup"><span data-stu-id="ff05d-121">If your existing system is using roles in addition to membership, you will need to migrate the user accounts, the associated passwords, the roles, and the role membership into ASP.NET Core Identity.</span></span> <span data-ttu-id="ff05d-122">Você também precisará atualizar seu código, no qual você está executando verificações de função usando instruções IF para utilizar filtros declarativos, atributos e/ou auxiliares de marca.</span><span class="sxs-lookup"><span data-stu-id="ff05d-122">You will also most likely need to update your code where you're currently performing role checks using if statements to instead leverage declarative filters, attributes, and/or tag helpers.</span></span> <span data-ttu-id="ff05d-123">Analisaremos as considerações de migração com mais detalhes no final deste capítulo.</span><span class="sxs-lookup"><span data-stu-id="ff05d-123">We will review migration considerations in greater detail at the end of this chapter.</span></span>

### <a name="authorization-configuration-in-web-forms"></a><span data-ttu-id="ff05d-124">Configuração de autorização no Web Forms</span><span class="sxs-lookup"><span data-stu-id="ff05d-124">Authorization configuration in Web Forms</span></span>

<span data-ttu-id="ff05d-125">Para configurar o acesso autorizado a determinadas páginas em um aplicativo ASP.NET Web Forms, normalmente você especifica que determinadas páginas ou pastas estão inacessíveis para usuários anônimos.</span><span class="sxs-lookup"><span data-stu-id="ff05d-125">To configure authorized access to certain pages in an ASP.NET Web Forms application, typically you specify that certain pages or folders are inaccessible to anonymous users.</span></span> <span data-ttu-id="ff05d-126">Isso é feito no arquivo de web.config:</span><span class="sxs-lookup"><span data-stu-id="ff05d-126">This is done in the web.config file:</span></span>

```xml
<?xml version="1.0"?>
<configuration>
    <system.web>
      <authentication mode="Forms">
        <forms defaultUrl="~/home.aspx" loginUrl="~/login.aspx"
          slidingExpiration="true" timeout="2880"></forms>
      </authentication>

      <authorization>
        <deny users="?" />
      </authorization>
    </system.web>
</configuration>
```

<span data-ttu-id="ff05d-127">A `authentication` seção de configuração configura a autenticação de formulários para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff05d-127">The `authentication` configuration section sets up forms authentication for the application.</span></span> <span data-ttu-id="ff05d-128">A `authorization` seção é usada para não permitir usuários anônimos para todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff05d-128">The `authorization` section is used to disallow anonymous users for the entire application.</span></span> <span data-ttu-id="ff05d-129">No entanto, você pode fornecer regras de autorização mais granulares em uma base por local, bem como aplicar verificações de autorização baseadas em função.</span><span class="sxs-lookup"><span data-stu-id="ff05d-129">However, you can provide more granular authorization rules on a per-location basis as well as apply role based authorization checks.</span></span>

```xml
<location path="login.aspx">
  <system.web>
    <authorization>
      <allow users="*" />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id="ff05d-130">A configuração acima, quando combinada com a primeira, permitiria que usuários anônimos acessassem a página de logon, substituindo a restrição em todo o site em usuários não autenticados.</span><span class="sxs-lookup"><span data-stu-id="ff05d-130">The above configuration, when combined with the first one, would allow anonymous users to access the login page, overriding the site-wide restriction on non-authenticated users.</span></span>

```xml
<location path="/admin">
  <system.web>
    <authorization>
      <allow roles="Administrators" />
      <deny users="*" />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id="ff05d-131">A configuração acima, quando combinada com as outras, restringe o acesso à `/admin` pasta e a todos os recursos dentro dela para os membros da função "administradores".</span><span class="sxs-lookup"><span data-stu-id="ff05d-131">The above configuration, when combined with the others, restricts access to the `/admin` folder and all resources within it to members of the "Administrators" role.</span></span> <span data-ttu-id="ff05d-132">Isso também pode ser aplicado colocando um arquivo separado `web.config` dentro da `/admin` raiz da pasta.</span><span class="sxs-lookup"><span data-stu-id="ff05d-132">This could also be applied by placing a separate `web.config` file within the `/admin` folder root.</span></span>

### <a name="authorization-code-in-web-forms"></a><span data-ttu-id="ff05d-133">Código de autorização no Web Forms</span><span class="sxs-lookup"><span data-stu-id="ff05d-133">Authorization code in Web Forms</span></span>

<span data-ttu-id="ff05d-134">Além de configurar o acesso usando `web.config` o, você também pode configurar programaticamente o acesso e o comportamento em seu aplicativo Web Forms.</span><span class="sxs-lookup"><span data-stu-id="ff05d-134">In addition to configuring access using `web.config`, you can also programmatically configure access and behavior in your Web Forms application.</span></span> <span data-ttu-id="ff05d-135">Por exemplo, você pode restringir a capacidade de executar determinadas operações ou exibir determinados dados com base na função do usuário.</span><span class="sxs-lookup"><span data-stu-id="ff05d-135">For instance, you can restrict the ability to perform certain operations or view certain data based on the user's role.</span></span>

<span data-ttu-id="ff05d-136">Esse código pode ser usado na lógica codebehind, bem como na própria página:</span><span class="sxs-lookup"><span data-stu-id="ff05d-136">This code can be used both in codebehind logic as well as in the page itself:</span></span>

```html
<% if (HttpContext.Current.User.IsInRole("Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

<span data-ttu-id="ff05d-137">Além de verificar a associação de função de usuário, você também pode determinar se elas são autenticadas (embora geralmente isso seja melhor usando a configuração baseada em local abordada acima).</span><span class="sxs-lookup"><span data-stu-id="ff05d-137">In addition to checking user role membership, you can also determine if they are authenticated (though often this is better done using the location-based configuration covered above).</span></span> <span data-ttu-id="ff05d-138">Veja abaixo um exemplo dessa abordagem.</span><span class="sxs-lookup"><span data-stu-id="ff05d-138">Below is an example of this approach.</span></span>

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    if (!User.Identity.IsAuthenticated)
    {
        FormsAuthentication.RedirectToLoginPage();
    }
    if (!Roles.IsUserInRole(User.Identity.Name, "Administrators"))
    {
        MessageLabel.Text = "Only administrators can view this.";
        SecretPanel.Visible = false;
    }
}
```

<span data-ttu-id="ff05d-139">No código acima, o RBAC (controle de acesso baseado em função) é usado para determinar se determinados elementos da página, como um `SecretPanel` , são visíveis com base na função do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="ff05d-139">In the code above, role-based access control (RBAC) is used to determine whether certain elements of the page, such as a `SecretPanel`, are visible based on the current user's role.</span></span>

<span data-ttu-id="ff05d-140">Normalmente, ASP.NET Web Forms aplicativos configuram a segurança dentro do `web.config` arquivo e, em seguida, adicionam verificações adicionais onde for necessário em `.aspx` páginas e seus `.aspx.cs` arquivos code-behind relacionados.</span><span class="sxs-lookup"><span data-stu-id="ff05d-140">Typically, ASP.NET Web Forms applications configure security within the `web.config` file and then add additional checks where needed in `.aspx` pages and their related `.aspx.cs` codebehind files.</span></span> <span data-ttu-id="ff05d-141">A maioria dos aplicativos aproveita o provedor de Associação Universal, frequentemente com o provedor de função adicional.</span><span class="sxs-lookup"><span data-stu-id="ff05d-141">Most applications leverage the universal membership provider, frequently with the additional role provider.</span></span>

## <a name="aspnet-core-identity"></a><span data-ttu-id="ff05d-142">Identidade do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ff05d-142">ASP.NET Core Identity</span></span>

<span data-ttu-id="ff05d-143">Embora ainda sejam tarefas com autenticação e autorização, a identidade ASP.NET Core usa um conjunto diferente de abstrações e suposições quando comparada aos provedores universais.</span><span class="sxs-lookup"><span data-stu-id="ff05d-143">Although still tasked with authentication and authorization, ASP.NET Core Identity uses a different set of abstractions and assumptions when compared to the universal providers.</span></span> <span data-ttu-id="ff05d-144">Por exemplo, o novo modelo de identidade dá suporte à autenticação de terceiros, permitindo que os usuários se autentiquem usando uma conta de mídia social ou outro provedor de autenticação confiável.</span><span class="sxs-lookup"><span data-stu-id="ff05d-144">For example, the new Identity model supports third party authentication, allowing users to authenticate using a social media account or other trusted authentication provider.</span></span> <span data-ttu-id="ff05d-145">ASP.NET Core identidade dá suporte à interface do usuário para páginas comumente necessárias, como logon, Logout e registro.</span><span class="sxs-lookup"><span data-stu-id="ff05d-145">ASP.NET Core Identity supports UI for commonly needed pages like login, logout, and register.</span></span> <span data-ttu-id="ff05d-146">Ele aproveita EF Core para seu acesso a dados e usa EF Core migrações para gerar o esquema necessário necessário para dar suporte ao seu modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="ff05d-146">It leverages EF Core for its data access, and uses EF Core migrations to generate the necessary schema required to supports its data model.</span></span> <span data-ttu-id="ff05d-147">Esta [introdução à identidade em ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/identity) fornece uma boa visão geral do que está incluído com a identidade ASP.NET Core e como começar a trabalhar com ele.</span><span class="sxs-lookup"><span data-stu-id="ff05d-147">This [introduction to Identity on ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/identity) provides a good overview of what is included with ASP.NET Core Identity and how to get started working with it.</span></span> <span data-ttu-id="ff05d-148">Se você ainda não tiver configurado ASP.NET Core identidade em seu aplicativo e seu banco de dados, ele o ajudará a começar.</span><span class="sxs-lookup"><span data-stu-id="ff05d-148">If you haven't already set up ASP.NET Core Identity in your application and its database, it will help you get started.</span></span>

### <a name="roles-claims-and-policies"></a><span data-ttu-id="ff05d-149">Funções, declarações e políticas</span><span class="sxs-lookup"><span data-stu-id="ff05d-149">Roles, claims, and policies</span></span>

<span data-ttu-id="ff05d-150">Tanto os provedores universais quanto a identidade de ASP.NET Core dão suporte ao conceito de funções.</span><span class="sxs-lookup"><span data-stu-id="ff05d-150">Both the universal providers and ASP.NET Core Identity support the concept of roles.</span></span> <span data-ttu-id="ff05d-151">Você pode criar funções para usuários e atribuir usuários a funções.</span><span class="sxs-lookup"><span data-stu-id="ff05d-151">You can create roles for users and assign users to roles.</span></span> <span data-ttu-id="ff05d-152">Os usuários podem pertencer a qualquer número de funções e você pode verificar a associação de função como parte da sua implementação de autorização.</span><span class="sxs-lookup"><span data-stu-id="ff05d-152">Users can belong to any number of roles, and you can verify role membership as part of your authorization implementation.</span></span>

<span data-ttu-id="ff05d-153">Além das funções, ASP.NET Core identidade dá suporte aos conceitos de declarações e políticas.</span><span class="sxs-lookup"><span data-stu-id="ff05d-153">In addition to roles, ASP.NET Core identity supports the concepts of claims and policies.</span></span> <span data-ttu-id="ff05d-154">Embora uma função deva corresponder especificamente a um conjunto de recursos que um usuário nessa função deve ser capaz de acessar, uma declaração é simplesmente parte da identidade de um usuário.</span><span class="sxs-lookup"><span data-stu-id="ff05d-154">While a role should specifically correspond to a set of resources a user in that role should be able to access, a claim is simply part of a user's identity.</span></span> <span data-ttu-id="ff05d-155">Uma declaração é um par de valor de nome que representa qual é o assunto, não o que o assunto pode fazer.</span><span class="sxs-lookup"><span data-stu-id="ff05d-155">A claim is a name value pair that represents what the subject is, not what the subject can do.</span></span>

<span data-ttu-id="ff05d-156">É possível inspecionar as declarações de um usuário diretamente e determinar com base nesses se um usuário deve receber acesso a um recurso.</span><span class="sxs-lookup"><span data-stu-id="ff05d-156">It is possible to directly inspect a user's claims and determine based on these whether a user should be given access to a resource.</span></span> <span data-ttu-id="ff05d-157">No entanto, essas verificações costumam ser repetitivas e espalhadas em todo o sistema.</span><span class="sxs-lookup"><span data-stu-id="ff05d-157">However, such checks are often repetitive and scattered throughout the system.</span></span> <span data-ttu-id="ff05d-158">Uma abordagem melhor é definir uma *política*.</span><span class="sxs-lookup"><span data-stu-id="ff05d-158">A better approach is to define a *policy*.</span></span>

<span data-ttu-id="ff05d-159">Uma política de autorização consiste em um ou mais requisitos.</span><span class="sxs-lookup"><span data-stu-id="ff05d-159">An authorization policy consists of one or more requirements.</span></span> <span data-ttu-id="ff05d-160">As políticas são registradas como parte da configuração do serviço de autorização no `ConfigureServices` método de `Startup.cs` .</span><span class="sxs-lookup"><span data-stu-id="ff05d-160">Policies are registered as part of the authorization service configuration in the `ConfigureServices` method of `Startup.cs`.</span></span> <span data-ttu-id="ff05d-161">Por exemplo, o trecho de código a seguir configura uma política chamada "CanadiansOnly", que tem o requisito de que o usuário tenha a declaração Country com o valor de "Canada".</span><span class="sxs-lookup"><span data-stu-id="ff05d-161">For example, the following code snippet configures a policy called "CanadiansOnly" which has the requirement that the user have the Country claim with the value of "Canada".</span></span>

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

<span data-ttu-id="ff05d-162">Você pode [aprender mais sobre como criar políticas personalizadas na documentação do](https://docs.microsoft.com/aspnet/core/security/authorization/policies).</span><span class="sxs-lookup"><span data-stu-id="ff05d-162">You can [learn more about how to create custom policies in the documentation](https://docs.microsoft.com/aspnet/core/security/authorization/policies).</span></span>

<span data-ttu-id="ff05d-163">Se você estiver usando políticas ou funções, poderá especificar que uma página específica em seu Blazor aplicativo exija essa função ou política com o `[Authorize]` atributo, aplicada com a `@attribute` diretiva.</span><span class="sxs-lookup"><span data-stu-id="ff05d-163">Whether you're using policies or roles, you can specify that a particular page in your Blazor application require that role or policy with the `[Authorize]` attribute, applied with the `@attribute` directive.</span></span>

<span data-ttu-id="ff05d-164">Exigindo uma função:</span><span class="sxs-lookup"><span data-stu-id="ff05d-164">Requiring a role:</span></span>

```csharp
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="ff05d-165">Exigir que uma política seja satisfeita:</span><span class="sxs-lookup"><span data-stu-id="ff05d-165">Requiring a policy be satisfied:</span></span>

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

<span data-ttu-id="ff05d-166">Se você precisar acessar o estado de autenticação, as funções ou as declarações de um usuário em seu código, há duas maneiras principais de fazer isso.</span><span class="sxs-lookup"><span data-stu-id="ff05d-166">If you need access to a user's authentication state, roles, or claims in your code, there are two primary ways to achieve this.</span></span> <span data-ttu-id="ff05d-167">A primeira é receber o estado de autenticação como um parâmetro em cascata.</span><span class="sxs-lookup"><span data-stu-id="ff05d-167">The first is to receive the authentication state as a cascading parameter.</span></span> <span data-ttu-id="ff05d-168">A segunda é acessar o estado usando um injetado `AuthenticationStateProvider` .</span><span class="sxs-lookup"><span data-stu-id="ff05d-168">The second is to access the state using an injected `AuthenticationStateProvider`.</span></span> <span data-ttu-id="ff05d-169">Os detalhes de cada uma dessas abordagens são descritos na [ Blazor documentação de segurança](https://docs.microsoft.com/aspnet/core/blazor/security/).</span><span class="sxs-lookup"><span data-stu-id="ff05d-169">The details of each of these approaches are described in the [Blazor Security documentation](https://docs.microsoft.com/aspnet/core/blazor/security/).</span></span>

<span data-ttu-id="ff05d-170">O código a seguir mostra como receber o `AuthenticationState` como um parâmetro em cascata:</span><span class="sxs-lookup"><span data-stu-id="ff05d-170">The following code shows how to receive the `AuthenticationState` as a cascading parameter:</span></span>

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

<span data-ttu-id="ff05d-171">Com esse parâmetro em vigor, você pode obter o usuário usando este código:</span><span class="sxs-lookup"><span data-stu-id="ff05d-171">With this parameter in place, you can get the user using this code:</span></span>

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

<span data-ttu-id="ff05d-172">O código a seguir mostra como injetar `AuthenticationStateProvider` :</span><span class="sxs-lookup"><span data-stu-id="ff05d-172">The following code shows how to inject the `AuthenticationStateProvider`:</span></span>

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

<span data-ttu-id="ff05d-173">Com o provedor em vigor, você pode obter acesso ao usuário com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ff05d-173">With the provider in place, you can gain access to the user with the following code:</span></span>

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

<span data-ttu-id="ff05d-174">**Observação:** O `AuthorizeView` componente, abordado mais adiante neste capítulo, fornece uma maneira declarativa de controlar o que um usuário vê em uma página ou componente.</span><span class="sxs-lookup"><span data-stu-id="ff05d-174">**Note:** The `AuthorizeView` component, covered later in this chapter, provides a declarative way to control what a user sees on a page or component.</span></span>

<span data-ttu-id="ff05d-175">Para trabalhar com usuários e declarações (em Blazor aplicativos de servidor), talvez você também precise injetar um `UserManager<T>` (use `IdentityUser` para o padrão), que pode ser usado para enumerar e modificar declarações para um usuário.</span><span class="sxs-lookup"><span data-stu-id="ff05d-175">To work with users and claims (in Blazor Server applications) you may also need to inject a `UserManager<T>` (use `IdentityUser` for default) which you can use to enumerate and modify claims for a user.</span></span> <span data-ttu-id="ff05d-176">Primeiro, insira o tipo e atribua-o a uma propriedade:</span><span class="sxs-lookup"><span data-stu-id="ff05d-176">First inject the type and assign it to a property:</span></span>

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

<span data-ttu-id="ff05d-177">Em seguida, use-o para trabalhar com as declarações do usuário.</span><span class="sxs-lookup"><span data-stu-id="ff05d-177">Then use it to work with the user's claims.</span></span> <span data-ttu-id="ff05d-178">O exemplo a seguir mostra como adicionar e manter uma declaração em um usuário:</span><span class="sxs-lookup"><span data-stu-id="ff05d-178">The following sample shows how to add and persist a claim on a user:</span></span>

```csharp
private async Task AddCountryClaim()
{
    var authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
    var user = authState.User;
    var identityUser = await MyUserManager.FindByNameAsync(user.Identity.Name);

    if (!user.HasClaim(c => c.Type == ClaimTypes.Country))
    {
        // stores the claim in the cookie
        ClaimsIdentity id = new ClaimsIdentity();
        id.AddClaim(new Claim(ClaimTypes.Country, "Canada"));
        user.AddIdentity(id);

        // save the claim in the database
        await MyUserManager.AddClaimAsync(identityUser, new Claim(ClaimTypes.Country, "Canada"));
    }
}
```

<span data-ttu-id="ff05d-179">Se você precisar trabalhar com funções, siga a mesma abordagem.</span><span class="sxs-lookup"><span data-stu-id="ff05d-179">If you need to work with roles, follow the same approach.</span></span> <span data-ttu-id="ff05d-180">Talvez seja necessário injetar um `RoleManager<T>` (usar `IdentityRole` para o tipo padrão) para listar e gerenciar as funções em si.</span><span class="sxs-lookup"><span data-stu-id="ff05d-180">You may need to inject a `RoleManager<T>` (use `IdentityRole` for default type) to list and manage the roles themselves.</span></span>

<span data-ttu-id="ff05d-181">**Observação:** Em Blazor projetos Webassembly, você precisará fornecer APIs de servidor para executar essas operações (em vez de usar `UserManager<T>` ou `RoleManager<T>` diretamente).</span><span class="sxs-lookup"><span data-stu-id="ff05d-181">**Note:** In Blazor WebAssembly projects, you will need to provide server APIs to perform these operations (instead of using `UserManager<T>` or `RoleManager<T>` directly).</span></span> <span data-ttu-id="ff05d-182">Um Blazor aplicativo cliente Webassembly gerenciaria declarações e/ou funções chamando com segurança pontos de extremidade de API expostos para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="ff05d-182">A Blazor WebAssembly client application would manage claims and/or roles by securely calling API endpoints exposed for this purpose.</span></span>

### <a name="migration-guide"></a><span data-ttu-id="ff05d-183">Guia de migração</span><span class="sxs-lookup"><span data-stu-id="ff05d-183">Migration guide</span></span>

<span data-ttu-id="ff05d-184">Migrar do ASP.NET Web Forms e provedores universais para ASP.NET Core identidade requer várias etapas:</span><span class="sxs-lookup"><span data-stu-id="ff05d-184">Migrating from ASP.NET Web Forms and universal providers to ASP.NET Core Identity requires several steps:</span></span>

1. <span data-ttu-id="ff05d-185">Criar ASP.NET Core esquema de banco de dados de identidade no banco de dados de destino</span><span class="sxs-lookup"><span data-stu-id="ff05d-185">Create ASP.NET Core Identity database schema in destination database</span></span>
2. <span data-ttu-id="ff05d-186">Migrar dados do esquema do provedor universal para ASP.NET Core esquema de identidade</span><span class="sxs-lookup"><span data-stu-id="ff05d-186">Migrate data from universal provider schema to ASP.NET Core Identity schema</span></span>
3. <span data-ttu-id="ff05d-187">Migre a configuração de web.config para middleware e serviços, normalmente em `Startup.cs`</span><span class="sxs-lookup"><span data-stu-id="ff05d-187">Migrate configuration from web.config to middleware and services, typically in `Startup.cs`</span></span>
4. <span data-ttu-id="ff05d-188">Atualize páginas individuais usando controles e condicionais para usar auxiliares de marca e novas APIs de identidade.</span><span class="sxs-lookup"><span data-stu-id="ff05d-188">Update individual pages using controls and conditionals to use tag helpers and new identity APIs.</span></span>

<span data-ttu-id="ff05d-189">Cada uma dessas etapas é descrita mais detalhadamente nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="ff05d-189">Each of these steps is described in detail in the following sections.</span></span>

### <a name="creating-the-aspnet-core-identity-schema"></a><span data-ttu-id="ff05d-190">Criando o esquema de identidade ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ff05d-190">Creating the ASP.NET Core Identity schema</span></span>

<span data-ttu-id="ff05d-191">Há várias maneiras de criar a estrutura de tabela necessária usada para ASP.NET Core identidade.</span><span class="sxs-lookup"><span data-stu-id="ff05d-191">There are several ways to create the necessary table structure used for ASP.NET Core Identity.</span></span> <span data-ttu-id="ff05d-192">A mais simples é criar um novo aplicativo Web ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ff05d-192">The simplest is to create a new ASP.NET Core Web application.</span></span> <span data-ttu-id="ff05d-193">Escolha aplicativo Web e, em seguida, altere a autenticação para usar contas de usuário individuais.</span><span class="sxs-lookup"><span data-stu-id="ff05d-193">Choose Web Application and then change Authentication to use Individual User Accounts.</span></span>

![novo projeto com contas de usuário individuais](./media/security/individual-user-accounts.png)

<span data-ttu-id="ff05d-195">Na linha de comando, você pode fazer a mesma coisa executando `dotnet new webapp -au Individual` .</span><span class="sxs-lookup"><span data-stu-id="ff05d-195">From the command line, you can do the same thing by running `dotnet new webapp -au Individual`.</span></span> <span data-ttu-id="ff05d-196">Depois que o aplicativo tiver sido criado, execute-o e registre-se no site.</span><span class="sxs-lookup"><span data-stu-id="ff05d-196">Once the app has been created, run it and register on the site.</span></span> <span data-ttu-id="ff05d-197">Você deve disparar uma página como a mostrada abaixo:</span><span class="sxs-lookup"><span data-stu-id="ff05d-197">You should trigger a page like the one shown below:</span></span>

![página aplicar migrações](./media/security/apply-migrations-page.png)

<span data-ttu-id="ff05d-199">Clique no botão "aplicar migrações" e as tabelas de banco de dados necessárias devem ser criadas para você.</span><span class="sxs-lookup"><span data-stu-id="ff05d-199">Click on the "Apply Migrations" button and the necessary database tables should be created for you.</span></span> <span data-ttu-id="ff05d-200">Além disso, os arquivos de migração devem aparecer em seu projeto, conforme mostrado:</span><span class="sxs-lookup"><span data-stu-id="ff05d-200">In addition, the migration files should appear in your project, as shown:</span></span>

![arquivos de migração](./media/security/migration-files.png)

<span data-ttu-id="ff05d-202">Você pode executar a migração por conta própria, sem executar o aplicativo Web, usando essa ferramenta de linha de comando:</span><span class="sxs-lookup"><span data-stu-id="ff05d-202">You can run the migration yourself, without running the web application, using this command line tool:</span></span>

```powershell
dotnet ef database update
```

<span data-ttu-id="ff05d-203">Se você preferir executar um script para aplicar o novo esquema a um banco de dados existente, poderá gerar script dessas migrações na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ff05d-203">If you would rather run a script to apply the new schema to an existing database, you can script these migrations from the command line.</span></span> <span data-ttu-id="ff05d-204">Execute este comando para gerar o script:</span><span class="sxs-lookup"><span data-stu-id="ff05d-204">Run this command to generate the script:</span></span>

```powershell
dotnet ef migrations script -o auth.sql
```

<span data-ttu-id="ff05d-205">Isso produzirá um script SQL no arquivo de saída `auth.sql` que pode ser executado em qualquer banco de dados que você desejar.</span><span class="sxs-lookup"><span data-stu-id="ff05d-205">This will produce a SQL script in the output file `auth.sql` which can then be run against whatever database you like.</span></span> <span data-ttu-id="ff05d-206">Se você tiver problemas para executar `dotnet ef` comandos, [Verifique se você tem as ferramentas de EF Core instaladas no sistema](https://docs.microsoft.com/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="ff05d-206">If you have any trouble running `dotnet ef` commands, [make sure you have the EF Core tools installed on your system](https://docs.microsoft.com/ef/core/miscellaneous/cli/dotnet).</span></span>

<span data-ttu-id="ff05d-207">Caso você tenha colunas adicionais em suas tabelas de origem, será necessário identificar o melhor local para essas colunas no novo esquema.</span><span class="sxs-lookup"><span data-stu-id="ff05d-207">In the event you have additional columns on your source tables, you will need to identify the best location for these columns in the new schema.</span></span> <span data-ttu-id="ff05d-208">Em geral, as colunas encontradas na `aspnet_Membership` tabela devem ser mapeadas para a `AspNetUsers` tabela.</span><span class="sxs-lookup"><span data-stu-id="ff05d-208">Generally, columns found on the `aspnet_Membership` table should be mapped to the `AspNetUsers` table.</span></span> <span data-ttu-id="ff05d-209">As colunas em `aspnet_Roles` devem ser mapeadas para `AspNetRoles` .</span><span class="sxs-lookup"><span data-stu-id="ff05d-209">Columns on `aspnet_Roles` should be mapped to `AspNetRoles`.</span></span> <span data-ttu-id="ff05d-210">Todas as colunas adicionais na `aspnet_UsersInRoles` tabela seriam adicionadas à `AspNetUserRoles` tabela.</span><span class="sxs-lookup"><span data-stu-id="ff05d-210">Any additional columns on the `aspnet_UsersInRoles` table would be added to the `AspNetUserRoles` table.</span></span>

<span data-ttu-id="ff05d-211">Também vale a pena considerar colocar qualquer coluna adicional em tabelas separadas, para que as migrações futuras não precisem levar em conta essas personalizações do esquema de identidade padrão.</span><span class="sxs-lookup"><span data-stu-id="ff05d-211">It's also worth considering putting any additional columns on separate tables, so that future migrations won't need to take into account such customizations of the default identity schema.</span></span>

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a><span data-ttu-id="ff05d-212">Migrando dados de provedores universais para identidade ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ff05d-212">Migrating data from universal providers to ASP.NET Core Identity</span></span>

<span data-ttu-id="ff05d-213">Quando você tiver o esquema da tabela de destino em vigor, a próxima etapa será migrar seus registros de usuário e função para o novo esquema.</span><span class="sxs-lookup"><span data-stu-id="ff05d-213">Once you have the destination table schema in place, the next step is to migrate your user and role records to the new schema.</span></span> <span data-ttu-id="ff05d-214">Uma lista completa das diferenças de esquema, incluindo quais colunas são mapeadas para quais novas colunas podem ser encontradas [aqui](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span><span class="sxs-lookup"><span data-stu-id="ff05d-214">A complete list of the schema differences, including which columns map to which new columns, can be found [here](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span>

<span data-ttu-id="ff05d-215">Para migrar os usuários da associação às novas tabelas de identidade, você deve [seguir as etapas descritas na documentação do](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span><span class="sxs-lookup"><span data-stu-id="ff05d-215">To migrate your users from membership to the new identity tables, you should [follow the steps described in the documentation](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span> <span data-ttu-id="ff05d-216">Depois de seguir essas etapas e o script fornecido, os usuários precisarão alterar sua senha na próxima vez que fizerem logon.</span><span class="sxs-lookup"><span data-stu-id="ff05d-216">After following these steps and the script provided, your users will need to change their password the next time they log in.</span></span>

<span data-ttu-id="ff05d-217">É possível migrar senhas de usuário, mas o processo é muito mais envolvido.</span><span class="sxs-lookup"><span data-stu-id="ff05d-217">It is possible to migrate user passwords but the process is much more involved.</span></span> <span data-ttu-id="ff05d-218">Exigir que os usuários atualizem suas senhas como parte do processo de migração e incentivando-as a usar senhas novas e exclusivas, provavelmente aumentará a segurança geral do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff05d-218">Requiring users to update their passwords as part of the migration process, and encouraging them to use new, unique passwords, is likely to enhance the overall security of the application.</span></span>

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a><span data-ttu-id="ff05d-219">Migrando configurações de segurança de web.config para Startup.cs</span><span class="sxs-lookup"><span data-stu-id="ff05d-219">Migrating security settings from web.config to Startup.cs</span></span>

<span data-ttu-id="ff05d-220">Conforme observado acima, a associação de ASP.NET e os provedores de função são configurados no arquivo de web.config do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff05d-220">As noted above, ASP.NET membership and role providers are configured in the application's web.config file.</span></span> <span data-ttu-id="ff05d-221">Como os aplicativos ASP.NET Core não estão vinculados ao IIS e usam um sistema separado para configuração, essas configurações devem ser configuradas em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="ff05d-221">Since ASP.NET Core apps are not tied to IIS and use a separate system for configuration, these settings must be configured elsewhere.</span></span> <span data-ttu-id="ff05d-222">Para a maior parte, ASP.NET Core identidade é configurada no `Startup.cs` arquivo.</span><span class="sxs-lookup"><span data-stu-id="ff05d-222">For the most part, ASP.NET Core Identity is configured in the `Startup.cs` file.</span></span> <span data-ttu-id="ff05d-223">Abra o projeto Web que foi criado anteriormente (para gerar o esquema da tabela de identidade) e examine seu `Startup.cs` arquivo.</span><span class="sxs-lookup"><span data-stu-id="ff05d-223">Open the web project that was created earlier (to generate the identity table schema) and review its `Startup.cs` file.</span></span>

<span data-ttu-id="ff05d-224">O método configureservices padrão adiciona suporte para EF Core e identidade:</span><span class="sxs-lookup"><span data-stu-id="ff05d-224">The default ConfigureServices method adds support for EF Core and Identity:</span></span>

```csharp
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
}
```

<span data-ttu-id="ff05d-225">O `AddDefaultIdentity` método de extensão é usado para configurar a identidade para usar o padrão `ApplicationDbContext` e o `IdentityUser` tipo da estrutura.</span><span class="sxs-lookup"><span data-stu-id="ff05d-225">The `AddDefaultIdentity` extension method is used to configure Identity to use the default `ApplicationDbContext` and the framework's `IdentityUser` type.</span></span> <span data-ttu-id="ff05d-226">Se você estiver usando um personalizado `IdentityUser` , certifique-se de especificar seu tipo aqui.</span><span class="sxs-lookup"><span data-stu-id="ff05d-226">If you're using a custom `IdentityUser`, be sure to specify its type here.</span></span> <span data-ttu-id="ff05d-227">Se esses métodos de extensão não estiverem funcionando em seu aplicativo, verifique se você tem as instruções de uso apropriadas e se você tem as referências de pacote NuGet necessárias.</span><span class="sxs-lookup"><span data-stu-id="ff05d-227">If these extension methods aren't working in your application, check that you have the appropriate using statements and that you have the necessary NuGet package references.</span></span> <span data-ttu-id="ff05d-228">Por exemplo, seu projeto deve ter alguma versão dos `Microsoft.AspNetCore.Identity.EntityFrameworkCore` pacotes e `Microsoft.AspNetCore.Identity.UI` referenciados.</span><span class="sxs-lookup"><span data-stu-id="ff05d-228">For example, your project should have some version of the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` and `Microsoft.AspNetCore.Identity.UI` packages referenced.</span></span>

<span data-ttu-id="ff05d-229">Além disso `Startup.cs` , você deve ver o middleware necessário configurado para o site.</span><span class="sxs-lookup"><span data-stu-id="ff05d-229">Also in `Startup.cs` you should see the necessary middleware configured for the site.</span></span> <span data-ttu-id="ff05d-230">Especificamente, `UseAuthentication` e `UseAuthorization` deve ser configurado e no local apropriado.</span><span class="sxs-lookup"><span data-stu-id="ff05d-230">Specifically, `UseAuthentication` and `UseAuthorization` should be set up, and in the proper location.</span></span>

```csharp

// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
        app.UseDatabaseErrorPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
        // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
        app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
}
```

<span data-ttu-id="ff05d-231">ASP.NET Identity não configura o acesso anônimo ou baseado em função a locais do `Startup.cs` .</span><span class="sxs-lookup"><span data-stu-id="ff05d-231">ASP.NET Identity does not configure anonymous or role-based access to locations from `Startup.cs`.</span></span> <span data-ttu-id="ff05d-232">Você precisará migrar quaisquer dados de configuração de autorização específicos do local para filtros no ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ff05d-232">You will need to migrate any location-specific authorization configuration data to filters in ASP.NET Core.</span></span> <span data-ttu-id="ff05d-233">Anote quais pastas e páginas exigirão essas atualizações.</span><span class="sxs-lookup"><span data-stu-id="ff05d-233">Make note of which folders and pages will require such updates.</span></span> <span data-ttu-id="ff05d-234">Você fará essas alterações na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="ff05d-234">You will make these changes in the next section.</span></span>

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a><span data-ttu-id="ff05d-235">Atualizando páginas individuais para usar ASP.NET Core abstrações de identidade</span><span class="sxs-lookup"><span data-stu-id="ff05d-235">Updating individual pages to use ASP.NET Core Identity abstractions</span></span>

<span data-ttu-id="ff05d-236">No aplicativo ASP.NET Web Forms, se você tiver web.config configurações para negar acesso a determinadas páginas ou pastas a usuários anônimos, você migrará esses arquivos simplesmente adicionando o `[Authorize]` atributo a essas páginas:</span><span class="sxs-lookup"><span data-stu-id="ff05d-236">In your ASP.NET Web Forms application, if you had web.config settings to deny access to certain pages or folders to anonymous users, you would migrate these by simply adding the `[Authorize]` attribute to such pages:</span></span>

```razor
@attribute [Authorize]
```

<span data-ttu-id="ff05d-237">Se você tiver mais acesso negado, exceto para os usuários que pertencem a uma determinada função, você migraria da mesma forma adicionando um atributo especificando uma função:</span><span class="sxs-lookup"><span data-stu-id="ff05d-237">If you further had denied access except to those users belonging to a certain role, you would likewise migrate this by adding an attribute specifying a role:</span></span>

```razor
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="ff05d-238">Observe que o `[Authorize]` atributo só funciona em `@page` componentes que são alcançados por meio do Blazor roteador.</span><span class="sxs-lookup"><span data-stu-id="ff05d-238">Note that the `[Authorize]` attribute only works on `@page` components that are reached via the Blazor Router.</span></span> <span data-ttu-id="ff05d-239">O atributo não funciona com componentes filho que, em vez disso, devem usar `AuthorizeView` .</span><span class="sxs-lookup"><span data-stu-id="ff05d-239">The attribute does not work with child components, which should instead use `AuthorizeView`.</span></span>

<span data-ttu-id="ff05d-240">Se você tiver lógica dentro da marcação de página para determinar se um código deve ser exibido para um determinado usuário, você poderá substituí-lo pelo `AuthorizeView` componente.</span><span class="sxs-lookup"><span data-stu-id="ff05d-240">If you have logic within page markup for determining whether to display some code to a certain user, you can replace this with the `AuthorizeView` component.</span></span> <span data-ttu-id="ff05d-241">O [componente AuthorizeView](https://docs.microsoft.com/aspnet/core/blazor/security#authorizeview-component) exibe de forma seletiva a interface do usuário, dependendo se ele está autorizado a vê-la.</span><span class="sxs-lookup"><span data-stu-id="ff05d-241">The [AuthorizeView component](https://docs.microsoft.com/aspnet/core/blazor/security#authorizeview-component) selectively displays UI depending on whether the user is authorized to see it.</span></span> <span data-ttu-id="ff05d-242">Ele também expõe uma `context` variável que pode ser usada para acessar informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="ff05d-242">It also exposes a `context` variable that can be used to access user information.</span></span>

```razor
<AuthorizeView>
    <Authorized>
        <h1>Hello, @context.User.Identity.Name!</h1>
        <p>You can only see this content if you are authenticated.</p>
    </Authorized>
    <NotAuthorized>
        <h1>Authentication Failure!</h1>
        <p>You are not signed in.</p>
    </NotAuthorized>
</AuthorizeView>
```

<span data-ttu-id="ff05d-243">Você pode acessar o estado de autenticação na lógica de procedimento acessando o usuário de um `Task<AuthenticationState` configurado com o `[CascadingParameter]` atributo.</span><span class="sxs-lookup"><span data-stu-id="ff05d-243">You can access authentication state within procedural logic by accessing the user from a `Task<AuthenticationState` configured with the `[CascadingParameter]` attribute.</span></span> <span data-ttu-id="ff05d-244">Isso fará com que você tenha acesso ao usuário, o que pode permitir que você determine se eles são autenticados e se eles pertencem a uma função específica.</span><span class="sxs-lookup"><span data-stu-id="ff05d-244">This will get you access to the user, which can let you determine if they are authenticated and if they belong to a particular role.</span></span> <span data-ttu-id="ff05d-245">Se você precisar avaliar uma política com um procedimento, poderá injetar uma instância do `IAuthorizationService` e chamar o `AuthorizeAsync` método nele.</span><span class="sxs-lookup"><span data-stu-id="ff05d-245">If you need to evaluate a policy procedurally, you can inject an instance of the `IAuthorizationService` and calls the `AuthorizeAsync` method on it.</span></span> <span data-ttu-id="ff05d-246">O código de exemplo a seguir demonstra como obter informações do usuário e permitir que um usuário autorizado execute uma tarefa restrita pela `content-editor` política.</span><span class="sxs-lookup"><span data-stu-id="ff05d-246">The following sample code demonstrates how to get user information and allow an authorized user to perform a task restricted by the `content-editor` policy.</span></span>

```razor
@using Microsoft.AspNetCore.Authorization
@inject IAuthorizationService AuthorizationService

<button @onclick="@DoSomething">Do something important</button>

@code {
    [CascadingParameter]
    private Task<AuthenticationState> authenticationStateTask { get; set; }

    private async Task DoSomething()
    {
        var user = (await authenticationStateTask).User;

        if (user.Identity.IsAuthenticated)
        {
            // Perform an action only available to authenticated (signed-in) users.
        }

        if (user.IsInRole("admin"))
        {
            // Perform an action only available to users in the 'admin' role.
        }

        if ((await AuthorizationService.AuthorizeAsync(user, "content-editor"))
            .Succeeded)
        {
            // Perform an action only available to users satisfying the
            // 'content-editor' policy.
        }
    }
}
```

<span data-ttu-id="ff05d-247">O `AuthenticationState` primeiro precisa ser configurado como um valor em cascata antes que possa ser associado a um parâmetro em cascata como este.</span><span class="sxs-lookup"><span data-stu-id="ff05d-247">The `AuthenticationState` does first need to be setup as a cascading value before it can be bound to a cascading parameter like this.</span></span> <span data-ttu-id="ff05d-248">Isso normalmente é feito usando o `CascadingAuthenticationState` componente.</span><span class="sxs-lookup"><span data-stu-id="ff05d-248">That's typically done using the `CascadingAuthenticationState` component.</span></span> <span data-ttu-id="ff05d-249">Normalmente, isso é feito em `App.razor` :</span><span class="sxs-lookup"><span data-stu-id="ff05d-249">This is typically done in `App.razor`:</span></span>

```razor
<CascadingAuthenticationState>
    <Router AppAssembly="@typeof(Program).Assembly">
        <Found Context="routeData">
            <AuthorizeRouteView RouteData="@routeData"
                DefaultLayout="@typeof(MainLayout)" />
        </Found>
        <NotFound>
            <LayoutView Layout="@typeof(MainLayout)">
                <p>Sorry, there's nothing at this address.</p>
            </LayoutView>
        </NotFound>
    </Router>
</CascadingAuthenticationState>
```

## <a name="summary"></a><span data-ttu-id="ff05d-250">Resumo</span><span class="sxs-lookup"><span data-stu-id="ff05d-250">Summary</span></span>

<span data-ttu-id="ff05d-251">Blazor usa o mesmo modelo de segurança que ASP.NET Core, que é ASP.NET Core identidade.</span><span class="sxs-lookup"><span data-stu-id="ff05d-251">Blazor uses the same security model as ASP.NET Core, which is ASP.NET Core Identity.</span></span> <span data-ttu-id="ff05d-252">A migração de provedores universais para ASP.NET Core identidade é relativamente simples, supondo que uma personalização muito grande foi aplicada ao esquema de dados original.</span><span class="sxs-lookup"><span data-stu-id="ff05d-252">Migrating from universal providers to ASP.NET Core Identity is relatively straightforward, assuming not too much customization was applied to the original data schema.</span></span> <span data-ttu-id="ff05d-253">Depois que os dados são migrados, trabalhar com autenticação e autorização em Blazor aplicativos é bem documentado, com suporte configurável e programático para a maioria dos requisitos de segurança.</span><span class="sxs-lookup"><span data-stu-id="ff05d-253">Once the data has been migrated, working with authentication and authorization in Blazor apps is well-documented, with configurable as well as programmatic support for most security requirements.</span></span>

## <a name="references"></a><span data-ttu-id="ff05d-254">Referências</span><span class="sxs-lookup"><span data-stu-id="ff05d-254">References</span></span>

- [<span data-ttu-id="ff05d-255">Introdução à identidade no ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ff05d-255">Introduction to Identity on ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/security/authentication/identity)
- [<span data-ttu-id="ff05d-256">Migrar da autenticação de associação do ASP.NET para a identidade do ASP.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="ff05d-256">Migrate from ASP.NET Membership authentication to ASP.NET Core 2.0 Identity</span></span>](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [<span data-ttu-id="ff05d-257">Migrar autenticação e identidade para ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ff05d-257">Migrate Authentication and Identity to ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/migration/identity)
- [<span data-ttu-id="ff05d-258">BlazorAutenticação e autorização do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ff05d-258">ASP.NET Core Blazor authentication and authorization</span></span>](https://docs.microsoft.com/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
><span data-ttu-id="ff05d-259">[Anterior](config.md) 
> [Avançar](migration.md)</span><span class="sxs-lookup"><span data-stu-id="ff05d-259">[Previous](config.md)
[Next](migration.md)</span></span>
