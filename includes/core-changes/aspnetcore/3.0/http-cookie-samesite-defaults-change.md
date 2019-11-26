---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74282517"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a>HTTP: alguns padrões de SameSite de cookie foram alterados para nenhum

`SameSite` é uma opção para cookies que podem ajudar a atenuar ataques de solicitação entre sites forjados (CSRF). Quando essa opção foi introduzida inicialmente, padrões inconsistentes foram usados em várias APIs de ASP.NET Core. A inconsistência levou a resultados confusos. A partir do ASP.NET Core 3,0, esses padrões são mais alinhados. Você deve aceitar esse recurso em uma base por componente.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

APIs ASP.NET Core semelhantes usavam valores de <xref:Microsoft.AspNetCore.Http.SameSiteMode> padrão diferentes. Um exemplo da inconsistência é visto em `HttpResponse.Cookies.Append(String, String)` e `HttpResponse.Cookies.Append(String, String, CookieOptions)`, que tem como padrão `SameSiteMode.None` e `SameSiteMode.Lax`, respectivamente.

#### <a name="new-behavior"></a>Novo comportamento

Todas as APIs afetadas têm como padrão `SameSiteMode.None`.

#### <a name="reason-for-change"></a>Motivo da alteração

O valor padrão foi alterado para fazer `SameSite` um recurso de aceitação.

#### <a name="recommended-action"></a>Ação recomendada

Cada componente que emite cookies precisa decidir se `SameSite` é apropriado para seus cenários. Examine o uso das APIs afetadas e reconfigure `SameSite` conforme necessário.

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
