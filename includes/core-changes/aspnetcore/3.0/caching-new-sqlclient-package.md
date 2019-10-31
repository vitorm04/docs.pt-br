---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198338"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Caching: o Microsoft. Extensions. Caching. SqlServer usa o novo pacote SqlClient

O pacote `Microsoft.Extensions.Caching.SqlServer` usará o novo pacote `Microsoft.Data.SqlClient` em vez do pacote `System.Data.SqlClient`. Essa alteração pode causar pequenas alterações significativas no comportamento. Para obter mais informações, consulte [apresentando o novo Microsoft. Data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

O pacote `Microsoft.Extensions.Caching.SqlServer` usou o pacote `System.Data.SqlClient`.

#### <a name="new-behavior"></a>Novo comportamento

`Microsoft.Extensions.Caching.SqlServer` agora está usando o pacote `Microsoft.Data.SqlClient`.

#### <a name="reason-for-change"></a>Motivo da alteração

`Microsoft.Data.SqlClient` é um novo pacote criado de `System.Data.SqlClient`. É aqui que todo o novo recurso funcionará a partir de agora.

#### <a name="recommended-action"></a>Ação recomendada

Os clientes não devem precisar se preocupar com essa alteração significativa, a menos que estejam usando tipos retornados pelo pacote `Microsoft.Extensions.Caching.SqlServer` e convertendo-os em tipos `System.Data.SqlClient`. Por exemplo, se alguém estivesse convertendo um `DbConnection` para o [tipo SqlConnection antigo](xref:System.Data.SqlClient.SqlConnection), ele precisaria alterar a conversão para o novo tipo de `Microsoft.Data.SqlClient.SqlConnection`.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
