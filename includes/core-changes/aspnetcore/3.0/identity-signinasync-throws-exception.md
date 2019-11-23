---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394040"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Identidade: o SignInAsync gera uma exceção para a identidade não autenticada

Por padrão, `SignInAsync` gera uma exceção para entidades/identidades nas quais `IsAuthenticated` é `false`.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

`SignInAsync` aceita quaisquer entidades/identidades, incluindo identidades nas quais `IsAuthenticated` está `false`.

#### <a name="new-behavior"></a>Novo comportamento

Por padrão, `SignInAsync` gera uma exceção para entidades/identidades nas quais `IsAuthenticated` é `false`. Há um novo sinalizador para suprimir esse comportamento, mas o comportamento padrão foi alterado.

#### <a name="reason-for-change"></a>Motivo da alteração

O comportamento antigo era problemático porque, por padrão, essas entidades foram rejeitadas por `[Authorize]` / `RequireAuthenticatedUser()`.

#### <a name="recommended-action"></a>Ação recomendada

No ASP.NET Core 3,0 Preview 6, há um sinalizador de `RequireAuthenticatedSignIn` no `AuthenticationOptions` `true` por padrão. Defina esse sinalizador como `false` para restaurar o comportamento antigo.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
