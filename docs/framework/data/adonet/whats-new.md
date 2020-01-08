---
title: Novidades no ADO.NET
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: db903f801994202ac50ac72ad5352f20367efed7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337017"
---
# <a name="whats-new-in-adonet"></a>Novidades no ADO.NET

Os recursos a seguir são novos no ADO.NET no .NET Framework 4,5.

## <a name="sqlclient-data-provider"></a>Provedor de Dados SqlClient

Os recursos a seguir são novos no .NET Framework Provedor de Dados para SQL Server no .NET Framework 4,5:

- As palavras-chaves de cadeia de caracteres de conexão ConnectRetryCount e ConnectRetryInterval (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) permitem controlar o recurso de resiliência de conexão ociosa.

- O suporte de streaming de SQL Server para um aplicativo dá suporte a cenários em que os dados no servidor não são estruturados.  Consulte [suporte a streaming SqlClient](sqlclient-streaming-support.md) para obter mais informações.

- O suporte foi adicionado para programação assíncrona.  Consulte [programação assíncrona](asynchronous-programming.md) para obter mais informações.

- As falhas de conexão não serão registradas no log de eventos estendido. Para obter mais informações, consulte [Rastreamento de dados no ADO.NET](data-tracing.md).

- O SqlClient agora tem suporte para a alta disponibilidade do SQL Server, o recurso de recuperação de desastre, AlwaysOn. Para obter mais informações, consulte [suporte a SqlClient para alta disponibilidade e recuperação de desastre](./sql/sqlclient-support-for-high-availability-disaster-recovery.md).

- Uma senha pode ser passada como um <xref:System.Security.SecureString> ao usar a autenticação SQL Server. Consulte <xref:System.Data.SqlClient.SqlCredential> para obter mais informações.

- Quando `TrustServerCertificate` é false e `Encrypt` é true, o nome do servidor (ou endereço IP) em um certificado SQL Server SSL deve corresponder exatamente ao nome do servidor (ou endereço IP) especificado na cadeia de conexão. Caso contrário, a tentativa de conexão falhará. Para obter mais informações, consulte a descrição da opção de conexão de `Encrypt` em <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

  Se esta alteração fizer um aplicativo existente não se conectar mais, você poderá corrigir o aplicativo usando um desses procedimentos:

  - Emita um certificado que especifica o nome curto no campo Nome Comum (CN) ou Nome Alternativo da Entidade (SAN). Esta solução funcionará para o espelhamento do banco de dados.

  - Adicione um alias que mapeia o nome curto para o nome de domínio totalmente qualificado.

  - Use o nome de domínio totalmente qualificado na cadeia de conexão.

- O SqlClient dá suporte à Proteção Estendido. Para obter mais informações sobre a proteção estendida, consulte [conectando-se ao mecanismo de banco de dados usando a proteção estendida](/sql/database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection).

- O SqlClient dá suporte a conexões com bancos de dados LocalDB. Para obter mais informações, consulte [suporte a SqlClient para LocalDB](./sql/sqlclient-support-for-localdb.md).

- `Type System Version=SQL Server 2012;` é o novo valor para passar para a propriedade de conexão `Type System Version`. O valor `Type System Version=Latest;` agora é obsoleto e agora é equivalente ao `Type System Version=SQL Server 2008;`. Para obter mais informações, consulte <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

- O SqlClient fornece suporte adicional a colunas esparsas, um recurso que foi adicionado no SQL Server 2008. Se o seu aplicativo já acessa dados em uma tabela que usa colunas esparsas, você deverá ver uma melhora no desempenho. A coluna IsColumnSet do <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> indica se uma coluna é uma esparsa que é membro de um conjunto de colunas. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> indica se uma coluna é uma coluna esparsa (consulte [SQL Server coleções de esquema](sql-server-schema-collections.md) para obter mais informações). Para obter mais informações sobre colunas esparsas, consulte [usar colunas esparsas](/sql/relational-databases/tables/use-sparse-columns).

- O assembly Microsoft.SqlServer.Types.dllque contém os tipos de dados espaciais foi atualizado da versão 10.0 para a versão 11.0. Os aplicativos que fazem referência a esse assembly podem falhar. Para obter mais informações, consulte [alterações recentes em recursos de mecanismo de banco de dados](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/ms143179(v=sql.110)).

## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework

O .NET Framework 4,5 adiciona APIs que habilitam novos cenários ao trabalhar com o Entity Framework 5,0. Para obter mais informações sobre melhorias e recursos que foram adicionados ao Entity Framework 5,0, consulte os seguintes tópicos: [novidades](https://docs.microsoft.com/previous-versions/gg696190(v=vs.103)) e [Entity Framework versões e controle de versão](/ef/ef6/what-is-new/past-releases).

## <a name="see-also"></a>Veja também

- [ADO.NET](index.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
- [SQL Server and ADO.NET](./sql/index.md) (SQL Server e ADO.NET)
- [O que há de novo no WCF Data Services 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
