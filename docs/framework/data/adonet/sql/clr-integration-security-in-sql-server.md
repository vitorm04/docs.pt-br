---
title: Segurança da integração CLR no SQL Server
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: e5d15b4e5ac36f7ecddf45179c65a60995a1a578
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147769"
---
# <a name="clr-integration-security-in-sql-server"></a>Segurança da integração CLR no SQL Server

Microsoft SQL Server fornece a integração do componente Common Language Runtime (CLR) do .NET Framework. A integração CLR permite que você escreva procedimentos armazenados, gatilhos, tipos definidos pelo usuário, funções definidas pelo usuário, agregações definidas pelo usuário e funções com valor de tabela de streaming, usando qualquer linguagem de .NET Framework, como o Microsoft Visual Basic .NET ou o Microsoft Visual C#.  
  
 O CLR dá suporte a um modelo de segurança chamado CAS (segurança de acesso do código) para código gerenciado. Nesse modelo, as permissões são concedidas a assemblies com base nas evidências fornecidas pelo código nos metadados. SQL Server integra o modelo de segurança baseado no usuário do SQL Server com o modelo de segurança baseado em acesso ao código do CLR.  
  
## <a name="external-resources"></a>Recursos externos  

 Para obter mais informações sobre a integração CLR com o SQL Server, consulte os recursos a seguir.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Segurança de Acesso do Código](../../../misc/code-access-security.md)|Contém tópicos que descrevem CAS no .NET Framework.|  
|[Segurança da integração CLR](/sql/relational-databases/clr-integration/security/clr-integration-security)|Discute o modelo de segurança para execução de código gerenciado dentro de SQL Server.|  
  
## <a name="see-also"></a>Confira também

- [Protegendo aplicativos ADO.NET](../securing-ado-net-applications.md)
- [Cenários de Segurança de Aplicativo no SQL Server](application-security-scenarios-in-sql-server.md)
- [Integração do Common Language Runtime do SQL](sql-server-common-language-runtime-integration.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
