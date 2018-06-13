---
title: Personalizando permissões com representação no SQL Server
ms.date: 03/30/2017
ms.assetid: dc733d09-1d6d-4af0-9c4b-8d24504860f1
ms.openlocfilehash: ac2c6805a9ab49d95f68e56306d7d9fb8aab2a2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362637"
---
# <a name="customizing-permissions-with-impersonation-in-sql-server"></a>Personalizando permissões com representação no SQL Server
Muitos aplicativos usam procedimentos armazenados para acessar os dados, dependendo do encadeamento de propriedade para restringir o acesso a tabelas base. Você pode conceder permissões EXECUTE em procedimentos armazenados, revogando ou negando permissões nas tabelas base. O SQL Server não verifica as permissões do chamador se o procedimento armazenado e as tabelas têm o mesmo proprietário. No entanto, o encadeamento de propriedades não funcionará se os objetos tiverem proprietários diferentes ou no caso de SQL dinâmico.  
  
 Você pode usar a cláusula EXECUTE AS em um procedimento armazenado quando o chamador não tiver permissões nos objetos de banco de dados referenciados. O efeito da cláusula EXECUTE AS é que o contexto de execução é alternado para o usuário do proxy. Qualquer código, assim como as chamadas para os procedimentos armazenados ou gatilhos aninhados, é executado sob o contexto de segurança do usuário do proxy. O contexto de execução é revertido para o chamador original somente após a execução do procedimento ou quando uma instrução REVERT for emitida.  
  
## <a name="context-switching-with-the-execute-as-statement"></a>Alternância de contexto com a instrução EXECUTE AS  
 A instrução EXECUTE AS do Transact-SQL permite a troca do contexto de execução de uma instrução representando outro logon ou usuário do banco de dados. Essa é uma técnica útil para testar consultas e procedimentos como outro usuário.  
  
```  
EXECUTE AS LOGIN = 'loginName';  
EXECUTE AS USER = 'userName';  
```  
  
 Você deve ter permissões IMPERSONATE no logon ou usuário que você está representando. Essa permissão é implícita para `sysadmin` para todos os bancos de dados e os membros de função `db_owner` nos bancos de dados que eles possuem.  
  
## <a name="granting-permissions-with-the-execute-as-clause"></a>Concedendo permissões com a cláusula EXECUTE AS  
 Você pode usar a cláusula EXECUTE AS no cabeçalho da definição de um procedimento armazenado, gatilho, ou uma função definida pelo usuário (com exceção das funções com valor de tabela embutida). Isso faz o procedimento ser executado no contexto do nome de usuário ou palavra-chave especificada na cláusula EXECUTE AS. Você pode criar um usuário de proxy no banco de dados que não seja mapeado para um logon, permitindo apenas as permissões necessárias sobre os objetos acessados pelo procedimento. Apenas o usuário do proxy especificado na cláusula EXECUTE AS deve ter permissões em todos os objetos acessados pelo módulo.  
  
> [!NOTE]
>  Algumas ações, como TRUNCATE TABLE, não têm permissões concessíveis. Incorporando a instrução dentro de um procedimento e especificando um usuário de proxy que tenha permissões ALTER TABLE, você pode estender as permissões para truncar a tabela para chamadores que têm somente as permissões EXECUTE no procedimento.  
  
 O contexto especificado na cláusula EXECUTE AS é válido para a duração do procedimento, inclusive procedimentos aninhados e gatilhos. O contexto será revertido para o chamador quando a execução estiver concluída ou a instrução REVERT for emitida.  
  
 Há três etapas envolvidas no uso da cláusula EXECUTE AS em um procedimento.  
  
1.  Crie um usuário de proxy no banco de dados que não seja mapeado para um logon. Isso não é obrigatório, mas ajuda a gerenciar permissões.  
  
```  
CREATE USER proxyUser WITHOUT LOGIN  
```  
  
1.  Conceda ao usuário de proxy as permissões necessárias.  
  
2.  Adicione a cláusula EXECUTE AS no procedimento armazenado ou função definida pelo usuário.  
  
```  
CREATE PROCEDURE [procName] WITH EXECUTE AS 'proxyUser' AS ...  
```  
  
> [!NOTE]
>  Os aplicativos que exigem a auditoria podem ser interrompidos porque o contexto de segurança original do chamador não é retido. As funções internas que retornam a identidade do usuário atual, como SESSION_USER, USER ou USER_NAME retornarão o usuário associado com a cláusula EXECUTE AS, não o chamador original.  
  
### <a name="using-execute-as-with-revert"></a>Usando EXECUTE AS com REVERT  
 Você pode usar a instrução REVERT do Transact-SQL para reverter para o contexto da execução original.  
  
 A cláusula opcional WITH NO REVERT COOKIE = @variableName, permite que você alternar o contexto de execução de volta para o chamador se o @variableName variável contém o valor correto. Isso permite a troca do contexto de execução de volta para o chamador em ambientes em que o pool de conexões é usado. Porque o valor de @variableName é conhecido apenas pelo chamador de EXECUTE AS instrução, o chamador pode garantir que o contexto de execução não pode ser alterado pelo usuário final que invoca o aplicativo. Quando a conexão é fechada, ela será retornada para o pool. Para obter mais informações sobre conexão pool no ADO.NET, consulte [Pooling de Conexão do SQL Server (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="specifying-the-execution-context"></a>Especificando o contexto de execução  
 Além de especificar um usuário, você também poderá usar EXECUTE AS com qualquer uma das palavras-chave a seguir.  
  
-   CALLER. Executar como CALLER é o padrão; se nenhuma outra opção for especificada, o procedimento será executado no contexto de segurança do chamador.  
  
-   OWNER. Executar como OWNER executa o procedimento no contexto do proprietário do procedimento. Se o procedimento for criado em um esquema de propriedade do `dbo` ou pelo proprietário do banco de dados, o procedimento será executado com permissões ilimitadas.  
  
-   SELF. Executar como SELF executa no contexto de segurança do criador do procedimento armazenado. Isso é equivalente a executar como usuário especificado, onde o usuário especificado é a pessoa que cria ou altera o procedimento.  
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Alternância de contexto](http://msdn.microsoft.com/library/ms188268.aspx) nos Manuais Online do SQL Server|Contém links para os tópicos que descrevem como usar a cláusula EXECUTE AS.|  
|[Usando EXECUTE AS para criar conjuntos de permissões personalizadas](http://msdn.microsoft.com/library/ms190384.aspx) e [usando EXECUTE AS em módulos](http://msdn.microsoft.com/library/ms178106.aspx) nos Manuais Online do SQL Server|Os tópicos descrevem como usar a cláusula EXECUTE AS.|  
  
## <a name="see-also"></a>Consulte também  
 [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [Visão geral de segurança do SQL Server](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Gerenciando permissões com procedimentos armazenados no SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Escrevendo SQL dinâmico seguro no SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Assinando procedimentos armazenados no SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [Modificando dados com procedimentos armazenados](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
