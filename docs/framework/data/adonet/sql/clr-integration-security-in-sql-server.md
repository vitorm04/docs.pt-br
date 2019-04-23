---
title: Segurança da integração CLR no SQL Server
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 946401211d515df9ba5b9e38d7cfd10730973b64
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165809"
---
# <a name="clr-integration-security-in-sql-server"></a>Segurança da integração CLR no SQL Server
Microsoft SQL Server fornece a integração do componente do common language runtime (CLR) do .NET Framework. Integração CLR permite que você grave procedimentos armazenados, disparadores, tipos definidos pelo usuário, funções definidas pelo usuário, agregações definidas pelo usuário e streaming funções com valor de tabela, usando qualquer linguagem do .NET Framework, como o Microsoft Visual Basic .NET ou o Microsoft Visual c#.  
  
 O CLR dá suporte a um modelo de segurança denominado segurança de acesso do código (CAS) para código gerenciado. Nesse modelo, as permissões são concedidas a assemblies com base na evidência fornecida pelo código em metadados. SQL Server integra-se o modelo de segurança baseado em usuário do SQL Server com o modelo de segurança baseada em acesso de código do CLR.  
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações sobre a integração de CLR com o SQL Server, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Segurança de acesso do código](../../../../../docs/framework/misc/code-access-security.md)|Contém tópicos que descrevem o CAS no .NET Framework.|  
|[Segurança da integração CLR](/sql/relational-databases/clr-integration/security/clr-integration-security)|Discute o modelo de segurança para código gerenciado em execução dentro do SQL Server.|  
  
## <a name="see-also"></a>Consulte também

- [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Integração do Common Language Runtime ao SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)
- [ADO.NET Overview](../../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)
