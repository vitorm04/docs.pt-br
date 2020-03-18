---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393967"
---
### <a name="authentication-google-deprecated-and-replaced"></a>Autenticação: Google+ preterido e substituído

O Google está começando a [encerrar](https://developers.google.com/+/api-shutdown) o Google+ Sign-in para aplicativos já em 28 de janeiro de 2019.

#### <a name="change-description"></a>Descrição da alteração

ASP.NET 4.x e ASP.NET Core têm usado as APIs de login do Google+ para autenticar usuários de contas do Google em aplicativos da Web. Os pacotes NuGet afetados são [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core `Microsoft.Owin` e [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) para com ASP.NET Formulários da Web e MVC.

As APIs de substituição do Google usam uma fonte e formato de dados diferentes. As mitigações e soluções fornecidas abaixo explicam as mudanças estruturais. Os aplicativos devem verificar se os dados em si ainda satisfazem suas necessidades. Por exemplo, nomes, endereços de e-mail, links de perfil e fotos de perfil podem fornecer valores sutilmente diferentes do que antes.

#### <a name="version-introduced"></a>Versão introduzida

Todas as versões. Esta mudança é externa ao ASP.NET Core.

#### <a name="recommended-action"></a>Ação recomendada

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a>Owin com formulários ASP.NET web e MVC

Para `Microsoft.Owin` 3.1.0 e posteriormente, uma mitigação temporária é delineada [aqui.](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635) Os aplicativos devem concluir os testes com a mitigação para verificar se há alterações no formato dos dados. Há planos para `Microsoft.Owin` lançar 4.0.1 com uma correção. Os aplicativos que usam qualquer versão anterior devem ser atualizados para a versão 4.0.1.

##### <a name="aspnet-core-1x"></a>ASP.NET Core 1.x

A mitigação em [Owin com ASP.NET Web Forms e MVC](#owin-with-aspnet-web-forms-and-mvc) pode ser adaptada para ASP.NET Core 1.x. Os patches do pacote NuGet não estão planejados porque o 1.x atingiu o status [de fim de vida](https://dotnet.microsoft.com/platform/support-policy) útil.

##### <a name="aspnet-core-2x"></a>ASP.NET Core 2.x

Para `Microsoft.AspNetCore.Authentication.Google` a versão 2.x, substitua `Startup.ConfigureServices` a chamada existente pelo `AddGoogle` seguinte código:

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

Os patches 2.1 e 2.2 de fevereiro incorporaram a reconfiguração anterior como o novo padrão. Nenhum patch está planejado para ASP.NET Núcleo 2.0 desde que chegou ao [fim da vida](https://dotnet.microsoft.com/platform/support-policy).

##### <a name="aspnet-core-30"></a>núcleo de ASP.NET 3.0

A atenuação dada para ASP.NET Core 2.x também pode ser usada para ASP.NET Núcleo 3.0. Em visualizações futuras 3.0, o `Microsoft.AspNetCore.Authentication.Google` pacote pode ser removido. Em `Microsoft.AspNetCore.Authentication.OpenIdConnect` vez disso, os usuários seriam direcionados. O código a seguir `AddGoogle` `AddOpenIdConnect` mostra `Startup.ConfigureServices`como substituir por in . Esta substituição pode ser usada com ASP.NET Core 2.0 e posteriormente e pode ser adaptada para ASP.NET Core 1.x conforme necessário.

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

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
