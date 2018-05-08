---
title: Assinando procedimentos armazenados no SQL Server
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: 98dfaa6d5293cb1ad85f70be3388fb333daef373
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="signing-stored-procedures-in-sql-server"></a>Assinando procedimentos armazenados no SQL Server
 Uma assinatura digital é um resumo dos dados criptografados com a chave privada do assinante. A chave privada garante que a assinatura digital seja exclusiva de seu portador ou proprietário. Você pode assinar assemblies, gatilhos, procedimentos armazenados e funções (exceto funções com valor de tabela embutida).  
  
 Você pode assinar um procedimento armazenado com um certificado ou uma chave assimétrica. Isso é criado para cenários quando as permissões não podem ser herdadas pelo encadeamento de propriedade ou quando a cadeia de propriedade é quebrada, como SQL dinâmico. Em seguida, você pode criar um usuário mapeado para o certificado, conceder permissões de usuário nos objetos de que procedimento armazenado precisa acessar de certificado.  

 Você também pode criar um logon mapeado para o mesmo certificado e, em seguida, conceder quaisquer permissões de nível de servidor necessárias para que o logon ou adicionar o logon a uma ou mais funções de servidor fixas. Isso é projetado para evitar habilitar o `TRUSTWORTHY` configuração para cenários em que são necessárias permissões de nível superior do banco de dados.  
  
 Quando o procedimento armazenado é executado, o SQL Server combina as permissões de usuário do certificado e/ou logon com aquelas do chamador. Ao contrário de `EXECUTE AS` cláusula, ela não altera o contexto de execução do procedimento. As funções internas que retornam o logon e os nomes de usuário retornam o nome do chamador, não o nome do usuário do certificado.  
  
## <a name="creating-certificates"></a>Criando certificados  
 Quando você se inscreve um procedimento armazenado com um certificado ou chave assimétrica, um resumo de dados que consiste o hash criptografado do código de procedimento armazenado, junto com o executar-como usuário, é criado usando a chave privada. Em tempo de execução, o resumo dos dados é criptografado com a chave pública e comparado com o valor de hash do procedimento armazenado. Alterando o executar-como usuário invalida o valor de hash para que a assinatura digital não corresponde. Modificar o procedimento armazenado remove a assinatura totalmente, que impede que alguém que não tem acesso à chave privada de alterar o código do procedimento armazenado. Em ambos os casos, você deve assinar novamente o procedimento sempre que você alterar o código ou o executar-como usuário.  
  
 Há duas etapas necessárias envolvidas em um módulo de assinatura:  
  
1.  Criar um certificado usando a instrução Transact-SQL `CREATE CERTIFICATE [certificateName]`. Essa instrução tem várias opções para definir uma data inicial e final e uma senha. A data de expiração padrão é um ano.  
  
1.  Assinar o procedimento armazenado com o certificado usando a instrução Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]`.  

Depois que o módulo tenha sido assinado, uma ou mais entidades precisa ser criado para manter as permissões adicionais que devem ser associadas ao certificado.  

Se o módulo precisa ter permissões de nível de banco de dados adicionais:  
  
1.  Crie um usuário de banco de dados associado ao certificado usando a instrução Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]`. Esse usuário existe no banco de dados somente e não está associado um logon, a menos que também foi criado um logon do mesmo certificado.  
  
1.  Conceda ao usuário do certificado as permissões necessárias de nível de banco de dados.  
  
Se o módulo precisa ter permissões de nível de servidor adicionais:  
  
1.  Copie o certificado para o `master` banco de dados.  
 
1.  Crie um logon associado ao certificado usando o Transact-SQL `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` instrução.  
  
1.  Concede ao logon de certificado as permissões necessárias de nível de servidor.  
  
> [!NOTE]  
>  Um certificado não pode conceder permissões a um usuário que tem permissões revogadas usando a instrução DENY. DENY sempre terá precedência sobre GRANT, impedindo que o chamador herde as permissões concedidas ao usuário do certificado.  
  
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
