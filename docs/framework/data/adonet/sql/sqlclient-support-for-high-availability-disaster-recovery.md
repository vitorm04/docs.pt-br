---
title: Suporte do SqlClient para alta disponibilidade, recuperação de desastre
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: b01db93c51c6d975c9cc951f08b64c5ffd6c1de4
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380007"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>Suporte do SqlClient para alta disponibilidade, recuperação de desastre
Este tópico discute o suporte do SqlClient (adicionado no .NET Framework 4.5) para recuperação de desastres de alta disponibilidade – grupos de disponibilidade AlwaysOn.  O recurso de grupos de disponibilidade AlwaysOn foi adicionado ao SQL Server 2012. Para obter mais informações sobre grupos de disponibilidade AlwaysOn, consulte os Manuais Online do SQL Server.  
  
 Agora você pode especificar o ouvinte do grupo de disponibilidade de uma (alta disponibilidade, recuperação de desastres) (AG) do grupo de disponibilidade ou instância de Cluster de Failover do SQL Server 2012 na propriedade de conexão. Se um aplicativo SqlClient está conectado a um banco de dados AlwaysOn que realiza failover, a conexão original será interrompida e o aplicativo deverá abrir uma nova conexão para continuar o trabalho após o failover.  
  
 Se você não estiver se conectando a um ouvinte do grupo de disponibilidade ou instância de Cluster de Failover do SQL Server 2012 e se vários endereços IP estiverem associados um nome de host, SqlClient percorrerá sequencialmente todos os endereços IP associados à entrada DNS. Isso pode ser demorado se o primeiro endereço IP retornado pelo servidor DNS não estiver associado a nenhuma placa de interface de rede (NIC). Ao se conectar a um ouvinte de grupo de disponibilidade ou instância de Cluster de Failover do SQL Server 2012, o SqlClient tenta estabelecer conexões com todos os endereços IP em paralelo e se uma tentativa de conexão for bem-sucedida, o driver descartará qualquer conexão pendente as tentativas.  
  
> [!NOTE]
>  Aumentar o tempo limite de conexão e implementar lógica de novas tentativas de conexão aumenta a probabilidade de um aplicativo conectar-se a um grupo de disponibilidade. Além disso, como uma conexão pode falhar devido a um failover, você deve implementar lógica de novas tentativas de conexão, repetindo uma conexão falha até que ela se reconecte.  
  
 As propriedades de conexão a seguir foram adicionadas ao SqlClient no .NET Framework 4.5:  
  
- `ApplicationIntent`  
  
- `MultiSubnetFailover`  
  
 Você pode modificar essas palavras-chave de cadeia de caracteres de conexão por meio de programação com:  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
>  Definindo `MultiSubnetFailover` para `true` não é necessária com o .NET Framework 4.6.1 ou versões posteriores.
  
## <a name="connecting-with-multisubnetfailover"></a>Conectar-se ao MultiSubnetFailover  
 Sempre especifique `MultiSubnetFailover=True` ao se conectar a um ouvinte de grupo de disponibilidade do SQL Server 2012 ou uma instância de Cluster de Failover do SQL Server 2012. `MultiSubnetFailover` permite failover mais rápido para grupos de disponibilidade todas as e ou instância de Cluster de Failover em SQL Server 2012 e reduzir significativamente o tempo de failover para topologias AlwaysOn únicas e de várias sub-redes. Durante um failover com várias sub-redes, o cliente tentará realizar conexões em paralelo. Durante um failover de sub-rede, ele tentará agressivamente realizar a conexão TCP.  
  
 O `MultiSubnetFailover` propriedade de conexão indica que o aplicativo está sendo implantado em um grupo de disponibilidade ou instância de Cluster de Failover do SQL Server 2012 e que o SqlClient tentará se conectar ao banco de dados na instância do SQL Server primário tentando Conecte-se a todos os endereços IP. Quando `MultiSubnetFailover=True` é especificado para uma conexão, o cliente tenta novamente realizar a conexão TCP mais rapidamente do que os intervalos de retransmissão de TCP do padrão do sistema operacional. Isso permite que uma reconexão mais rápida após o failover de um Grupo de Disponibilidade AlwaysOn ou uma Instância de Cluster de Failover AlwaysOn, e é aplicável a Grupos de Disponibilidade de sub-rede único Instâncias de Cluster de Failover.  
  
 Para obter mais informações sobre palavras-chave de cadeia de caracteres de conexão no SqlClient, consulte <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Especificando `MultiSubnetFailover=True` quando conexão a algo que não seja um ouvinte de grupo de disponibilidade ou instância de Cluster de Failover do SQL Server 2012 pode resultar em um impacto negativo no desempenho e não é suportado.  
  
 Use as diretrizes a seguir para se conectar a um servidor em um grupo de disponibilidade ou instância de Cluster de Failover do SQL Server 2012:  
  
- Use a propriedade de conexão `MultiSubnetFailover` ao conectar-se a uma sub-rede única ou a várias. Isso melhora o desempenho para ambos os casos.  
  
- Para conectar-se a um grupo de disponibilidade, especifique o ouvinte de grupo de disponibilidade do grupo de disponibilidade como servidor na cadeia de caracteres de conexão.  
  
