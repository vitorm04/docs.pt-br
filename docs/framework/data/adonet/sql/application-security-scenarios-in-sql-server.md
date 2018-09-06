---
title: Cenários de segurança de aplicativo no SQL Server
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: bf4f4adfd5f49bd210026e40bd5fa4e67da10d75
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777802"
---
# <a name="application-security-scenarios-in-sql-server"></a>Cenários de segurança de aplicativo no SQL Server
Não há nenhuma maneira correta de única para criar um aplicativo de cliente seguro do SQL Server. Cada aplicativo é exclusivo em seus requisitos, o ambiente de implantação e a população de usuários. Um aplicativo que é razoavelmente seguro quando ele é implantado inicialmente pode se tornar menos seguro ao longo do tempo. É impossível prever com algum nível de precisão, o que ameaças podem surgir no futuro.  
  
 SQL Server, como um produto, evoluiu ao longo de várias versões para incorporar recursos de segurança mais recentes que permitem aos desenvolvedores criar aplicativos de banco de dados seguro. No entanto, a segurança não vem na caixa. ele requer o monitoramento contínuo e a atualização.  
  
## <a name="common-threats"></a>Ameaças comuns  
 Os desenvolvedores precisam compreender as ameaças de segurança, as ferramentas fornecidas para elas e como evitar falhas de segurança autoinfligidos do contador. Segurança pode melhor ser pensada como uma cadeia, onde uma quebra de qualquer um link compromete a força do todo. A lista a seguir inclui algumas ameaças comuns à segurança que são abordados mais detalhadamente nos tópicos nesta seção.  
  
### <a name="sql-injection"></a>Injeção de SQL  
 A Injeção de SQL é o processo pelo qual um usuário mal-intencionado insere instruções Transact-SQL em vez de entrada válida. Se a entrada é passada diretamente para o servidor sem que está sendo validado e o aplicativo executa inadvertidamente o código injetado, o ataque tem o potencial de danificar ou destruir dados. Você pode impedir o SQL Server injeção de ataques, usando procedimentos armazenados e comandos parametrizados, evitando o SQL dinâmico e restringindo as permissões de todos os usuários.  
  
### <a name="elevation-of-privilege"></a>Elevação de privilégio  
 Elevação de privilégio ataques ocorrem quando um usuário é capaz de assumir os privilégios de uma conta confiável, como um proprietário ou administrador. Sempre são executados em contas de usuário com privilégios mínimos e atribuir apenas as permissões necessárias. Evite usando administrativo ou proprietário de contas para executar o código. Isso limita a quantidade de danos que podem ocorrer se um ataque for bem-sucedida. Ao executar tarefas que requerem permissões adicionais, use o procedimento de assinatura ou a representação apenas para a duração da tarefa. Você pode assinar procedimentos armazenados com certificados ou usar a representação para temporariamente atribuir permissões.  
  
### <a name="probing-and-intelligent-observation"></a>Observação de investigação e inteligente  
 Um ataque de sondagem pode usar mensagens de erro geradas por um aplicativo para procurar por vulnerabilidades de segurança. Implementar o tratamento de erros em todo o código procedural para impedir que as informações de erro do SQL Server seja retornada para o usuário final.  
  
### <a name="authentication"></a>Autenticação  
 Um ataque de injeção de cadeia de caracteres de conexão pode ocorrer ao usar logons do SQL Server, se uma cadeia de caracteres de conexão com base na entrada do usuário é construído em tempo de execução. Se a cadeia de caracteres de conexão não está marcada para pares de palavra-chave válida, um invasor pode inserir caracteres extras, potencialmente, acessar dados confidenciais ou outros recursos no servidor. Use a autenticação do Windows sempre que possível. Se você deve usar logons do SQL Server, use o <xref:System.Data.SqlClient.SqlConnectionStringBuilder> para criar e validar cadeias de caracteres de conexão em tempo de execução.  
  
### <a name="passwords"></a>Senhas  
 Muitos ataques bem-sucedida porque um invasor foi capaz de obter ou adivinhar uma senha para um usuário com privilégios. As senhas são a primeira linha de defesa contra intrusos, portanto, definir senhas fortes é essencial para a segurança do seu sistema. Criar e impor políticas de senha para autenticação de modo misto.  
  
 Sempre atribua uma senha forte para o `sa` de conta, mesmo ao usar a autenticação do Windows.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Gerenciando permissões com procedimentos armazenados no SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 Descreve como usar procedimentos armazenados para gerenciar permissões e controlar o acesso a dados. Usando procedimentos armazenados é uma maneira eficiente para responder a muitas ameaças de segurança.  
  
 [Escrevendo SQL dinâmico seguro no SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 Descreve técnicas para escrever um SQL dinâmico seguro que usando procedimentos armazenados.  
  
 [Assinando procedimentos armazenados no SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 Descreve como assinar um procedimento armazenado com um certificado para permitir que os usuários trabalhar com dados não tiverem acesso direto ao. Isso permite que procedimentos armazenados para executar operações que o chamador não tem permissões para executar diretamente.  
  
 [Personalizando permissões com representação no SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 Descreve como usar EXECUTE AS cláusula para representar outro usuário. Representação alterna o contexto de execução do chamador para o usuário especificado.  
  
 [Concedendo permissões de nível de linha no SQL Server](../../../../../docs/framework/data/adonet/sql/granting-row-level-permissions-in-sql-server.md)  
 Descreve como implementar as permissões de nível de linha para restringir o acesso a dados.  
  
 [Criando funções de aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md)  
 Descreve os recursos e funcionalidade de funções de aplicativo.  
  
 [Habilitando o acesso ao banco de dados no SQL Server](../../../../../docs/framework/data/adonet/sql/enabling-cross-database-access-in-sql-server.md)  
 Descreve como habilitar o acesso entre bancos de dados sem comprometer a segurança.  
  
## <a name="see-also"></a>Consulte também  
 [SQL Server Security](../../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)  
 [Visão geral de segurança do SQL Server](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
