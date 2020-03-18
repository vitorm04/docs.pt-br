---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901954"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Autorização: Implementações do IAuthorizationPolicyProvider exigem um novo método

Em ASP.NET Núcleo 3.0, um `GetFallbackPolicyAsync` `IAuthorizationPolicyProvider`novo método foi adicionado a . Esta política de recuo é usada pelo middleware de autorização quando nenhuma política é especificada.

Para obter mais informações, consulte [dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Implementações `IAuthorizationPolicyProvider` de não requerem `GetFallbackPolicyAsync` um método.

#### <a name="new-behavior"></a>Novo comportamento

Implementações `IAuthorizationPolicyProvider` requerem `GetFallbackPolicyAsync` um método.

#### <a name="reason-for-change"></a>Motivo da mudança

Um novo método foi `AuthorizationMiddleware` necessário para que o novo seja usado quando nenhuma política for especificada.

#### <a name="recommended-action"></a>Ação recomendada

Adicione `GetFallbackPolicyAsync` o método às `IAuthorizationPolicyProvider`suas implementações de .

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
