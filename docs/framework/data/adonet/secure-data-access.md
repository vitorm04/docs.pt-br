---
title: Proteger o acesso a dados
ms.date: 03/30/2017
ms.assetid: 473ebd69-21a3-4627-b95e-4e04d035c56f
ms.openlocfilehash: e5bb96a091dcd64f12d086d864643d00c34d8f17
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49372454"
---
# <a name="secure-data-access"></a>Proteger o acesso a dados
Para escrever código seguro do ADO.NET, você precisa compreender os mecanismos de segurança disponíveis no armazenamento de dados subjacente ou banco de dados. Você também precisa considerar as implicações de segurança de outros recursos ou componentes que seu aplicativo pode conter.  
  
## <a name="authentication-authorization-and-permissions"></a>Autenticação, autorização e permissões  
 Ao se conectar ao Microsoft SQL Server, você pode usar a autenticação do Windows, também conhecido como segurança integrada, que usa a identidade do usuário Windows Active Directory atual em vez de passar uma ID de usuário e senha. Usando a autenticação do Windows é altamente recomendável porque as credenciais do usuário não são expostas na cadeia de conexão. Se você não pode usar a autenticação do Windows para se conectar ao SQL Server, considere a criação de cadeias de caracteres de conexão em tempo de execução usando o <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 As credenciais usadas para autenticação precisam ser manipulados variam de acordo com o tipo de aplicativo. Por exemplo, em um aplicativo de formulários do Windows, o usuário pode ser solicitado a fornecer informações de autenticação ou credenciais do Windows do usuário podem ser usadas. No entanto, um aplicativo Web frequentemente acessa dados usando as credenciais fornecidas pelo próprio aplicativo e não pelo usuário.  
  
 Depois de autenticar usuários, o escopo de suas ações depende das permissões que foram concedidas a eles. Sempre siga o princípio de privilégio mínimo e conceder somente permissões que são absolutamente necessárias.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)|Descreve as práticas recomendadas de segurança e técnicas para proteger as informações de conexão, como o uso de configuração protegida para criptografar cadeias de caracteres de conexão.|  
|[Recomendações para estratégias de acesso a dados](https://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)|Fornece recomendações para acessar dados e executar operações de banco de dados.|  
|[Construtores de cadeia de Conexão](../../../../docs/framework/data/adonet/connection-string-builders.md)|Descreve como criar cadeias de caracteres de conexão de entrada do usuário em tempo de execução.|  
|[Visão geral de segurança do SQL Server](../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)|Descreve a arquitetura de segurança do SQL Server.|  
  
## <a name="parameterized-commands-and-sql-injection"></a>Injeção de SQL e comandos parametrizados  
 Uso de comandos parametrizados ajuda na proteção contra ataques de injeção de SQL, em que um invasor "injeta" um comando em uma instrução SQL que compromete a segurança no servidor. Comandos parametrizados se proteger contra um ataque de injeção de SQL, garantindo que os valores recebidos de uma fonte externa são passados como valores somente e não faz parte da instrução Transact-SQL. Como resultado, os comandos Transact-SQL inseridos em um valor não são executados na fonte de dados. Em vez disso, eles serão avaliados somente como um valor de parâmetro. Além dos benefícios de segurança, os comandos parametrizados fornecem um método conveniente para organizar os valores passados com uma instrução Transact-SQL ou um procedimento armazenado.  
  
 Para obter mais informações sobre como usar os comandos com parâmetros, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Parâmetros DataAdapter](../../../../docs/framework/data/adonet/dataadapter-parameters.md)|Descreve como usar parâmetros com um `DataAdapter`.|  
|[Modificando dados com procedimentos armazenados](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)|Descreve como especificar parâmetros e obter um valor de retorno.|  
|[Gerenciando permissões com procedimentos armazenados no SQL Server](../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)|Descreve como usar procedimentos armazenados do SQL Server para encapsular acesso a dados.|  
  
## <a name="script-exploits"></a>Explorações de script  
 Um script malicioso é outra forma de injeção que usa caracteres mal-intencionados inseridos em uma página da Web. O navegador não valida os caracteres inseridos e processará-los como parte da página.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Visão geral de explorações de script](https://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|Descreve como se proteger contra scripts e a instrução SQL explorações.|  
  
## <a name="probing-attacks"></a>Investigando ataques  
 Os invasores geralmente usar informações de uma exceção, como o nome do servidor, banco de dados ou tabela, para montar um ataque no seu sistema. Como as exceções podem conter informações específicas sobre seu aplicativo ou a fonte de dados, você pode ajudar a manter sua fonte de dados e aplicativos melhor protegidos expondo somente informações essenciais para o cliente.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Fundamentos do tratamento de exceções](../../../../docs/standard/exceptions/exception-handling-fundamentals.md)|Descreve as formas básicas de manipulação de exceção estruturada try/catch/finally.|  
