---
title: Assinando procedimentos armazenados no SQL Server
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b3d90579e28fde40d461bdb511d797e5d7f6f179
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="signing-stored-procedures-in-sql-server"></a>Assinando procedimentos armazenados no SQL Server
Você pode assinar um procedimento armazenado com um certificado ou uma chave assimétrica. Isso é criado para cenários quando as permissões não podem ser herdadas pelo encadeamento de propriedade ou quando a cadeia de propriedade é quebrada, como SQL dinâmico. Você cria um usuário mapeado para o certificado, concedendo permissões de usuário do certificado nos objetos que o procedimento armazenado precisa acessar.  
  
 Quando o procedimento armazenado é executado, o SQL Server combina as permissões do usuário do certificado com as do chamador. Ao contrário da cláusula EXECUTE AS, ele não altera o contexto de execução do procedimento. As funções internas que retornam o logon e os nomes de usuário retornam o nome do chamador, não o nome do usuário do certificado.  
  
 Uma assinatura digital é um resumo dos dados criptografados com a chave privada do assinante. A chave privada garante que a assinatura digital seja exclusiva de seu portador ou proprietário. Você pode assinar procedimentos armazenados, funções ou gatilhos.  
  
> [!NOTE]
>  Você pode criar um certificado no banco de dados mestre para conceder permissões de nível de servidor.  
  
## <a name="creating-certificates"></a>Criando certificados  
 Quando você assina um procedimento armazenado com um certificado, um resumo dos dados que consiste em hash criptografado do código do procedimento armazenado é criado usando a chave privada. Em tempo de execução, o resumo dos dados é criptografado com a chave pública e comparado com o valor de hash do procedimento armazenado. Alterar o procedimento armazenado invalida o valor de hash de modo que a assinatura digital não corresponda. Isso impedirá que alguém que não tenha acesso à chave privada altere o código do procedimento armazenado. Portanto, você deve reassinar o procedimento sempre que modificá-lo.  
  
 Há quatro etapas envolvidas na assinatura de um módulo:  
  
1.  Criar um certificado usando a instrução Transact-SQL `CREATE CERTIFICATE [certificateName]`. Essa instrução tem várias opções para definir uma data inicial e final e uma senha. A data de validade padrão é um ano  
  
2.  Crie um usuário de banco de dados associado ao certificado usando a instrução Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]`. Este usuário somente existe no banco de dados e não está associado a um logon.  
  
3.  Conceder ao usuário do certificado as permissões necessárias nos objetos de banco de dados.  
  
> [!NOTE]
>  Um certificado não pode conceder permissões a um usuário que tem permissões revogadas usando a instrução DENY. DENY sempre terá precedência sobre GRANT, impedindo que o chamador herde as permissões concedidas ao usuário do certificado.  
  
1.  Assinar o procedimento armazenado com o certificado usando a instrução Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]`.  
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Assinatura de módulo](http://go.microsoft.com/fwlink/?LinkId=98590) nos Manuais Online do SQL Server|Descreve a assinatura do módulo, fornecendo um cenário de exemplo e links para tópicos relevantes do Transact-SQL.|  
|[Procedimentos armazenados com um certificado de assinatura](http://msdn.microsoft.com/library/bb283630.aspx) nos Manuais Online do SQL Server|Fornece um tutorial para assinar um procedimento armazenado com um certificado.|  
  
## <a name="see-also"></a>Consulte também  
 [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [Visão geral de segurança do SQL Server](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Gerenciando permissões com procedimentos armazenados no SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Escrevendo SQL dinâmico seguro no SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Personalizando permissões com representação no SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [Modificando dados com procedimentos armazenados](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
