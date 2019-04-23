---
ms.openlocfilehash: fcaee245e98dfe71beb4042a2664a14b64cf2398
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235061"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection não pode mais se conectar ao SQL Server 1997 ou a bancos de dados usando o adaptador VIA

|   |   |
|---|---|
|Detalhes|Conexões a bancos de dados do SQL Server usando o [Protocolo VIA (Virtual Interface Adapter)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229%28v=sql.105%29) não têm mais suporte. O protocolo usado para se conectar a um banco de dados do SQL Server fica visível na cadeia de conexão. Uma conexão VIA conterá via:&lt;nomedoservidor&gt;. Se o aplicativo estiver se conectando ao SQL usando um protocolo diferente do VIA (tcp: ou np:, por exemplo), nenhuma alteração da falha será encontrada. Além disso, não há suporte para conexões com o SQL Server 7 (1997).|
|Sugestão|O protocolo VIA foi preterido, de modo que um protocolo alternativo deve ser usado para se conectar a bancos de dados SQL. O protocolo mais usado é o TCP/IP. Para obter mais informações sobre como se conectar por meio de TCP/IP, confira [Habilitar o protocolo TCP/IP para uma instância de banco de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)). Se o banco de dados for acessado somente de dentro de uma intranet, o protocolo de pipes compartilhado poderá fornecer um melhor desempenho se a rede estiver lenta.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|
