---
ms.openlocfilehash: 74b989a2413d2192f7cf5208e400eaed879ea096
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198332"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Autorização: implementações de IAuthorizationPolicyProvider exigem novo método

No ASP.NET Core 3,0, um novo método `GetFallbackPolicyAsync` foi adicionado a `IAuthorizationPolicyProvider`. Essa política de fallback é usada pelo middleware de autorização quando nenhuma política é especificada.

Para obter mais informações, consulte [ASPNET/AspNetCore # 9759](https://github.com/aspnet/AspNetCore/pull/9759).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

As implementações de `IAuthorizationPolicyProvider` não exigiam um método `GetFallbackPolicyAsync`.

#### <a name="new-behavior"></a>Novo comportamento

As implementações de `IAuthorizationPolicyProvider` exigem um método `GetFallbackPolicyAsync`.

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
