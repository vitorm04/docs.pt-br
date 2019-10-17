---
ms.openlocfilehash: a916af91670dc9c5ceb2ff759cd8ae308fb2c2dc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393924"
---
### <a name="kestrel-connection-adapters-removed"></a>Kestrel: adaptadores de conexão removidos

Como parte da mudança para mover APIs "pubternal" para `public`, o conceito de um `IConnectionAdapter` foi removido de Kestrel. Os adaptadores de conexão estão sendo substituídos pelo middleware de conexão (semelhante ao middleware HTTP no pipeline de ASP.NET Core, mas para conexões de nível inferior). O log de conexão e HTTPS foi movido dos adaptadores de conexão para o middleware de conexão. Esses métodos de extensão devem continuar funcionando sem problemas, mas os detalhes da implementação foram alterados.

Para obter mais informações, consulte [ASPNET/AspNetCore # 11412](https://github.com/aspnet/AspNetCore/pull/11412). Para obter uma discussão, consulte [ASPNET/AspNetCore # 11475](https://github.com/aspnet/AspNetCore/issues/11475).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Os componentes de extensibilidade do Kestrel foram criados usando `IConnectionAdapter`.

#### <a name="new-behavior"></a>Novo comportamento

Os componentes de extensibilidade do Kestrel são criados como [middleware](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="reason-for-change"></a>Motivo da alteração

Essa alteração destina-se a fornecer uma arquitetura de extensibilidade mais flexível.

#### <a name="recommended-action"></a>Ação recomendada

Converta todas as implementações de `IConnectionAdapter` para usar o novo padrão de middleware, conforme mostrado [aqui](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
