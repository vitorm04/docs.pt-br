---
title: Cenários de segurança do aplicativo no SQL Server
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: bf844f35a3504af52cdb6bf745862ad5098dfc5f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782697"
---
# <a name="application-security-scenarios-in-sql-server"></a>Cenários de segurança do aplicativo no SQL Server
Não há uma maneira correta de criar um aplicativo cliente seguro SQL Server. Cada aplicativo é exclusivo em seus requisitos, ambiente de implantação e população do usuário. Um aplicativo razoavelmente seguro quando é implantado inicialmente pode se tornar menos seguro ao longo do tempo. É impossível prever qualquer precisão que as ameaças possam surgir no futuro.  
  
 SQL Server, como um produto, evoluiu várias versões para incorporar os recursos de segurança mais recentes que permitem aos desenvolvedores criar aplicativos de banco de dados seguros. No entanto, a segurança não vem na caixa; Ele requer monitoramento e atualização contínuos.  
  
## <a name="common-threats"></a>Ameaças comuns  
 Os desenvolvedores precisam entender as ameaças de segurança, as ferramentas fornecidas para combater e como evitar falhas de segurança. A segurança pode ser considerada como uma cadeia, em que uma quebra em qualquer link compromete a força do todo. A lista a seguir inclui algumas ameaças comuns de segurança que são discutidas mais detalhadamente nos tópicos desta seção.  
  
### <a name="sql-injection"></a>Injeção de SQL  
 A Injeção de SQL é o processo pelo qual um usuário mal-intencionado insere instruções Transact-SQL em vez de entrada válida. Se a entrada for passada diretamente para o servidor sem ser validada e se o aplicativo executar inadvertidamente o código injetado, o ataque terá o potencial de danificar ou destruir dados. Você pode impedir ataques de injeção de SQL Server usando procedimentos armazenados e comandos com parâmetros, evitando o SQL dinâmico e restringindo permissões em todos os usuários.  
  
### <a name="elevation-of-privilege"></a>Elevação de privilégio  
 Os ataques de elevação de privilégio ocorrem quando um usuário é capaz de assumir os privilégios de uma conta confiável, como um proprietário ou administrador. Sempre execute sob contas de usuário com privilégios mínimos e atribua apenas as permissões necessárias. Evite usar contas administrativas ou proprietárias para executar o código. Isso limita a quantidade de danos que podem ocorrer se um ataque for realizado com sucesso. Ao executar tarefas que exigem permissões adicionais, use a assinatura ou representação de procedimento somente pela duração da tarefa. Você pode assinar procedimentos armazenados com certificados ou usar a representação para atribuir permissões temporariamente.  
  
### <a name="probing-and-intelligent-observation"></a>Investigação e observação inteligente  
 Um ataque de investigação pode usar mensagens de erro geradas por um aplicativo para procurar vulnerabilidades de segurança. Implemente o tratamento de erros em todo o código de procedimento para impedir que SQL Server informações de erro sejam retornadas ao usuário final.  
  
### <a name="authentication"></a>Autenticação  
 Um ataque de injeção de cadeia de conexão pode ocorrer ao usar SQL Server logons se uma cadeia de conexão baseada na entrada do usuário for construída em tempo de execução. Se a cadeia de conexão não for verificada em busca de pares de palavras-chave válidos, um invasor poderá inserir caracteres extras, potencialmente acessar dados confidenciais ou outros recursos no servidor. Use a autenticação do Windows sempre que possível. Se você precisar usar SQL Server logons, use o <xref:System.Data.SqlClient.SqlConnectionStringBuilder> para criar e validar cadeias de conexão em tempo de execução.  
  
### <a name="passwords"></a>Suas  
 Muitos ataques são bem-sucedidos porque um invasor conseguiu obter ou adivinhar uma senha para um usuário privilegiado. As senhas são sua primeira linha de defesa contra intrusos, portanto, definir senhas fortes é essencial para a segurança do seu sistema. Criar e impor políticas de senha para autenticação de modo misto.  
  
 Sempre atribua uma senha forte à `sa` conta, mesmo ao usar a autenticação do Windows.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Gerenciando permissões com procedimentos armazenados no SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)  
 Descreve como usar procedimentos armazenados para gerenciar permissões e controlar o acesso a dados. O uso de procedimentos armazenados é uma maneira eficaz de responder a muitas ameaças de segurança.  
  
 [Escrevendo SQL dinâmico seguro no SQL Server](writing-secure-dynamic-sql-in-sql-server.md)  
 Descreve técnicas para escrever SQL dinâmico seguro usando procedimentos armazenados.  
  
 [Assinando procedimentos armazenados no SQL Server](signing-stored-procedures-in-sql-server.md)  
 Descreve como assinar um procedimento armazenado com um certificado para permitir que os usuários trabalhem com dados aos quais eles não têm acesso direto. Isso permite que os procedimentos armazenados executem operações que o chamador não tem permissões para executar diretamente.  
  
 [Personalizando permissões com representação no SQL Server](customizing-permissions-with-impersonation-in-sql-server.md)  
 Descreve como usar a cláusula EXECUTE AS para representar outro usuário. A representação alterna o contexto de execução do chamador para o usuário especificado.  
  
 [Concedendo permissões de nível de linha no SQL Server](granting-row-level-permissions-in-sql-server.md)  
 Descreve como implementar permissões em nível de linha para restringir o acesso a dados.  
  
 [Criando funções de aplicativo no SQL Server](creating-application-roles-in-sql-server.md)  
 Descreve os recursos e a funcionalidade das funções de aplicativo.  
  
 [Habilitando o acesso ao banco de dados no SQL Server](enabling-cross-database-access-in-sql-server.md)  
 Descreve como habilitar o acesso entre bancos de dados sem comprometer a segurança.  
  
## <a name="see-also"></a>Consulte também

- [SQL Server Security](sql-server-security.md) (Segurança do SQL Server)
- [Visão geral de segurança do SQL Server](overview-of-sql-server-security.md)
- [Securing ADO.NET Applications](../securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
