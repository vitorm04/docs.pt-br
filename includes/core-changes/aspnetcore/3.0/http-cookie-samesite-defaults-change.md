---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282517"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a>HTTP: Alguns padrões do Cookie SameSite alterados para Nenhum

`SameSite`é uma opção para cookies que podem ajudar a mitigar alguns ataques de CSRF (Cross-Site Request Forgery). Quando essa opção foi introduzida inicialmente, padrões inconsistentes foram usados em várias APIs ASP.NET Core. A inconsistência levou a resultados confusos. A partir de ASP.NET Core 3.0, esses padrões estão melhor alinhados. Você deve optar por esse recurso por componente.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

As APIs de ASP.NET <xref:Microsoft.AspNetCore.Http.SameSiteMode> semelhantes usavam diferentes valores padrão. Um exemplo da inconsistência é `HttpResponse.Cookies.Append(String, String)` `HttpResponse.Cookies.Append(String, String, CookieOptions)`visto em e `SameSiteMode.None` `SameSiteMode.Lax`, que padrão para e , respectivamente.

#### <a name="new-behavior"></a>Novo comportamento

Todas as APIs `SameSiteMode.None`afetadas padrão para .

#### <a name="reason-for-change"></a>Motivo da mudança

O valor padrão foi `SameSite` alterado para fazer um recurso de opt-in.

#### <a name="recommended-action"></a>Ação recomendada

Cada componente que emite `SameSite` cookies precisa decidir se é apropriado para seus cenários. Revise o uso das APIs `SameSite` afetadas e reconfigure conforme necessário.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
