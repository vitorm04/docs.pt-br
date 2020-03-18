---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968143"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="67a10-101">HTTP: O Navegador SameSite altera a autenticação de impacto</span><span class="sxs-lookup"><span data-stu-id="67a10-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="67a10-102">Alguns navegadores, como Chrome e Firefox, fizeram `SameSite` alterações em suas implementações de cookies.</span><span class="sxs-lookup"><span data-stu-id="67a10-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="67a10-103">As alterações afetam cenários de autenticação remota, como OpenID Connect `SameSite=None`e WS-Federation, que devem optar pelo envio .</span><span class="sxs-lookup"><span data-stu-id="67a10-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="67a10-104">No `SameSite=None` entanto, quebra sustam o iOS 12 e algumas versões mais antigas de outros navegadores.</span><span class="sxs-lookup"><span data-stu-id="67a10-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="67a10-105">O aplicativo precisa farejar essas `SameSite`versões e omitir .</span><span class="sxs-lookup"><span data-stu-id="67a10-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="67a10-106">Para discussão sobre este assunto, consulte [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span><span class="sxs-lookup"><span data-stu-id="67a10-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="67a10-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="67a10-107">Version introduced</span></span>

<span data-ttu-id="67a10-108">3.1 Pré-visualização 1</span><span class="sxs-lookup"><span data-stu-id="67a10-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="67a10-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="67a10-109">Old behavior</span></span>

<span data-ttu-id="67a10-110">`SameSite`é uma extensão padrão de rascunho de 2016 para cookies HTTP.</span><span class="sxs-lookup"><span data-stu-id="67a10-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="67a10-111">Destina-se a mitigar a Falsificação de Solicitações Entre Sites (CSRF).</span><span class="sxs-lookup"><span data-stu-id="67a10-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="67a10-112">Isso foi originalmente projetado como um recurso que os servidores optariam adicionando os novos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="67a10-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="67a10-113">ASP.NET Núcleo 2.0 adicionou suporte inicial para `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="67a10-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="67a10-114">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="67a10-114">New behavior</span></span>

<span data-ttu-id="67a10-115">O Google propôs um novo padrão de rascunho que não é retrocompatível.</span><span class="sxs-lookup"><span data-stu-id="67a10-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="67a10-116">O padrão altera o `Lax` modo padrão `None` e adiciona uma nova entrada para desativar. `Lax` basta para a maioria dos cookies de aplicativos; no entanto, ele quebra cenários entre sites como OpenID Connect e ws-federation login.</span><span class="sxs-lookup"><span data-stu-id="67a10-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="67a10-117">A maioria dos logins OAuth não são afetados por causa de diferenças na forma como a solicitação flui.</span><span class="sxs-lookup"><span data-stu-id="67a10-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="67a10-118">O `None` novo parâmetro causa problemas de compatibilidade com clientes que implementaram o padrão de rascunho anterior (por exemplo, o iOS 12).</span><span class="sxs-lookup"><span data-stu-id="67a10-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="67a10-119">O Chrome 80 incluirá as alterações.</span><span class="sxs-lookup"><span data-stu-id="67a10-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="67a10-120">Consulte [as atualizações do mesmosite](https://www.chromium.org/updates/same-site) para a linha do tempo de lançamento do produto Chrome.</span><span class="sxs-lookup"><span data-stu-id="67a10-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="67a10-121">ASP.NET O Core 3.1 foi `SameSite` atualizado para implementar o novo comportamento.</span><span class="sxs-lookup"><span data-stu-id="67a10-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="67a10-122">A atualização redefine o `SameSiteMode.None` comportamento `SameSite=None` de emitir `SameSiteMode.Unspecified` e adiciona `SameSite` um novo valor para omitir o atributo.</span><span class="sxs-lookup"><span data-stu-id="67a10-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="67a10-123">Todas as APIs `Unspecified`de cookies agora são padrão, embora alguns componentes que usam cookies definam valores mais específicos para seus cenários, como a correlação OpenID Connect e os cookies nonce.</span><span class="sxs-lookup"><span data-stu-id="67a10-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="67a10-124">Para outras alterações recentes nesta área, consulte [HTTP: Alguns padrões do Cookie SameSite alterados para Nenhum](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span><span class="sxs-lookup"><span data-stu-id="67a10-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="67a10-125">Em ASP.NET Núcleo 3.0, a <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> maioria <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> dos padrões foi alterada de (mas ainda usando o padrão anterior).</span><span class="sxs-lookup"><span data-stu-id="67a10-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="67a10-126">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="67a10-126">Reason for change</span></span>

<span data-ttu-id="67a10-127">Alterações de navegador e especificação conforme descrito no texto anterior.</span><span class="sxs-lookup"><span data-stu-id="67a10-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="67a10-128">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="67a10-128">Recommended action</span></span>

<span data-ttu-id="67a10-129">Aplicativos que interagem com sites remotos, como por meio de login de terceiros, precisam:</span><span class="sxs-lookup"><span data-stu-id="67a10-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="67a10-130">Teste esses cenários em vários navegadores.</span><span class="sxs-lookup"><span data-stu-id="67a10-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="67a10-131">Aplique a mitigação de sniffing do navegador de política de cookies discutida no [suporte a navegadores mais antigos](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="67a10-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="67a10-132">Para obter instruções de teste e de farejamento do navegador, consulte a seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="67a10-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="67a10-133">Determine se você é afetado</span><span class="sxs-lookup"><span data-stu-id="67a10-133">Determine if you're affected</span></span>

<span data-ttu-id="67a10-134">Teste seu aplicativo web usando uma versão cliente que pode optar pelo novo comportamento.</span><span class="sxs-lookup"><span data-stu-id="67a10-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="67a10-135">Chrome, Firefox e Microsoft Edge Chromium têm novos sinalizadores de recurso opt-in que podem ser usados para testes.</span><span class="sxs-lookup"><span data-stu-id="67a10-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="67a10-136">Verifique se seu aplicativo é compatível com versões mais antigas do cliente depois de aplicar os patches, especialmente o Safari.</span><span class="sxs-lookup"><span data-stu-id="67a10-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="67a10-137">Para obter mais informações, consulte [Suporte a navegadores mais antigos](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="67a10-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="67a10-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="67a10-138">Chrome</span></span>

<span data-ttu-id="67a10-139">O Chrome 78 e posteriormente produzem resultados de teste enganosos.</span><span class="sxs-lookup"><span data-stu-id="67a10-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="67a10-140">Essas versões têm uma atenuação temporária e permitem cookies com menos de dois minutos de idade.</span><span class="sxs-lookup"><span data-stu-id="67a10-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="67a10-141">Com os sinalizadores de teste apropriados ativados, os Chrome 76 e 77 produzem resultados mais precisos.</span><span class="sxs-lookup"><span data-stu-id="67a10-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="67a10-142">Para testar o novo comportamento, alterne `chrome://flags/#same-site-by-default-cookies` para ativado.</span><span class="sxs-lookup"><span data-stu-id="67a10-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="67a10-143">O Chrome 75 e anteriormente `None` são relatados como falha com a nova configuração.</span><span class="sxs-lookup"><span data-stu-id="67a10-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="67a10-144">Para obter mais informações, consulte [Suporte a navegadores mais antigos](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="67a10-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="67a10-145">O Google não disponibiliza versões mais antigas do Chrome.</span><span class="sxs-lookup"><span data-stu-id="67a10-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="67a10-146">Você pode, no entanto, baixar versões mais antigas do Chromium, o que será suficiente para testes.</span><span class="sxs-lookup"><span data-stu-id="67a10-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="67a10-147">Siga as instruções em [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span><span class="sxs-lookup"><span data-stu-id="67a10-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="67a10-148">Cromo 76 Win64</span><span class="sxs-lookup"><span data-stu-id="67a10-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="67a10-149">Cromo 74 Win64</span><span class="sxs-lookup"><span data-stu-id="67a10-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="67a10-150">Safari</span><span class="sxs-lookup"><span data-stu-id="67a10-150">Safari</span></span>

<span data-ttu-id="67a10-151">O Safari 12 implementou estritamente o rascunho `None` anterior e falha se vir o novo valor em cookies.</span><span class="sxs-lookup"><span data-stu-id="67a10-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="67a10-152">Isso deve ser evitado através do código de farejador do navegador mostrado no [Suporte a navegadores mais antigos](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="67a10-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="67a10-153">Certifique-se de testar o Safari 12 e 13, bem como logins baseados no WebKit, no estilo sO, usando a Microsoft Authentication Library (MSAL), a Active Directory Authentication Library (ADAL) ou qualquer biblioteca que você esteja usando.</span><span class="sxs-lookup"><span data-stu-id="67a10-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="67a10-154">O problema depende da versão do sistema operacional subjacente.</span><span class="sxs-lookup"><span data-stu-id="67a10-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="67a10-155">Sabe-se que os OSX Mojave 10.14 e iOS 12 têm problemas de compatibilidade com o novo comportamento.</span><span class="sxs-lookup"><span data-stu-id="67a10-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="67a10-156">A atualização para o OSX Catalina 10.15 ou iOS 13 corrige o problema.</span><span class="sxs-lookup"><span data-stu-id="67a10-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="67a10-157">Atualmente, o Safari não tem um sinalizador de opt-in para testar o novo comportamento de especificação.</span><span class="sxs-lookup"><span data-stu-id="67a10-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="67a10-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="67a10-158">Firefox</span></span>

<span data-ttu-id="67a10-159">O suporte ao Firefox para o novo padrão pode ser testado `about:config` na versão `network.cookie.sameSite.laxByDefault`68 e posteriormente optando na página com o sinalizador de recurso .</span><span class="sxs-lookup"><span data-stu-id="67a10-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="67a10-160">Nenhum problema de compatibilidade foi relatado em versões mais antigas do Firefox.</span><span class="sxs-lookup"><span data-stu-id="67a10-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="67a10-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="67a10-161">Microsoft Edge</span></span>

<span data-ttu-id="67a10-162">Embora o Microsoft Edge `SameSite` suporte o antigo padrão, a partir da versão 44 não teve nenhum problema de compatibilidade com o novo padrão.</span><span class="sxs-lookup"><span data-stu-id="67a10-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="67a10-163">Cromo Da Borda da Microsoft</span><span class="sxs-lookup"><span data-stu-id="67a10-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="67a10-164">A bandeira `edge://flags/#same-site-by-default-cookies`de recurso é .</span><span class="sxs-lookup"><span data-stu-id="67a10-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="67a10-165">Não foram observados problemas de compatibilidade durante os testes com o Microsoft Edge Chromium 78.</span><span class="sxs-lookup"><span data-stu-id="67a10-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="67a10-166">Elétron</span><span class="sxs-lookup"><span data-stu-id="67a10-166">Electron</span></span>

<span data-ttu-id="67a10-167">Versões de Electron incluem versões mais antigas do Chromium.</span><span class="sxs-lookup"><span data-stu-id="67a10-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="67a10-168">Por exemplo, a versão do Electron usada pelo Microsoft Teams é o Chromium 66, que exibe o comportamento mais antigo.</span><span class="sxs-lookup"><span data-stu-id="67a10-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="67a10-169">Realize seus próprios testes de compatibilidade com a versão da Electron que seu produto usa.</span><span class="sxs-lookup"><span data-stu-id="67a10-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="67a10-170">Para obter mais informações, consulte [Suporte a navegadores mais antigos](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="67a10-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="67a10-171">Suporte a navegadores mais antigos</span><span class="sxs-lookup"><span data-stu-id="67a10-171">Support older browsers</span></span>

<span data-ttu-id="67a10-172">A norma de `SameSite` 2016 determinava `SameSite=Strict` que valores desconhecidos fossem tratados como valores.</span><span class="sxs-lookup"><span data-stu-id="67a10-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="67a10-173">Consequentemente, todos os navegadores mais antigos que `SameSite` suportam o `None`padrão original podem quebrar quando virem uma propriedade com um valor de .</span><span class="sxs-lookup"><span data-stu-id="67a10-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="67a10-174">Os aplicativos da Web devem implementar o sniffing do navegador se eles pretendem suportar esses navegadores antigos.</span><span class="sxs-lookup"><span data-stu-id="67a10-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="67a10-175">ASP.NET Core não implementa o sniffing do navegador para você porque `User-Agent` os valores de cabeçalho de solicitação são altamente instáveis e mudam semanalmente.</span><span class="sxs-lookup"><span data-stu-id="67a10-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="67a10-176">Em vez disso, um ponto de `User-Agent`extensão na política de cookies permite adicionar uma lógica específica.</span><span class="sxs-lookup"><span data-stu-id="67a10-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="67a10-177">Em *Startup.cs,* adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="67a10-177">In *Startup.cs*, add the following code:</span></span>

```csharp
private void CheckSameSite(HttpContext httpContext, CookieOptions options)
{
    if (options.SameSite == SameSiteMode.None)
    {
        var userAgent = httpContext.Request.Headers["User-Agent"].ToString();
        // TODO: Use your User Agent library of choice here.
        if (/* UserAgent doesn't support new behavior */)
        {
            options.SameSite = SameSiteMode.Unspecified;
        }
    }
}

public void ConfigureServices(IServiceCollection services)
{
    services.Configure<CookiePolicyOptions>(options =>
    {
        options.MinimumSameSitePolicy = SameSiteMode.Unspecified;
        options.OnAppendCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
        options.OnDeleteCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
    });
}

public void Configure(IApplicationBuilder app)
{
    // Before UseAuthentication or anything else that writes cookies.
    app.UseCookiePolicy();

    app.UseAuthentication();
    // code omitted for brevity
}
```

##### <a name="opt-out-switches"></a><span data-ttu-id="67a10-178">Interruptores de exclusão</span><span class="sxs-lookup"><span data-stu-id="67a10-178">Opt-out switches</span></span>

<span data-ttu-id="67a10-179">O `Microsoft.AspNetCore.SuppressSameSiteNone` switch de compatibilidade permite que você opte temporariamente pelo novo comportamento de cookies ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="67a10-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="67a10-180">Adicione o JSON a seguir a um arquivo *runtimeconfig.template.json* em seu projeto:</span><span class="sxs-lookup"><span data-stu-id="67a10-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a><span data-ttu-id="67a10-181">Outras versões</span><span class="sxs-lookup"><span data-stu-id="67a10-181">Other Versions</span></span>

<span data-ttu-id="67a10-182">Patches `SameSite` relacionados estão próximos para:</span><span class="sxs-lookup"><span data-stu-id="67a10-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="67a10-183">ASP.NET Core 2.1, 2.2 e 3.0</span><span class="sxs-lookup"><span data-stu-id="67a10-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="67a10-184">`Microsoft.Owin`4.1</span><span class="sxs-lookup"><span data-stu-id="67a10-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="67a10-185">`System.Web`(para .NET Framework 4.7.2 e posteriores)</span><span class="sxs-lookup"><span data-stu-id="67a10-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="67a10-186">Categoria</span><span class="sxs-lookup"><span data-stu-id="67a10-186">Category</span></span>

<span data-ttu-id="67a10-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="67a10-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="67a10-188">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="67a10-188">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieBuilder.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieOptions.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`
- `Overload:Microsoft.AspNetCore.Http.CookieBuilder.SameSite`
- `Overload:Microsoft.AspNetCore.Http.CookieOptions.SameSite`
- `T:Microsoft.AspNetCore.Http.SameSiteMode`
- `T:Microsoft.Net.Http.Headers.SameSiteMode`
- `Overload:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite`

-->
