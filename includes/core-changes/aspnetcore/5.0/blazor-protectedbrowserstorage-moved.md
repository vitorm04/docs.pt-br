---
ms.openlocfilehash: a9545c66d3873b5114fe66e13c77ddc28e20020e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077599"
---
### <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a>Mais incrivelmente: o recurso ProtectedBrowserStorage mudou para a estrutura compartilhada

Como parte da versão do ASP.NET Core RC2 5,0, o `ProtectedBrowserStorage` recurso foi movido para a estrutura compartilhada ASP.NET Core.

#### <a name="version-introduced"></a>Versão introduzida

5,0 RC2

#### <a name="old-behavior"></a>Comportamento antigo

No ASP.NET Core 5,0 Preview 8, o recurso está disponível como parte do pacote [Microsoft. AspNetCore. Components. Web. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) , mas só pode ser usado no Webassembly de mais incrivelmente.

No ASP.NET Core 5,0 RC1, o recurso está disponível como parte do pacote [Microsoft. AspNetCore. Components. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) , que faz referência à `Microsoft.AspNetCore.App` estrutura compartilhada.

#### <a name="new-behavior"></a>Novo comportamento

No ASP.NET Core 5,0 RC2, uma referência de pacote NuGet não é mais necessária para referenciar e usar o recurso.

#### <a name="reason-for-change"></a>Motivo da alteração

A mudança para a estrutura compartilhada é uma melhor opção para a experiência do usuário que os clientes esperam.

#### <a name="recommended-action"></a>Ação recomendada

Se estiver atualizando do ASP.NET Core 5,0 RC1, conclua as seguintes etapas:

1. Remova a `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` referência do pacote do projeto.
1. Substitua `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` por `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.
1. Remova a chamada de `AddProtectedBrowserStorage` de sua `Startup` classe.

Se estiver atualizando do ASP.NET Core 5,0 Preview 8, conclua as seguintes etapas:

1. Remova a `Microsoft.AspNetCore.Components.Web.Extensions` referência do pacote do projeto.
1. Substitua `using Microsoft.AspNetCore.Components.Web.Extensions;` por `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.
1. Remova a chamada de `AddProtectedBrowserStorage` de sua `Startup` classe.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!--

#### Affected APIs

Not detectable via API analysis

-->
