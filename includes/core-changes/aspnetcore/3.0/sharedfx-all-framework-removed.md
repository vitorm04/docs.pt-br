---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394435"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a>Estrutura compartilhada: Removed Microsoft.AspNetCore.All

A partir de ASP.NET Core `Microsoft.AspNetCore.All` 3.0, `Microsoft.AspNetCore.All` o metapacote e a estrutura compartilhada correspondente não são mais produzidos. Este pacote está disponível em ASP.NET Core 2.2 e continuará recebendo atualizações de manutenção em ASP.NET Core 2.1.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Os aplicativos `Microsoft.AspNetCore.All` podem usar o `Microsoft.AspNetCore.All` metapacote para segmentar a estrutura compartilhada no .NET Core.

#### <a name="new-behavior"></a>Novo comportamento

O .NET Core 3.0 `Microsoft.AspNetCore.All` não inclui uma estrutura compartilhada.

#### <a name="reason-for-change"></a>Motivo da mudança

O `Microsoft.AspNetCore.All` metapacote incluiu um grande número de dependências externas.

#### <a name="recommended-action"></a>Ação recomendada

Migre seu projeto `Microsoft.AspNetCore.App` para usar a estrutura. Os componentes que estavam disponíveis anteriormente ainda `Microsoft.AspNetCore.All` estão disponíveis no NuGet. Esses componentes agora são implantados com seu aplicativo em vez de serem incluídos na estrutura compartilhada.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
