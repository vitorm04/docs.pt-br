---
title: Escrevendo SQL dinâmico seguro no SQL Server
ms.date: 03/30/2017
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.openlocfilehash: 9b0c903c04c82c9a0f61197642645c5ba93ba099
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645904"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>Escrevendo SQL dinâmico seguro no SQL Server
A Injeção de SQL é o processo pelo qual um usuário mal-intencionado insere instruções Transact-SQL em vez de entrada válida. Se a entrada for passada diretamente para o servidor sem ser validada e se o aplicativo executa inadvertidamente o código injetado, o ataque terá o potencial de danificar ou destruir dados.  
  
 Qualquer procedimento que construa instruções SQL deve ser analisado em busca de vulnerabilidades de injeção porque o SQL Server executará todas as consultas sintaticamente válidas que receber. Até mesmo os dados com parâmetros podem ser manipulados por um invasor qualificado e determinado. Se você usar o SQL dinâmico, parametrize os comandos e nunca inclua valores de parâmetros diretamente na cadeia de caracteres da consulta.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>Anatomia de um ataque de injeção de SQL  
 O processo de injeção funciona encerrando prematuramente uma cadeia de caracteres de texto e anexando um novo comando. Como o comando inserido pode ter cadeias de caracteres adicionais anexadas a ele antes de ser executado, o malfeitor encerra a cadeia de caracteres injetada com uma marca de comentário "--". O texto subsequente é ignorado em tempo de execução. Vários comandos podem ser inseridos usando um delimitador de ponto e vírgula (;).  
  
 Contanto que o código SQL injetado esteja sintaticamente correto, a violação não poderá ser detectada programaticamente. Portanto, você deve validar todas as entradas de usuário e cuidadosamente revisar o código que executa comandos SQL construídos no servidor que você está usando. Nunca concatene entrada de usuário que não seja validada. A concatenação de cadeia de caracteres é o ponto de entrada primária para injeção de script.  
  
 Aqui estão algumas diretrizes úteis:  
  
- Nunca construa instruções Transact-SQL diretamente da entrada do usuário; use procedimentos armazenados para validar a entrada de usuário.  
  
- Valide a entrada de usuário testando tipo, comprimento, formato e intervalo. Use a função Transact-SQL QUOTENAME() para ignorar nomes do sistema ou a função REPLACE() para ignorar qualquer caractere em uma cadeia de caracteres.  
  
- Implemente várias camadas de validação em cada camada do aplicativo.  
  
- Teste o tamanho e o tipo de dados de entrada e imponha limites apropriados. Isso pode ajudar a impedir o excesso deliberado de buffer.  
  
- Teste o conteúdo de variáveis de cadeia de caracteres e aceite somente valores previstos. Rejeite entradas que contenham dados binários, sequências de escape e caracteres de comentário.  
  
- Quando você estiver trabalhando com documentos XML, valide todos os dados em seu esquema como foram inseridos.  
  
- Em ambientes de várias camadas, todos os dados devem ser validados antes de entrarem na zona de confiança.  
  
- Não aceite as seguintes cadeias de caracteres nos campos do que os nomes de arquivo podem ser criados: AUX, CLOCK$, COM1 a COM8, CON, CONFIG$, LPT1 a LPT8, NUL e PRN.  
  
- Use objetos <xref:System.Data.SqlClient.SqlParameter> com procedimentos armazenados e comandos para fornecer a verificação de tipo e validação de comprimento.  
  
- Use expressões <xref:System.Text.RegularExpressions.Regex> em código de cliente para filtrar caracteres inválidos.  
  
## <a name="dynamic-sql-strategies"></a>Estratégias dinâmicas do SQL  
 Executar instruções SQL dinamicamente criadas em seu código procedural quebra a cadeia de propriedade, fazendo o SQL Server verificar as permissões do chamador nos objetos acessados pelo SQL dinâmico.  
  
 O SQL Server tem métodos para conceder aos usuários acesso aos dados usando procedimentos armazenados e funções definidas pelo usuário que executa o SQL dinâmico.  
  
- Usar a representação com a cláusula Transact-SQL EXECUTE AS, conforme descrito em [Personalizando permissões com representação no SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
- Assinar procedimentos armazenados com certificados, conforme descrito em [Assinando procedimentos armazenados no SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
### <a name="execute-as"></a>EXECUTE AS  
 A cláusula EXECUTE AS substitui as permissões do chamador com relação pelas do usuário especificado na cláusula EXECUTE AS. Os procedimentos armazenados aninhados ou gatilhos são executados sob o contexto de segurança do usuário do proxy. Isso pode interromper aplicativos que dependem de segurança em nível de linha ou exigem auditoria. Algumas funções que retornam a identidade do usuário retornam o usuário especificado na cláusula EXECUTE AS, não o chamador original. O contexto de execução é revertido para o chamador original somente após a execução do procedimento ou quando uma instrução REVERT for emitida.  
  
### <a name="certificate-signing"></a>Assinatura de certificado  
 Quando um procedimento armazenado que foi assinado com um certificado é executado, as permissões concedidas para o usuário do certificado são mescladas com as do chamador. O contexto de execução permanece o mesmo; o usuário do certificado não representa o chamador. Assinar procedimentos armazenados exige várias etapas para implementar. Cada vez que o procedimento é modificado, ele deve ser assinado novamente.  
  
### <a name="cross-database-access"></a>Acesso entre bancos de dados  
 O encadeamento de propriedades entre bancos de dados não funciona nos casos em que as instruções SQL criadas dinamicamente são executadas. Resolva isso no SQL Server criando um procedimento armazenado que acessa os dados em outro banco de dados e assinando o procedimento armazenado com um certificado existente em ambos os bancos de dados. Isso concede acesso de usuários aos recursos de banco de dados usados pelo procedimento sem conceder-lhes o acesso ao banco de dados ou permissões.  
  
## <a name="external-resources"></a>Recursos externos  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Procedimentos armazenados](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) e [Injeção de SQL](/sql/relational-databases/security/sql-injection) nos Manuais Online do SQL Server|Os tópicos descrevem como criar procedimentos armazenados e como a injeção de SQL funciona.|  
  
## <a name="see-also"></a>Consulte também

- [Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [Visão geral de segurança do SQL Server](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Cenários de segurança do aplicativo no SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Gerenciando permissões com procedimentos armazenados no SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [Assinando procedimentos armazenados no SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)
- [Personalizando permissões com representação no SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