|[Práticas recomendadas para exceções](../../../../docs/standard/exceptions/best-practices-for-exceptions.md)|Descreve as práticas recomendadas para tratamento de exceções.|  
  
## <a name="protecting-microsoft-access-and-excel-data-sources"></a>Protegendo o Microsoft Access e fontes de dados do Excel  
 Microsoft Access e Microsoft Excel podem agir como um armazenamento de dados para um aplicativo ADO.NET, quando os requisitos de segurança mínima ou inexistente. Seus recursos de segurança entram para bloqueio de privilégios, mas não devem ser usados mais de desencorajar meddling por usuários uninformed. Os arquivos de dados físico para o Excel e Access existem no sistema de arquivos e devem ser acessíveis a todos os usuários. Isso os torna vulnerável a ataques que podem resultar em roubo ou perda de dados, pois os arquivos podem ser facilmente copiados ou alterados. Quando uma segurança robusta é necessária, use SQL Server ou outro banco de dados com base no servidor onde os arquivos de dados físicos não são legíveis do sistema de arquivos.  
  
 Para obter mais informações sobre como proteger os dados do Excel e Access, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Considerações de segurança e diretrizes para o Access 2007](https://go.microsoft.com/fwlink/?LinkId=98354)|Descreve técnicas de segurança para o Access 2007 tais criptografando arquivos, administrando as senhas, convertendo os bancos de dados para os novos formatos ACCDB e ACCDE e usando outras opções de segurança.|  
|[Ajudar a proteger um banco de dados do Access com segurança de nível de usuário (MDB)](https://go.microsoft.com/fwlink/?LinkId=47697)|Aplica-se para o Access 2003. Fornece instruções para a implementação de segurança em nível de usuário para proteger os dados no Access 2003.|  
|[Noções básicas sobre a função de arquivos de informações do grupo de trabalho na segurança de acesso](https://support.microsoft.com/kb/305542)|Explica a função e a relação do arquivo de informações do grupo de trabalho de segurança do Access 2003.|  
|[Com frequência frequentes perguntas sobre segurança do Microsoft Access para versões do Microsoft Access 2.0 até 2000](https://go.microsoft.com/fwlink/?LinkId=47698)|Versão para download perguntas frequentes sobre o Microsoft Access Security.|  
|[Solucionar problemas de segurança e proteção](https://go.microsoft.com/fwlink/?LinkId=47703)|Apresenta soluções para problemas comuns com segurança no Excel 2003.|  
  
## <a name="enterprise-services"></a>O Enterprise Services  
 COM+ contém seu próprio modelo de segurança que se baseia em contas do Windows NT e a representação de processo/thread. O <xref:System.EnterpriseServices> namespace fornece wrappers que permitem que os aplicativos .NET para integrar o código gerenciado com serviços de segurança COM+ por meio de <xref:System.EnterpriseServices.ServicedComponent> classe.  
  
 Para obter mais informações, consulte o seguinte recurso.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Segurança baseada em função COM+ e o .NET Framework](https://msdn.microsoft.com/library/02ab22ef-e5e2-4d29-b33a-6e03d94c4981)|Descreve como integrar o código gerenciado com serviços de segurança COM+.|  
  
## <a name="interoperating-with-unmanaged-code"></a>Interoperação com código não gerenciado  
 O .NET Framework fornece para interação com código não gerenciado, inclusive COM componentes, COM + serviços, bibliotecas de tipos externas e muitos serviços do sistema operacional. Trabalhar com código não gerenciado envolve vai fora do perímetro de segurança para código gerenciado. Seu código e qualquer código que o chama devem ter não gerenciados permissão de código (<xref:System.Security.Permissions.SecurityPermission> com o <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> sinalizador especificado). Código não gerenciado pode introduzir vulnerabilidades de segurança não intencionais em seu aplicativo. Portanto, você deve evitar a interoperação com código não gerenciado, a menos que seja absolutamente necessário.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Interoperação com código não gerenciado](../../../../docs/framework/interop/index.md)|Contém tópicos que descrevem como expor componentes COM para o .NET Framework e como expor os componentes do .NET Framework a com.&lt;1}|  
|[Interoperabilidade COM avançada](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)|Contém tópicos avançados, como assemblies de interoperabilidade primários, threading e marshaling personalizado.|  
  
## <a name="see-also"></a>Consulte também  
 [Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [SQL Server Security](../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)  
 [Recomendações para estratégias de acesso a dados](https://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [Construtores de cadeia de Conexão](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
