---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901954"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Autorização: implementações de IAuthorizationPolicyProvider exigem novo método

No ASP.NET Core 3,0, um novo método `GetFallbackPolicyAsync` foi adicionado a `IAuthorizationPolicyProvider`. Essa política de fallback é usada pelo middleware de autorização quando nenhuma política é especificada.

Para obter mais informações, consulte [dotnet/aspnetcore # 9759](https://github.com/dotnet/aspnetcore/pull/9759).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

As implementações de `IAuthorizationPolicyProvider` não exigiam um método `GetFallbackPolicyAsync`.

#### <a name="new-behavior"></a>Novo comportamento

Implementações de `IAuthorizationPolicyProvider` exigem um método `GetFallbackPolicyAsync`.

#### <a name="reason-for-change"></a>Motivo da alteração

Um novo método era necessário para o novo `AuthorizationMiddleware` a ser usado quando nenhuma política é especificada.

#### <a name="recommended-action"></a>Ação recomendada

Adicione o método `GetFallbackPolicyAsync` às suas implementações de `IAuthorizationPolicyProvider`.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
