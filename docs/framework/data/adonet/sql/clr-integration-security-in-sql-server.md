---
title: Segurança da integração CLR no SQL Server
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 4756d13ff52a4c55b48c3ea56d26111029c8a7e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794565"
---
# <a name="clr-integration-security-in-sql-server"></a>Segurança da integração CLR no SQL Server
Microsoft SQL Server fornece a integração do componente Common Language Runtime (CLR) do .NET Framework. A integração CLR permite que você escreva procedimentos armazenados, gatilhos, tipos definidos pelo usuário, funções definidas pelo usuário, agregações definidas pelo usuário e funções com valor de tabela de streaming, usando qualquer linguagem de .NET Framework, como Microsoft Visual Basic .NET ou Microsoft Visual C#.  
  
 O CLR dá suporte a um modelo de segurança chamado CAS (segurança de acesso do código) para código gerenciado. Nesse modelo, as permissões são concedidas a assemblies com base nas evidências fornecidas pelo código nos metadados. SQL Server integra o modelo de segurança baseado no usuário do SQL Server com o modelo de segurança baseado em acesso ao código do CLR.  
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações sobre a integração CLR com o SQL Server, consulte os recursos a seguir.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Segurança de acesso do código](../../../misc/code-access-security.md)|Contém tópicos que descrevem CAS no .NET Framework.|  
|[Segurança de integração CLR](/sql/relational-databases/clr-integration/security/clr-integration-security)|Discute o modelo de segurança para execução de código gerenciado dentro de SQL Server.|  
  
## <a name="see-also"></a>Consulte também

- [Securing ADO.NET Applications](../securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [Cenários de segurança do aplicativo no SQL Server](application-security-scenarios-in-sql-server.md)
- [Integração do Common Language Runtime ao SQL Server](sql-server-common-language-runtime-integration.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
