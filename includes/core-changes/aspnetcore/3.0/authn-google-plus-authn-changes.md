---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393967"
---
### <a name="authentication-google-deprecated-and-replaced"></a><span data-ttu-id="80049-101">Autenticação: Google + preterido e substituído</span><span class="sxs-lookup"><span data-stu-id="80049-101">Authentication: Google+ deprecated and replaced</span></span>

<span data-ttu-id="80049-102">O Google está começando a [desligar](https://developers.google.com/+/api-shutdown) o Google + entrar para aplicativos como no início de 28 de janeiro de 2019.</span><span class="sxs-lookup"><span data-stu-id="80049-102">Google is starting to [shut down](https://developers.google.com/+/api-shutdown) Google+ Sign-in for apps as early as January 28, 2019.</span></span>

#### <a name="change-description"></a><span data-ttu-id="80049-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="80049-103">Change description</span></span>

<span data-ttu-id="80049-104">ASP.NET 4. x e ASP.NET Core têm usado as APIs de entrada do Google + para autenticar usuários da conta do Google em aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="80049-104">ASP.NET 4.x and ASP.NET Core have been using the Google+ Sign-in APIs to authenticate Google account users in web apps.</span></span> <span data-ttu-id="80049-105">Os pacotes NuGet afetados são [Microsoft. AspNetCore. Authentication. Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) para ASP.NET Core e [Microsoft. Owin. Security. Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) para `Microsoft.Owin` com ASP.NET Web Forms e MVC.</span><span class="sxs-lookup"><span data-stu-id="80049-105">The affected NuGet packages are [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core and [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) for `Microsoft.Owin` with ASP.NET Web Forms and MVC.</span></span>

<span data-ttu-id="80049-106">As APIs de substituição do Google usam uma fonte de dados e um formato diferentes.</span><span class="sxs-lookup"><span data-stu-id="80049-106">Google's replacement APIs use a different data source and format.</span></span> <span data-ttu-id="80049-107">As atenuações e soluções fornecidas abaixo têm uma conta para as alterações estruturais.</span><span class="sxs-lookup"><span data-stu-id="80049-107">The mitigations and solutions provided below account for the structural changes.</span></span> <span data-ttu-id="80049-108">Os aplicativos devem verificar se os dados em si ainda atendem às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="80049-108">Apps should verify the data itself still satisfies their requirements.</span></span> <span data-ttu-id="80049-109">Por exemplo, nomes, endereços de email, links de perfil e fotos de perfil podem fornecer valores sutilmente diferentes de antes.</span><span class="sxs-lookup"><span data-stu-id="80049-109">For example, names, email addresses, profile links, and profile photos may provide subtly different values than before.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="80049-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="80049-110">Version introduced</span></span>

<span data-ttu-id="80049-111">Todas as versões.</span><span class="sxs-lookup"><span data-stu-id="80049-111">All versions.</span></span> <span data-ttu-id="80049-112">Essa alteração é externa a ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="80049-112">This change is external to ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="80049-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="80049-113">Recommended action</span></span>

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a><span data-ttu-id="80049-114">Owin com ASP.NET Web Forms e MVC</span><span class="sxs-lookup"><span data-stu-id="80049-114">Owin with ASP.NET Web Forms and MVC</span></span>

<span data-ttu-id="80049-115">Para `Microsoft.Owin` 3.1.0 e posterior, uma mitigação temporária é descrita [aqui](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span><span class="sxs-lookup"><span data-stu-id="80049-115">For `Microsoft.Owin` 3.1.0 and later, a temporary mitigation is outlined [here](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span></span> <span data-ttu-id="80049-116">Os aplicativos devem concluir o teste com a mitigação para verificar se há alterações no formato de dados.</span><span class="sxs-lookup"><span data-stu-id="80049-116">Apps should complete testing with the mitigation to check for changes in the data format.</span></span> <span data-ttu-id="80049-117">Há planos para liberar `Microsoft.Owin` 4.0.1 com uma correção.</span><span class="sxs-lookup"><span data-stu-id="80049-117">There are plans to release `Microsoft.Owin` 4.0.1 with a fix.</span></span> <span data-ttu-id="80049-118">Os aplicativos que usam qualquer versão anterior devem ser atualizados para a versão 4.0.1.</span><span class="sxs-lookup"><span data-stu-id="80049-118">Apps using any prior version should update to version 4.0.1.</span></span>

##### <a name="aspnet-core-1x"></a><span data-ttu-id="80049-119">ASP.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="80049-119">ASP.NET Core 1.x</span></span>

<span data-ttu-id="80049-120">A mitigação no [Owin com ASP.NET Web Forms e MVC](#owin-with-aspnet-web-forms-and-mvc) pode ser adaptada para ASP.NET Core 1. x.</span><span class="sxs-lookup"><span data-stu-id="80049-120">The mitigation in [Owin with ASP.NET Web Forms and MVC](#owin-with-aspnet-web-forms-and-mvc) can be adapted to ASP.NET Core 1.x.</span></span> <span data-ttu-id="80049-121">Os patches do pacote NuGet não estão planejados porque 1. x atingiu o status [de término da vida útil](https://dotnet.microsoft.com/platform/support-policy) .</span><span class="sxs-lookup"><span data-stu-id="80049-121">NuGet package patches aren't planned because 1.x has reached [end of life](https://dotnet.microsoft.com/platform/support-policy) status.</span></span>

##### <a name="aspnet-core-2x"></a><span data-ttu-id="80049-122">ASP.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="80049-122">ASP.NET Core 2.x</span></span>

<span data-ttu-id="80049-123">Para `Microsoft.AspNetCore.Authentication.Google` versão 2. x, substitua sua chamada existente para `AddGoogle` em `Startup.ConfigureServices` pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="80049-123">For `Microsoft.AspNetCore.Authentication.Google` version 2.x, replace your existing call to `AddGoogle` in `Startup.ConfigureServices` with the following code:</span></span>

```csharp
.AddGoogle(o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.UserInformationEndpoint = "https://www.googleapis.com/oauth2/v2/userinfo";
    o.ClaimActions.Clear();
    o.ClaimActions.MapJsonKey(ClaimTypes.NameIdentifier, "id");
    o.ClaimActions.MapJsonKey(ClaimTypes.Name, "name");
    o.ClaimActions.MapJsonKey(ClaimTypes.GivenName, "given_name");
    o.ClaimActions.MapJsonKey(ClaimTypes.Surname, "family_name");
    o.ClaimActions.MapJsonKey("urn:google:profile", "link");
    o.ClaimActions.MapJsonKey(ClaimTypes.Email, "email");
});
```

<span data-ttu-id="80049-124">Os patches de fevereiro de 2,1 e 2,2 incorporaram a reconfiguração anterior como o novo padrão.</span><span class="sxs-lookup"><span data-stu-id="80049-124">The February 2.1 and 2.2 patches incorporated the preceding reconfiguration as the new default.</span></span> <span data-ttu-id="80049-125">Nenhum patch está planejado para ASP.NET Core 2,0, pois ele atingiu o [fim da vida útil](https://dotnet.microsoft.com/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="80049-125">No patch is planned for ASP.NET Core 2.0 since it has reached [end of life](https://dotnet.microsoft.com/platform/support-policy).</span></span>

##### <a name="aspnet-core-30"></a><span data-ttu-id="80049-126">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="80049-126">ASP.NET Core 3.0</span></span>

<span data-ttu-id="80049-127">A mitigação fornecida para o ASP.NET Core 2. x também pode ser usada para ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="80049-127">The mitigation given for ASP.NET Core 2.x can also be used for ASP.NET Core 3.0.</span></span> <span data-ttu-id="80049-128">Em futuras versões do 3,0, o pacote `Microsoft.AspNetCore.Authentication.Google` pode ser removido.</span><span class="sxs-lookup"><span data-stu-id="80049-128">In future 3.0 previews, the `Microsoft.AspNetCore.Authentication.Google` package may be removed.</span></span> <span data-ttu-id="80049-129">Os usuários seriam direcionados para `Microsoft.AspNetCore.Authentication.OpenIdConnect` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="80049-129">Users would be directed to `Microsoft.AspNetCore.Authentication.OpenIdConnect` instead.</span></span> <span data-ttu-id="80049-130">O código a seguir mostra como substituir `AddGoogle` por `AddOpenIdConnect` em `Startup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="80049-130">The following code shows how to replace `AddGoogle` with `AddOpenIdConnect` in `Startup.ConfigureServices`.</span></span> <span data-ttu-id="80049-131">Essa substituição pode ser usada com o ASP.NET Core 2,0 e posterior e pode ser adaptada para o ASP.NET Core 1. x, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="80049-131">This replacement can be used with ASP.NET Core 2.0 and later and can be adapted for ASP.NET Core 1.x as needed.</span></span>

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/sigin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a><span data-ttu-id="80049-132">Categoria</span><span class="sxs-lookup"><span data-stu-id="80049-132">Category</span></span>

<span data-ttu-id="80049-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="80049-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="80049-134">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="80049-134">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
