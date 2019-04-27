---
title: Segurança do SQL Server Express
ms.date: 03/30/2017
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
ms.openlocfilehash: f4291de89b397f60aedd35b89d6aa3130d348be5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876779"
---
# <a name="sql-server-express-security"></a>Segurança do SQL Server Express
O Microsoft SQL Server Express Edition (SQL Server Express) é baseado no Microsoft SQL Server, e dá suporte à maioria dos recursos do mecanismo de banco de dados. Ele foi criado de forma que os recursos insuficientes e a conectividade de rede sejam desativadas por padrão. Isso reduz a área da superfície disponível para ataque por um usuário mal-intencionado.  
  
 O SQL Server Express é normalmente instalado como uma instância nomeada. O nome padrão da instância é `SQLExpress`. Uma instância nomeada é identificada pelo nome de rede do computador e o nome da instância que você especifica durante a instalação.  
  
## <a name="network-access"></a>Acesso de rede  
 Por razões de segurança, os protocolos de rede são desabilitados por padrão no SQL Server Express. Isso impede ataques de usuários externos que possam comprometer o computador que hospeda a instância do SQL Server Express. Você deve habilitar explicitamente a conectividade de rede e iniciar o serviço do navegador do SQL Server para se conectar a uma instância do SQL Server Express de outro computador.  
  
 Assim que a conectividade de rede estiver habilitada, uma instância do SQL Server Express terá os mesmos requisitos de segurança que as outras edições do SQL Server.  
  
## <a name="user-instances"></a>Instâncias de usuário  
 Uma instância de usuário é uma instância separada do Mecanismo de Banco de Dados SQL Server Express que é gerado por uma instância pai do SQL Server Express. O principal objetivo de uma instância de usuário é permitir que os usuários que estão executando o Windows com uma conta de usuário com menos privilégios tenham privilégios de administrador do sistema (`sysadmin`) na instância do SQL Server Express no computador local. As instâncias de usuário não são destinadas para os usuários que são administradores do sistema em seus próprios computadores.  
  
 Uma instância de usuário é gerada de uma instância primária do SQL Server ou do SQL Server Express em nome de um usuário. Ela é executada como um processo de usuário no contexto de segurança do Windows do usuário, não como um serviço. Os logons do SQL Server não são permitidos; somente logons do Windows têm suporte. Isso impede o software que está sendo executado em uma instância de usuário de fazer alterações no sistema que o usuário não teria permissões para fazer. Uma instância de usuário também é conhecida como instância filha ou cliente, e às vezes é conhecida pela utilização do acrônimo de RANU (“executar como usuário normal”).  
  
 Cada instância de usuário é isolada de sua instância pai e de outras instâncias de usuário que são executadas no mesmo computador. Os bancos de dados instalados em instâncias de usuário estão abertos somente no modo de usuário único; vários usuários não podem se conectar a eles. A replicação, as consultas distribuídas e as conexões remotas são desativadas para instâncias de usuário. Quando conectados a uma instância de usuário, os usuários não têm nenhum privilégio especial na instância pai do SQL Server Express.  
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações sobre o SQL Server Express, consulte os seguintes recursos.  
  
|||  
|-|-|  
|[Microsoft SQL Server 2005 Express Edition Manuais Online](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms165706(v=sql.90))|Documentação completa do SQL Server 2005 Express Edition.|  
|[Instâncias de usuário para não administradores](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms143684(v=sql.100)) nos Manuais Online do SQL Server|Descreve como criar e implantar instâncias de usuário.|  
|[Instâncias do usuário do SQL Server Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)|Descreve recursos de instância de usuário em um aplicativo do ADO.NET. Fornece informações sobre como habilitar uma instância de usuário, conectar-se a uma instância de usuário usando um <xref:System.Data.SqlClient.SqlConnection>, o tempo de vida da instância de usuário e os cenários de instância de usuário.|  
  
## <a name="see-also"></a>Consulte também

- [SQL Server Security](../../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)
- [Instâncias do usuário do SQL Server Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
