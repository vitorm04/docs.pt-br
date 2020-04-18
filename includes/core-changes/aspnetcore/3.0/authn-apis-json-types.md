---
ms.openlocfilehash: b4499637cd5fff015335e0cdb3c6cf1c3ea6cff0
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81637178"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>Autenticação: Tipos Newtonsoft.Json substituídos

Em ASP.NET Núcleo 3.0, `Newtonsoft.Json` os tipos usados nas `System.Text.Json` APIs de autenticação foram substituídos por tipos. Exceto para os seguintes casos, o uso básico dos pacotes de autenticação permanece inalterado:

* Classes derivadas dos provedores OAuth, como as do [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).
* Implementações avançadas de manipulação de sinistros.

Para obter mais informações, consulte [dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105). Para discussão, consulte [dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Para implementações oAuth derivadas, a mudança `JObject.Parse` `JsonDocument.Parse` mais `CreateTicketAsync` comum é substituir na substituição como mostrado [aqui](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40). `JsonDocument` implementa `IDisposable`.

A lista a seguir descreve alterações conhecidas:

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType>torna-se `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`. Todas as implementações `ClaimAction` derivadas são igualmente afetadas.
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> torna-se `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> torna-se `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext>teve um antigo construtor removido e `JObject` o `JsonElement`outro substituído por . A `User` propriedade `RunClaimActions` e o método foram atualizados para coincidir.
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)>agora aceita um parâmetro `JsonDocument` de `JObject`tipo em vez de . A `Response` propriedade foi atualizada para coincidir. `OAuthTokenResponse`agora é descartável e `OAuthHandler`será descartado por . Implementações oAuth derivadas `ExchangeCodeAsync` não precisam descartar `JsonDocument` o `OAuthTokenResponse`ou .
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType>mudou `JObject` de `JsonDocument`.
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType>mudou `JObject` de `JsonElement`.
- O último parâmetro do [TwitterHandler.CreateTicketAsync (ClaimsIdentity,AuthenticationProperties,AccessToken,JObject)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.authentication.twitter.twitterhandler.createticketasync?view=aspnetcore-2.2#Microsoft_AspNetCore_Authentication_Twitter_TwitterHandler_CreateTicketAsync_System_Security_Claims_ClaimsIdentity_Microsoft_AspNetCore_Authentication_AuthenticationProperties_Microsoft_AspNetCore_Authentication_Twitter_AccessToken_Newtonsoft_Json_Linq_JObject_) mudou de `JObject` `JsonElement`para . O método <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,System.Text.Json.JsonElement)?displayProperty=nameWithType>de substituição é .

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.AspNetCore.Authentication.Facebook?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.MicrosoftAccount?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OAuth?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Twitter?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Facebook`
- `N:Microsoft.AspNetCore.Authentication.Google`
- `N:Microsoft.AspNetCore.Authentication.MicrosoftAccount`
- `N:Microsoft.AspNetCore.Authentication.OAuth`
- `N:Microsoft.AspNetCore.Authentication.OpenIdConnect`
- `N:Microsoft.AspNetCore.Authentication.Twitter`

-->
