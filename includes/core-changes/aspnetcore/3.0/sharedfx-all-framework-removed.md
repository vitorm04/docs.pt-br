---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394435"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a>Estrutura compartilhada: Microsoft. AspNetCore. All removido

A partir do ASP.NET Core 3,0, o metapacote `Microsoft.AspNetCore.All` e a estrutura compartilhada `Microsoft.AspNetCore.All` correspondente não são mais produzidos. Este pacote está disponível no ASP.NET Core 2,2 e continuará a receber atualizações de serviço no ASP.NET Core 2,1.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Os aplicativos podem usar o metapacote `Microsoft.AspNetCore.All` para direcionar a estrutura compartilhada `Microsoft.AspNetCore.All` no .NET Core.

#### <a name="new-behavior"></a>Novo comportamento

O .NET Core 3,0 não inclui uma estrutura compartilhada `Microsoft.AspNetCore.All`.

#### <a name="reason-for-change"></a>Motivo da alteração

O metapacote `Microsoft.AspNetCore.All` incluía um grande número de dependências externas.

#### <a name="recommended-action"></a>Ação recomendada

Migre seu projeto para usar a estrutura `Microsoft.AspNetCore.App`. Os componentes que estavam disponíveis anteriormente no `Microsoft.AspNetCore.All` ainda estão disponíveis no NuGet. Esses componentes agora são implantados com seu aplicativo, em vez de serem incluídos na estrutura compartilhada.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
