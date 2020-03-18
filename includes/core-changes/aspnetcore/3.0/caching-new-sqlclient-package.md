---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198338"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Cache: Microsoft.Extensions.Caching.SqlServer usa novo pacote SqlClient

O `Microsoft.Extensions.Caching.SqlServer` pacote usará `Microsoft.Data.SqlClient` o novo `System.Data.SqlClient` pacote em vez de pacote. Essa mudança pode causar pequenas mudanças comportamentais. Para obter mais informações, consulte [Introduzindo o novo Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

O `Microsoft.Extensions.Caching.SqlServer` pacote `System.Data.SqlClient` usou o pacote.

#### <a name="new-behavior"></a>Novo comportamento

`Microsoft.Extensions.Caching.SqlServer`agora está `Microsoft.Data.SqlClient` usando o pacote.

#### <a name="reason-for-change"></a>Motivo da mudança

`Microsoft.Data.SqlClient`é um novo pacote que `System.Data.SqlClient`é construído a partir de . É onde todos os novos trabalhos serão feitos a partir de agora.

#### <a name="recommended-action"></a>Ação recomendada

Os clientes não devem se preocupar com essa mudança de `Microsoft.Extensions.Caching.SqlServer` quebra, a `System.Data.SqlClient` menos que estejam usando tipos devolvidos pelo pacote e lançando-os para tipos. Por exemplo, se alguém `DbConnection` estivesse lançando um para o [antigo tipo SqlConnection,](xref:System.Data.SqlClient.SqlConnection)ele precisaria mudar o elenco para o novo `Microsoft.Data.SqlClient.SqlConnection` tipo.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
