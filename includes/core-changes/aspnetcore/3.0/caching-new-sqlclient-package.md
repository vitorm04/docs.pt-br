---
ms.openlocfilehash: 32c7f4e9e4736145f9275b74f34c04404e7c770a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394011"
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

Os clientes não devem precisar se preocupar com essa alteração significativa, a menos que estejam usando tipos retornados pelo pacote `Microsoft.Extensions.Caching.SqlServer` e convertendo-os em tipos `System.Data.SqlClient`. Por exemplo, se alguém estivesse convertendo um `DbConnection` para o [tipo SqlConnection antigo](xref:System.Data.SqlClient.SqlConnection), ele precisaria alterar a conversão para o novo tipo de @no__t 2. 

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