- Conectando a um servidor SQL instância configurada com mais de 64 endereços IP causará uma falha de conexão.  
  
- Comportamento de um aplicativo que usa o `MultiSubnetFailover` propriedade de conexão não é afetada com base no tipo de autenticação: Autenticação do SQL Server, a autenticação Kerberos ou autenticação do Windows.  
  
- Aumente o valor de `Connect Timeout` para compensar o tempo de failover e reduzir as tentativas de conexão do aplicativo.  
  
- Não há suporte para transações distribuídas.  
  
 Se o roteamento de somente leitura não estiver em vigor, conectar-se a um local de réplica secundário falhará nas seguintes situações:  
  
1. Se o local de réplica secundário não estiver configurado para aceitar conexões.  
  
2. Se um aplicativo usar `ApplicationIntent=ReadWrite` (discutido abaixo) e o local de réplica secundário estiver configurado para acesso de somente leitura.  
  
 <xref:System.Data.SqlClient.SqlDependency> não é suportado em réplicas secundárias de somente leitura.  
  
 Uma conexão falhará se a réplica primária estiver configurada para rejeitar as cargas de trabalho de somente leitura e a cadeia de caracteres da conexão contém `ApplicationIntent=ReadOnly`.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Atualizando para usar vários clusters de sub-redes do espelhamento do banco de dados  
 Um erro de conexão (<xref:System.ArgumentException>) ocorrerá se as palavras-chave de conexão `MultiSubnetFailover` e `Failover Partner` estiverem presentes na cadeia de conexão, ou se `MultiSubnetFailover=True` e um protocolo diferente do TCP for usado. Um erro (<xref:System.Data.SqlClient.SqlException>) também ocorrerá se `MultiSubnetFailover` é usado e o SQL Server retorna uma resposta de parceiro de failover indicando que ela faz parte de um par de espelhamento de banco de dados.  
  
 Se você atualizar um aplicativo SqlClient que atualmente usa o espelhamento de banco de dados para um cenário de várias sub-redes, deverá remover a propriedade de conexão `Failover Partner` e substituí-la por `MultiSubnetFailover` definida como `True`, além de substituir o nome do servidor na cadeia de conexão por um ouvinte do grupo de disponibilidade. Se uma cadeia de conexão usar `Failover Partner` e `MultiSubnetFailover=True`, o driver gerará um erro. No entanto, se uma cadeia de conexão usa `Failover Partner` e `MultiSubnetFailover=False` (ou `ApplicationIntent=ReadWrite`), o aplicativo irá usar o espelhamento de banco de dados.  
  
 O driver retornará um erro se o espelhamento do banco de dados for usado no banco de dados primário na AG e se `MultiSubnetFailover=True` for usado na cadeia de conexão que se conecta a um banco de dados principal, em vez de um ouvinte de grupo de disponibilidade.  
  
## <a name="specifying-application-intent"></a>Especificando a intenção do aplicativo  
 Quando `ApplicationIntent=ReadOnly`, o cliente solicita uma carga de trabalho de leitura ao se conectar a um banco de dados habilitado para AlwaysOn. O servidor irá impor a intenção no momento da conexão e durante uma instrução de banco de dados USE, mas apenas para um banco de dados habilitado para AlwaysOn.  
  
 A palavra-chave `ApplicationIntent` não funciona com bancos de dados legados de somente leitura.  
  
 Um banco de dados pode permitir ou impedir cargas de trabalho de leitura no banco de dados AlwaysOn de destino. (Isso é feito com a cláusula `ALLOW_CONNECTIONS` das instruções `PRIMARY_ROLE` e `SECONDARY_ROLE`[!INCLUDE[tsql](../../../../../includes/tsql-md.md)].)  
  
 A palavra-chave `ApplicationIntent` é usada para ativar o roteamento de somente leitura.  
  
## <a name="read-only-routing"></a>Roteamento de somente leitura  
 Roteamento de somente leitura é um recurso que pode garantir a disponibilidade de uma réplica de somente leitura de um banco de dados. Para habilitar o roteamento de somente leitura:  
  
1. Você deve se conectar a um ouvinte do Grupo de Disponibilidade Always On.  
  
2. A palavra-chave da cadeia de conexão `ApplicationIntent` deve ser definida como `ReadOnly`.  
  
3. O Grupo de Disponibilidade deve ser configurado pelo administrador do banco de dados para habilitar o roteamento de somente leitura.  
  
 É possível que várias conexões usando o roteamento de somente leitura serão não se conectam à mesma réplica somente leitura. Alterações na sincronização ou alteração de banco de dados na configuração de roteamento do servidor podem resultar em conexões de cliente para diferentes réplicas somente leitura. Para garantir que todas as solicitações de somente leitura se conectem à mesma réplica somente leitura, não passe um ouvinte de grupo de disponibilidade para a palavra-chave da cadeia de conexão `Data Source`. Em vez disso, especifique o nome da instância de somente leitura.  
  
 O roteamento de somente leitura pode demorar mais do que a conexão principal porque ele primeiro se conecta ao primário e, em seguida, procura o melhor secundário legível disponível. Por isso, aumente o tempo limite de logon.  
  
## <a name="see-also"></a>Consulte também

- [SQL Server Features and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md) (Recursos do SQL Server e o ADO.NET)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
