---
title: Gerenciando permissões com procedimentos armazenados no SQL Server
ms.date: 03/30/2017
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
ms.openlocfilehash: 0688157b45892cacb73f858dffb93836da9fc91d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229986"
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a>Gerenciando permissões com procedimentos armazenados no SQL Server
Um método de criar várias linhas de defesa em torno do banco de dados é implementar todo o acesso a dados usando procedimentos armazenados ou funções definidas pelo usuário. Você revogar ou nega todas as permissões para objetos subjacentes, como tabelas, e concede permissões EXECUTE em procedimentos armazenados. Isso cria efetivamente um perímetro de segurança em torno dos dados e objetos de banco de dados.  
  
## <a name="stored-procedure-benefits"></a>Benefícios do procedimento armazenado  
 Os procedimentos armazenados têm os seguintes benefícios:  
  
-   A lógica de dados e as regras de negócio podem ser encapsuladas de forma que os usuários possam acessar dados e objetos somente de maneiras que os desenvolvedores e administradores de banco de dados pretenderem.  
  
-   Os procedimentos armazenados com parâmetros que validam toda a entrada do usuário podem ser usados para frustrar ataques de injeção SQL. Se você usar o SQL dinâmico, parametrize os comandos e nunca inclua valores de parâmetros diretamente na cadeia de caracteres de uma consulta.  
  
-   Consultas ad hoc e as modificações de dados podem ser recusadas. Isso impede que os usuários destruam dados de maneira maliciosa ou inadvertida ou executem consultas que comprometam o desempenho do servidor ou da rede.  
  
-   Os erros podem ser tratados no código do procedimento sem ser passado diretamente para aplicativos cliente. Isso impede que as mensagens de erro sejam retornadas, o que pode ajudar em um ataque de sondagem. Registre erros e trate-os no servidor.  
  
-   Os procedimentos armazenados podem ser escritos uma vez e acessados por muitos aplicativos.  
  
-   Os aplicativos cliente não precisam saber nada sobre as estruturas de dados subjacentes. O código do procedimento armazenado pode ser alterado sem exigir alterações em aplicativos cliente contanto que as alterações não afetem listas de parâmetros ou tipos de dados retornados.  
  
-   Os procedimentos armazenados podem reduzir o tráfego de rede combinando várias operações em uma chamada de procedimento.  
  
## <a name="stored-procedure-execution"></a>Execução de procedimento armazenado  
 Os procedimentos armazenados aproveitam o encadeamento de propriedade para fornecer acesso aos dados de forma que os usuários não precisem ter a permissão explícita para acessar objetos de banco de dados. Uma cadeia de propriedade existe quando os objetos que se acessam entre si tiverem o mesmo proprietário sequencialmente. Por exemplo, um procedimento armazenado pode chamar outros procedimentos armazenados, ou um procedimento armazenado pode acessar várias tabelas. Se todos os objetos na cadeia de execução tiverem o mesmo proprietário, o SQL Server somente verificará a permissão EXECUTE para o chamador, não as permissões do chamador em outros objetos. Portanto, você precisa conceder somente permissões EXECUTE em procedimentos armazenados; você pode revogar ou nega todas as permissões nas tabelas subjacentes.  
  
## <a name="best-practices"></a>Práticas recomendadas  
 Somente gravar procedimentos armazenados não é suficiente para proteger adequadamente seu aplicativo. Você também deverá considerar os seguintes buracos na segurança.  
  
-   Conceda permissões EXECUTE em procedimentos armazenados para funções de banco de dados que você deseja que possam acessar os dados.  
  
-   Revogue ou negue todas as permissões para as tabelas subjacentes para todas as funções e usuários no banco de dados, inclusive a função `public`. Todos os usuários herdam permissões públicas. Portanto, negar permissões a `public` significa que somente os proprietários e os membros de `sysadmin` têm acesso; todos os outros usuários não poderão herdar permissões de associação em outras funções.  
  
-   Não adicione usuários ou funções às funções `sysadmin` ou `db_owner`. Os administradores do sistema e os proprietários de banco de dados podem acessar todos os objetos de banco de dados.  
  
-   Desabilite a conta `guest`. Isso impedirá que os usuários anônimos conectem-se ao banco de dados. A conta guest é desabilitada por padrão em novos bancos de dados.  
  
-   Implemente tratamento de erros e registre os erros em log.  
  
-   Crie os procedimentos armazenados com parâmetros que validam toda a entrada do usuário. Considere toda a entrada do usuário como não confiável.  
  
-   Evite SQL dinâmico a menos que seja absolutamente necessário. Use a função Transact-SQL QUOTENAME() para limitar um valor de cadeia de caracteres e ignorar qualquer ocorrência de delimitadores na cadeia de caracteres de entrada.  
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Procedimentos armazenados](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) e [Injeção de SQL](https://go.microsoft.com/fwlink/?LinkId=98234) nos Manuais Online do SQL Server|Os tópicos descrevem como criar procedimentos armazenados e como a injeção de SQL funciona.|  
  
## <a name="see-also"></a>Consulte também

- [Protegendo aplicativos ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Visão geral de segurança do SQL Server](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Escrevendo SQL dinâmico seguro no SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [Assinando procedimentos armazenados no SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)
- [Personalizando permissões com representação no SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)
- [Modificando dados com procedimentos armazenados](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
