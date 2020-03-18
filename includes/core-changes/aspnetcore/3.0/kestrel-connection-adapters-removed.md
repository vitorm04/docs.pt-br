---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901824"
---
### <a name="kestrel-connection-adapters-removed"></a>Kestrel: Adaptadores de conexão removidos

Como parte do movimento para mover APIs "pubternais" para `public`, o conceito de um `IConnectionAdapter` foi removido de Kestrel. Os adaptadores de conexão estão sendo substituídos por middleware de conexão (semelhante ao middleware HTTP no ASP.NET pipeline Core, mas para conexões de nível inferior). O registro https e de conexão passou de adaptadores de conexão para middleware de conexão. Esses métodos de extensão devem continuar funcionando perfeitamente, mas os detalhes da implementação mudaram.

Para obter mais informações, consulte [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412). Para discussão, consulte [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Os componentes de extensibilidade `IConnectionAdapter`kestrel foram criados usando .

#### <a name="new-behavior"></a>Novo comportamento

Os componentes de extensibilidade kestrel são criados como [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="reason-for-change"></a>Motivo da mudança

Esta mudança visa fornecer uma arquitetura de extensibilidade mais flexível.

#### <a name="recommended-action"></a>Ação recomendada

Converta quaisquer `IConnectionAdapter` implementações para usar o novo padrão de middleware como mostrado [aqui](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
