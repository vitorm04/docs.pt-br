---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394000"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a>Identidade: Versão padrão do Bootstrap da interface do ui alterada

A partir de ASP.NET Core 3.0, a Interface do Usuário de Identidade não usa a versão 4 do Bootstrap.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

A `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` chamada do método era a mesma que`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`

#### <a name="new-behavior"></a>Novo comportamento

A `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` chamada do método é a mesma que`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`

#### <a name="reason-for-change"></a>Motivo da mudança

Bootstrap 4 foi lançado durante ASP.NET período de tempo do Core 3.0.

#### <a name="recommended-action"></a>Ação recomendada

Você será impactado por essa alteração se usar a ui `Startup.ConfigureServices` de identidade padrão e adicioná-la como mostrado no exemplo a seguir:

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

Execute uma das seguintes ações:

- Migre seu aplicativo para usar o Bootstrap 4 usando seu [guia de migração](https://getbootstrap.com/docs/4.0/migration).
- Atualização `Startup.ConfigureServices` para reforçar o uso do Bootstrap 3. Por exemplo: 

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
