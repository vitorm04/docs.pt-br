---
title: Cenários de segurança do aplicativo no SQL Server
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: 1239715678bda648bc962f9b23667b954b540e3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="application-security-scenarios-in-sql-server"></a>Cenários de segurança do aplicativo no SQL Server
Não é possível corrigir único para criar um aplicativo de cliente do SQL Server seguro. Cada aplicativo é exclusivo em seus requisitos, o ambiente de implantação e a população de usuários. Um aplicativo que seja razoavelmente seguro quando ele é implantado inicialmente pode se tornar menos segura ao longo do tempo. É impossível prever com precisão de qualquer quais ameaças podem surgir no futuro.  
  
 SQL Server, como um produto, evoluiu várias versões para incorporar os recursos de segurança mais recentes que permitem aos desenvolvedores criar aplicativos de banco de dados seguro. No entanto, a segurança não chegar na caixa. ele requer o monitoramento e atualização contínuas.  
  
## <a name="common-threats"></a>Ameaças comuns  
 Os desenvolvedores precisam entender a ameaças de segurança, as ferramentas fornecidas para elas e como evitar falhas de segurança causado do contador. Segurança pode melhor ser pensada como uma cadeia, onde uma quebra de qualquer um link compromete a intensidade do todo. A lista a seguir inclui algumas ameaças de segurança comuns que são abordadas mais detalhadamente nos tópicos nesta seção.  
  
### <a name="sql-injection"></a>Injeção SQL  
 A Injeção de SQL é o processo pelo qual um usuário mal-intencionado insere instruções Transact-SQL em vez de entrada válida. Se a entrada é passada diretamente para o servidor sem validação e se o aplicativo inadvertidamente executa o código injetado, o ataque tem o potencial para danificar ou destruir dados. Você pode impedir o SQL Server injeção de ataques por meio de procedimentos armazenados e comandos parametrizados, evitando o SQL dinâmico e restringindo as permissões de todos os usuários.  
  
### <a name="elevation-of-privilege"></a>Elevação de privilégio  
 Elevação de ataques de privilégio ocorrem quando um usuário é capaz de assumir os privilégios de uma conta confiável, como um proprietário ou administrador. Sempre executadas em contas de usuário de privilégios mínimos e atribuir apenas as permissões necessárias. Evite usar administrativo ou proprietário contas para executar o código. Isso limita a quantidade de danos que podem ocorrer se um ataque tiver êxito. Ao executar tarefas que requerem permissões adicionais, use o procedimento de assinatura ou representação apenas para a duração da tarefa. Você pode assinar procedimentos armazenados com certificados ou usar a representação para temporariamente atribuir permissões.  
  
### <a name="probing-and-intelligent-observation"></a>Observação de investigação e inteligente  
 Um ataque de investigação pode usar mensagens de erro geradas por um aplicativo para procurar vulnerabilidades de segurança. Implementar o tratamento de erros em todo o código de procedimento para impedir que as informações de erro do SQL Server seja retornada para o usuário final.  
  
### <a name="authentication"></a>Autenticação  
 Um ataque de injeção de cadeia de caracteres de conexão pode ocorrer ao usar logons do SQL Server, se uma cadeia de caracteres de conexão com base na entrada do usuário é construída em tempo de execução. Se a cadeia de caracteres de conexão não está marcada para pares de palavra-chave válida, um invasor pode inserir caracteres extras, potencialmente acessar dados confidenciais ou outros recursos no servidor. Use autenticação do Windows sempre que possível. Se você deve usar logons do SQL Server, use o <xref:System.Data.SqlClient.SqlConnectionStringBuilder> para criar e validar cadeias de caracteres de conexão em tempo de execução.  
  
### <a name="passwords"></a>Senhas  
 Muitos ataques bem-sucedida porque um invasor foi capaz de obter ou adivinhar uma senha para um usuário com privilégios. As senhas são a primeira linha de defesa contra intrusos; portanto definir senhas fortes é essencial para a segurança do seu sistema. Criar e aplicar políticas de senha para autenticação de modo misto.  
  
 Sempre atribua uma senha forte para a `sa` de conta, mesmo quando a autenticação do Windows.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Gerenciando permissões com procedimentos armazenados no SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 Descreve como usar procedimentos armazenados para gerenciar permissões e controlar o acesso a dados. Usando procedimentos armazenados é uma maneira eficiente para responder a muitas ameaças de segurança.  
  
 [Escrevendo SQL dinâmico seguro no SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 Descreve técnicas para gravação seguro SQL dinâmico, usando procedimentos armazenados.  
  
 [Assinando procedimentos armazenados no SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 Descreve como assinar um procedimento armazenado com um certificado para permitir aos usuários trabalhar com dados que não têm acesso direto ao. Isso permite que procedimentos armazenados executar operações que o chamador não tem permissões para executar diretamente.  
  
 [Personalizando permissões com representação no SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 Descreve como usar EXECUTE AS cláusula para representar outro usuário. Representação alterna o contexto de execução do chamador para o usuário especificado.  
  
 [Concedendo permissões de nível de linha no SQL Server](../../../../../docs/framework/data/adonet/sql/granting-row-level-permissions-in-sql-server.md)  
 Descreve como implementar permissões em nível de linha para restringir o acesso a dados.  
  
 [Criando funções de aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md)  
 Descreve os recursos e funcionalidade de funções de aplicativo.  
  
 [Habilitando o acesso ao banco de dados no SQL Server](../../../../../docs/framework/data/adonet/sql/enabling-cross-database-access-in-sql-server.md)  
 Descreve como habilitar o acesso de banco de dados sem comprometer a segurança.  
  
## <a name="see-also"></a>Consulte também  
 [SQL Server Security](../../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)  
 [Visão geral de segurança do SQL Server](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
