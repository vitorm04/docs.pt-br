---
title: Novidades no ADO.NET
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: 90ac3ffe9bae892bf20ad874e5634a3a045f776d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877428"
---
# <a name="whats-new-in-adonet"></a>Novidades no ADO.NET

Os seguintes recursos são novos no ADO.NET no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].

## <a name="sqlclient-data-provider"></a>Provedor de Dados SqlClient

Os seguintes recursos são novos no .NET Framework Data Provider para SQL Server em [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]:

- As palavras-chaves de cadeia de caracteres de conexão ConnectRetryCount e ConnectRetryInterval (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) permitem controlar o recurso de resiliência de conexão ociosa.

- Suporte a streaming do SQL Server para um aplicativo dá suporte a cenários em que os dados no servidor são não estruturados.  Ver [suporte de Streaming do SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md) para obter mais informações.

- O suporte foi adicionado para programação assíncrona.  Ver [programação assíncrona](../../../../docs/framework/data/adonet/asynchronous-programming.md) para obter mais informações.

- As falhas de conexão não serão registradas no log de eventos estendido. Para obter mais informações, consulte [Rastreamento de dados no ADO.NET](../../../../docs/framework/data/adonet/data-tracing.md).

- SqlClient agora tem suporte do SQL Server alta disponibilidade de recurso de recuperação de desastre, AlwaysOn. Para obter mais informações, consulte [suporte do SqlClient para alta disponibilidade, recuperação de desastres](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

- Uma senha pode ser passada como um <xref:System.Security.SecureString> ao usar a autenticação do SQL Server. Consulte <xref:System.Data.SqlClient.SqlCredential> para obter mais informações.

- Quando `TrustServerCertificate` é false e `Encrypt` for true, o nome do servidor (ou endereço IP) em um certificado SSL do SQL Server deve corresponder exatamente o servidor nome (ou endereço IP) especificado na cadeia de conexão. Caso contrário, a tentativa de conexão falhará. Para obter mais informações, consulte a descrição da opção de conexão de `Encrypt` em <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

  Se esta alteração fizer um aplicativo existente não se conectar mais, você poderá corrigir o aplicativo usando um desses procedimentos:

  - Emita um certificado que especifica o nome curto no campo Nome Comum (CN) ou Nome Alternativo da Entidade (SAN). Esta solução funcionará para o espelhamento do banco de dados.

  - Adicione um alias que mapeia o nome curto para o nome de domínio totalmente qualificado.

  - Use o nome de domínio totalmente qualificado na cadeia de conexão.

- O SqlClient dá suporte à Proteção Estendido. Para obter mais informações sobre a proteção estendida, consulte [conectar-se ao banco de dados de mecanismo de usando proteção estendida](https://go.microsoft.com/fwlink/?LinkId=219978).

- O SqlClient dá suporte a conexões com bancos de dados LocalDB. Para obter mais informações, consulte [suporte do SqlClient para LocalDB](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-localdb.md).

- `Type System Version=SQL Server 2012;` é o novo valor para passar para a propriedade de conexão `Type System Version`. O valor `Type System Version=Latest;` agora é obsoleto e agora é equivalente ao `Type System Version=SQL Server 2008;`. Para obter mais informações, consulte <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

- O SqlClient fornece suporte adicional a colunas esparsas, um recurso que foi adicionado no SQL Server 2008. Se o aplicativo já acessa dados em uma tabela que usa colunas esparsas, você deverá ver um aumento no desempenho. A coluna IsColumnSet do <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> indica se uma coluna é uma esparsa que é membro de um conjunto de colunas. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Indica se uma coluna é uma coluna esparsa (consulte [coleções de esquema do SQL Server](../../../../docs/framework/data/adonet/sql-server-schema-collections.md) para obter mais informações). Para obter mais informações sobre colunas esparsas, consulte [usando colunas esparsas](https://go.microsoft.com/fwlink/?LinkId=224244).

- O Microsoft.SqlServer.Types.dll do assembly, que contém os tipos de dados espaciais, foi atualizada da versão 10.0 para a 11.0. Os aplicativos que fazem referência a esse assembly podem falhar. Para obter mais informações, consulte [alterações recentes em recursos do mecanismo de banco de dados](https://go.microsoft.com/fwlink/?LinkId=224367).

## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework

O [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] adiciona as APIs que permitem que os cenários novos funcionem com o Entity Framework 5.0. Para obter mais informações sobre aprimoramentos e recursos que foram adicionados para o Entity Framework 5.0, consulte os tópicos a seguir: [Quais são as novidades](https://go.microsoft.com/fwlink/?LinkID=251106) e [versões do Entity Framework e controle de versão](https://go.microsoft.com/fwlink/?LinkId=234899).

## <a name="see-also"></a>Consulte também

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET Overview](../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)
- [SQL Server and ADO.NET](../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)
- [O que há de novo no WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
