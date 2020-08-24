---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198338"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Caching: o Microsoft. Extensions. Caching. SqlServer usa o novo pacote SqlClient

O `Microsoft.Extensions.Caching.SqlServer` pacote usará o novo `Microsoft.Data.SqlClient` pacote em vez do `System.Data.SqlClient` pacote. Essa alteração pode causar pequenas alterações significativas no comportamento. Para obter mais informações, consulte [apresentando o novo Microsoft. Data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Versão introduzida

3,0

#### <a name="old-behavior"></a>Comportamento antigo

O `Microsoft.Extensions.Caching.SqlServer` pacote usou o `System.Data.SqlClient` pacote.

#### <a name="new-behavior"></a>Novo comportamento

`Microsoft.Extensions.Caching.SqlServer` Agora está usando o `Microsoft.Data.SqlClient` pacote.

#### <a name="reason-for-change"></a>Motivo da alteração

`Microsoft.Data.SqlClient` é um novo pacote criado do `System.Data.SqlClient` . É aqui que todo o novo recurso funcionará a partir de agora.

#### <a name="recommended-action"></a>Ação recomendada

Os clientes não devem precisar se preocupar com essa alteração significativa, a menos que estejam usando tipos retornados pelo `Microsoft.Extensions.Caching.SqlServer` pacote e convertendo-os em `System.Data.SqlClient` tipos. Por exemplo, se alguém estivesse convertendo um `DbConnection` para o [tipo SqlConnection antigo](xref:System.Data.SqlClient.SqlConnection), ele precisaria alterar a conversão para o novo `Microsoft.Data.SqlClient.SqlConnection` tipo.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
