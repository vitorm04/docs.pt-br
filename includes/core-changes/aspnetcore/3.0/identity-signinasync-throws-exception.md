---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394040"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Identidade: SignInAsync lança exceção para identidade não autenticada

Por padrão, `SignInAsync` lança uma exceção para `IsAuthenticated` diretores /identidades em que é `false`.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

`SignInAsync`aceita quaisquer princípios/identidades, incluindo identidades `IsAuthenticated` `false`em que é .

#### <a name="new-behavior"></a>Novo comportamento

Por padrão, `SignInAsync` lança uma exceção para `IsAuthenticated` diretores /identidades em que é `false`. Há uma nova bandeira para suprimir esse comportamento, mas o comportamento padrão mudou.

#### <a name="reason-for-change"></a>Motivo da mudança

O comportamento antigo era problemático porque, por padrão, `[Authorize]`  /  `RequireAuthenticatedUser()`esses diretores eram rejeitados por .

#### <a name="recommended-action"></a>Ação recomendada

Em ASP.NET Core 3.0 Preview 6, `AuthenticationOptions` há `true` uma `RequireAuthenticatedSignIn` bandeira que é por padrão. Coloque esta `false` bandeira para restaurar o velho comportamento.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
