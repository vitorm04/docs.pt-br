---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968143"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a>HTTP: O Navegador SameSite altera a autenticação de impacto

Alguns navegadores, como Chrome e Firefox, fizeram `SameSite` alterações em suas implementações de cookies. As alterações afetam cenários de autenticação remota, como OpenID Connect `SameSite=None`e WS-Federation, que devem optar pelo envio . No `SameSite=None` entanto, quebra sustam o iOS 12 e algumas versões mais antigas de outros navegadores. O aplicativo precisa farejar essas `SameSite`versões e omitir .

Para discussão sobre este assunto, consulte [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).

#### <a name="version-introduced"></a>Versão introduzida

3.1 Pré-visualização 1

#### <a name="old-behavior"></a>Comportamento antigo

`SameSite`é uma extensão padrão de rascunho de 2016 para cookies HTTP. Destina-se a mitigar a Falsificação de Solicitações Entre Sites (CSRF). Isso foi originalmente projetado como um recurso que os servidores optariam adicionando os novos parâmetros. ASP.NET Núcleo 2.0 adicionou suporte inicial para `SameSite`.

#### <a name="new-behavior"></a>Novo comportamento

O Google propôs um novo padrão de rascunho que não é retrocompatível. O padrão altera o `Lax` modo padrão `None` e adiciona uma nova entrada para desativar. `Lax` basta para a maioria dos cookies de aplicativos; no entanto, ele quebra cenários entre sites como OpenID Connect e ws-federation login. A maioria dos logins OAuth não são afetados por causa de diferenças na forma como a solicitação flui. O `None` novo parâmetro causa problemas de compatibilidade com clientes que implementaram o padrão de rascunho anterior (por exemplo, o iOS 12). O Chrome 80 incluirá as alterações. Consulte [as atualizações do mesmosite](https://www.chromium.org/updates/same-site) para a linha do tempo de lançamento do produto Chrome.

ASP.NET O Core 3.1 foi `SameSite` atualizado para implementar o novo comportamento. A atualização redefine o `SameSiteMode.None` comportamento `SameSite=None` de emitir `SameSiteMode.Unspecified` e adiciona `SameSite` um novo valor para omitir o atributo. Todas as APIs `Unspecified`de cookies agora são padrão, embora alguns componentes que usam cookies definam valores mais específicos para seus cenários, como a correlação OpenID Connect e os cookies nonce.

Para outras alterações recentes nesta área, consulte [HTTP: Alguns padrões do Cookie SameSite alterados para Nenhum](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none). Em ASP.NET Núcleo 3.0, a <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> maioria <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> dos padrões foi alterada de (mas ainda usando o padrão anterior).

#### <a name="reason-for-change"></a>Motivo da mudança

Alterações de navegador e especificação conforme descrito no texto anterior.

#### <a name="recommended-action"></a>Ação recomendada

Aplicativos que interagem com sites remotos, como por meio de login de terceiros, precisam:

* Teste esses cenários em vários navegadores.
* Aplique a mitigação de sniffing do navegador de política de cookies discutida no [suporte a navegadores mais antigos](#support-older-browsers).

Para obter instruções de teste e de farejamento do navegador, consulte a seção a seguir.

##### <a name="determine-if-youre-affected"></a>Determine se você é afetado

Teste seu aplicativo web usando uma versão cliente que pode optar pelo novo comportamento. Chrome, Firefox e Microsoft Edge Chromium têm novos sinalizadores de recurso opt-in que podem ser usados para testes. Verifique se seu aplicativo é compatível com versões mais antigas do cliente depois de aplicar os patches, especialmente o Safari. Para obter mais informações, consulte [Suporte a navegadores mais antigos](#support-older-browsers).

##### <a name="chrome"></a>Chrome

O Chrome 78 e posteriormente produzem resultados de teste enganosos. Essas versões têm uma atenuação temporária e permitem cookies com menos de dois minutos de idade. Com os sinalizadores de teste apropriados ativados, os Chrome 76 e 77 produzem resultados mais precisos. Para testar o novo comportamento, alterne `chrome://flags/#same-site-by-default-cookies` para ativado. O Chrome 75 e anteriormente `None` são relatados como falha com a nova configuração. Para obter mais informações, consulte [Suporte a navegadores mais antigos](#support-older-browsers).

O Google não disponibiliza versões mais antigas do Chrome. Você pode, no entanto, baixar versões mais antigas do Chromium, o que será suficiente para testes. Siga as instruções em [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).

* [Cromo 76 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [Cromo 74 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a>Safari

O Safari 12 implementou estritamente o rascunho `None` anterior e falha se vir o novo valor em cookies. Isso deve ser evitado através do código de farejador do navegador mostrado no [Suporte a navegadores mais antigos](#support-older-browsers). Certifique-se de testar o Safari 12 e 13, bem como logins baseados no WebKit, no estilo sO, usando a Microsoft Authentication Library (MSAL), a Active Directory Authentication Library (ADAL) ou qualquer biblioteca que você esteja usando. O problema depende da versão do sistema operacional subjacente. Sabe-se que os OSX Mojave 10.14 e iOS 12 têm problemas de compatibilidade com o novo comportamento. A atualização para o OSX Catalina 10.15 ou iOS 13 corrige o problema. Atualmente, o Safari não tem um sinalizador de opt-in para testar o novo comportamento de especificação.

##### <a name="firefox"></a>Firefox

O suporte ao Firefox para o novo padrão pode ser testado `about:config` na versão `network.cookie.sameSite.laxByDefault`68 e posteriormente optando na página com o sinalizador de recurso . Nenhum problema de compatibilidade foi relatado em versões mais antigas do Firefox.

##### <a name="microsoft-edge"></a>Microsoft Edge

Embora o Microsoft Edge `SameSite` suporte o antigo padrão, a partir da versão 44 não teve nenhum problema de compatibilidade com o novo padrão.

##### <a name="microsoft-edge-chromium"></a>Cromo Da Borda da Microsoft

A bandeira `edge://flags/#same-site-by-default-cookies`de recurso é . Não foram observados problemas de compatibilidade durante os testes com o Microsoft Edge Chromium 78.

##### <a name="electron"></a>Elétron

Versões de Electron incluem versões mais antigas do Chromium. Por exemplo, a versão do Electron usada pelo Microsoft Teams é o Chromium 66, que exibe o comportamento mais antigo. Realize seus próprios testes de compatibilidade com a versão da Electron que seu produto usa. Para obter mais informações, consulte [Suporte a navegadores mais antigos](#support-older-browsers).

##### <a name="support-older-browsers"></a>Suporte a navegadores mais antigos

A norma de `SameSite` 2016 determinava `SameSite=Strict` que valores desconhecidos fossem tratados como valores. Consequentemente, todos os navegadores mais antigos que `SameSite` suportam o `None`padrão original podem quebrar quando virem uma propriedade com um valor de . Os aplicativos da Web devem implementar o sniffing do navegador se eles pretendem suportar esses navegadores antigos. ASP.NET Core não implementa o sniffing do navegador para você porque `User-Agent` os valores de cabeçalho de solicitação são altamente instáveis e mudam semanalmente. Em vez disso, um ponto de `User-Agent`extensão na política de cookies permite adicionar uma lógica específica.

Em *Startup.cs,* adicione o seguinte código:

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

##### <a name="opt-out-switches"></a>Interruptores de exclusão

O `Microsoft.AspNetCore.SuppressSameSiteNone` switch de compatibilidade permite que você opte temporariamente pelo novo comportamento de cookies ASP.NET Core. Adicione o JSON a seguir a um arquivo *runtimeconfig.template.json* em seu projeto:

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a>Outras versões

Patches `SameSite` relacionados estão próximos para:

* ASP.NET Core 2.1, 2.2 e 3.0
* `Microsoft.Owin`4.1
* `System.Web`(para .NET Framework 4.7.2 e posteriores)

#### <a name="category"></a>Categoria

ASP.NET

#### <a name="affected-apis"></a>APIs afetadas

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
