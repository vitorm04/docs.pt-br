---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394285"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>Autenticação: assinatura OAuthHandler ExchangeCodeAsync alterada

No ASP.NET Core 3,0, a assinatura de `OAuthHandler.ExchangeCodeAsync` foi alterada de:

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

As cadeias de caracteres `code` e `redirectUri` foram passadas como argumentos separados.

#### <a name="new-behavior"></a>Novo comportamento

`Code` e `RedirectUri` são propriedades em `OAuthCodeExchangeContext` que podem ser definidas por meio do Construtor `OAuthCodeExchangeContext`. O novo tipo `OAuthCodeExchangeContext` é o único argumento passado para `OAuthHandler.ExchangeCodeAsync`.

#### <a name="reason-for-change"></a>Motivo da alteração

Essa alteração permite que parâmetros adicionais sejam fornecidos de forma não-significativa. Não há necessidade de criar novas sobrecargas `ExchangeCodeAsync`.

#### <a name="recommended-action"></a>Ação recomendada

Construa um `OAuthCodeExchangeContext` com os valores de `code` e `redirectUri` apropriados. Uma instância <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> deve ser fornecida. Essa instância única `OAuthCodeExchangeContext` pode ser passada para `OAuthHandler.ExchangeCodeAsync` em vez de vários argumentos.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
