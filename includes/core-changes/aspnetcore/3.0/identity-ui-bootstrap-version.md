---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394000"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a>Identidade: versão de inicialização padrão da interface do usuário alterada

A partir do ASP.NET Core 3,0, a interface do usuário de identidade usa como padrão a versão 4 da inicialização.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

A chamada do método `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` era a mesma que `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`

#### <a name="new-behavior"></a>Novo comportamento

A chamada do método `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` é a mesma que `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`

#### <a name="reason-for-change"></a>Motivo da alteração

A inicialização 4 foi lançada durante ASP.NET Core período de tempo de 3,0.

#### <a name="recommended-action"></a>Ação recomendada

Você será afetado por essa alteração se usar a interface do usuário de identidade padrão e a tiver adicionado em `Startup.ConfigureServices`, conforme mostrado no exemplo a seguir:

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

Execute uma das seguintes ações:

- Migre seu aplicativo para usar a inicialização 4 usando o [Guia de migração](https://getbootstrap.com/docs/4.0/migration).
- Atualize `Startup.ConfigureServices` para impor o uso da inicialização 3. Por exemplo:

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
