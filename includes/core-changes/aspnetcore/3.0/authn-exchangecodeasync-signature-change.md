---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394285"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>Autenticação: OAuthHandler ExchangeCodeAsync assinatura alterada

Em ASP.NET Núcleo 3.0, `OAuthHandler.ExchangeCodeAsync` a assinatura foi alterada de:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

Para:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

As `code` `redirectUri` cordas e cordas foram passadas como argumentos separados.

#### <a name="new-behavior"></a>Novo comportamento

`Code`e `RedirectUri` são `OAuthCodeExchangeContext` propriedades que podem `OAuthCodeExchangeContext` ser definidas através do construtor. O `OAuthCodeExchangeContext` novo tipo é o `OAuthHandler.ExchangeCodeAsync`único argumento passado para .

#### <a name="reason-for-change"></a>Motivo da mudança

Esta alteração permite que parâmetros adicionais sejam fornecidos de forma não-quebra. Não há necessidade de `ExchangeCodeAsync` criar novas sobrecargas.

#### <a name="recommended-action"></a>Ação recomendada

Construa `OAuthCodeExchangeContext` um `code` com `redirectUri` os valores apropriados e. Uma <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instância deve ser fornecida. Esta `OAuthCodeExchangeContext` única instância pode `OAuthHandler.ExchangeCodeAsync` ser passada para em vez de múltiplos argumentos.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
