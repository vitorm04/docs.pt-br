---
title: "Segurança da integração CLR no SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d4364e35bbce3261c8f6e6c45002d5a603007b85
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="clr-integration-security-in-sql-server"></a>Segurança da integração CLR no SQL Server
Microsoft SQL Server fornece a integração do componente de tempo de execução (CLR) de linguagem comum do .NET Framework. Integração CLR permite que você grave procedimentos armazenados, disparadores, tipos definidos pelo usuário, funções definidas pelo usuário, agregações definidas pelo usuário e streaming funções com valor de tabela, usando qualquer linguagem do .NET Framework, como o Microsoft Visual Basic .NET ou o Microsoft Visual c#.  
  
 O CLR oferece suporte a um modelo de segurança denominado segurança de acesso ao código (CAS) para código gerenciado. Nesse modelo, as permissões são concedidas a assemblies com base na evidência fornecida pelo código nos metadados. SQL Server integra-se o modelo de segurança com base em usuário do SQL Server com o modelo de segurança baseada em acesso de código do CLR.  
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações sobre a integração de CLR com o SQL Server, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Segurança de acesso do código](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03)|Contém tópicos que descrevem o CAS no .NET Framework.|  
|[Segurança da integração CLR](http://go.microsoft.com/fwlink/?LinkId=59998)|Discute o modelo de segurança para código gerenciado em execução dentro do SQL Server.|  
  
## <a name="see-also"></a>Consulte também  
 [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Integração do Common Language Runtime ao SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
