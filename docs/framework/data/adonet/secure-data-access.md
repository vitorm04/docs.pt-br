---
title: Proteger o acesso a dados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 473ebd69-21a3-4627-b95e-4e04d035c56f
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 428dd4cfb9533dbf57b984c8bc1c557f37bb7d15
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="secure-data-access"></a>Proteger o acesso a dados
Para escrever código ADO.NET seguro, você precisa entender os mecanismos de segurança disponíveis no repositório de dados subjacente ou banco de dados. Você também precisa considerar as implicações de segurança de outros recursos ou componentes que seu aplicativo pode conter.  
  
## <a name="authentication-authorization-and-permissions"></a>Autenticação, autorização e permissões  
 Ao se conectar ao Microsoft SQL Server, você pode usar a autenticação do Windows, também conhecido como segurança integrada, que usa a identidade do usuário ativo atual do Windows em vez de passar uma ID de usuário e senha. Usando a autenticação do Windows é altamente recomendável porque as credenciais de usuário não são expostas na cadeia de conexão. Se você não pode usar a autenticação do Windows para se conectar ao SQL Server, considere a criação de cadeias de caracteres de conexão em tempo de execução usando o <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 As credenciais usadas para autenticação precisam ser manipulados variam de acordo com o tipo de aplicativo. Por exemplo, em um aplicativo de formulários do Windows, o usuário pode ser solicitado a fornecer informações de autenticação ou credenciais do Windows do usuário podem ser usadas. No entanto, um aplicativo da Web geralmente acessa dados usando as credenciais fornecidas pelo próprio aplicativo e não pelo usuário.  
  
 Depois que os usuários foram autenticados, o escopo de suas ações depende das permissões que foram concedidas a eles. Sempre siga o princípio de menos privilégios e conceda apenas as permissões que são absolutamente necessárias.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)|Descreve técnicas para proteção de informações de conexão, como usando configuração protegida para criptografar cadeias de caracteres de conexão e práticas recomendadas de segurança.|  
|[Recomendações para estratégias de acesso de dados](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)|Fornece recomendações para acessar dados e executar operações de banco de dados.|  
|[Construtores de cadeia de Conexão](../../../../docs/framework/data/adonet/connection-string-builders.md)|Descreve como criar cadeias de caracteres de conexão de entrada do usuário em tempo de execução.|  
|[Visão geral de segurança do SQL Server](../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)|Descreve a arquitetura de segurança do SQL Server.|  
  
## <a name="parameterized-commands-and-sql-injection"></a>Injeção de SQL e comandos parametrizados  
 Uso de comandos parametrizados ajuda a proteger contra ataques de injeção de SQL, em que um invasor "injeta" um comando em uma instrução SQL que compromete a segurança no servidor. Comandos parametrizados proteger contra um ataque de injeção de SQL, garantindo que os valores recebidos de uma fonte externa são transmitidos como valores somente e não faz parte da instrução Transact-SQL. Como resultado, os comandos Transact-SQL inseridos em um valor não são executados na fonte de dados. Em vez disso, eles serão avaliados somente como um valor de parâmetro. Além dos benefícios de segurança, os comandos com parâmetros fornecem um método conveniente para organizar os valores passados com uma instrução Transact-SQL ou um procedimento armazenado.  
  
 Para obter mais informações sobre como usar comandos com parâmetros, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Parâmetros DataAdapter](../../../../docs/framework/data/adonet/dataadapter-parameters.md)|Descreve como usar parâmetros com um `DataAdapter`.|  
|[Modificando dados com procedimentos armazenados](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)|Descreve como especificar parâmetros e obter um valor de retorno.|  
|[Gerenciando permissões com procedimentos armazenados no SQL Server](../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)|Descreve como usar procedimentos armazenados do SQL Server para encapsular o acesso a dados.|  
  
## <a name="script-exploits"></a>Explorações de script  
 Uma exploração de script é outra forma de injeção que usa mal-intencionado caracteres inseridos em uma página da Web. O navegador não validar os caracteres inseridos e os processa como parte da página.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Visão geral de explorações de script](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|Descreve como se proteger contra scripts e a instrução SQL explorações.|  
  
## <a name="probing-attacks"></a>Investigando ataques  
 Os invasores geralmente usam informações de exceção, como o nome do servidor, banco de dados ou tabela, para montar um ataque no seu sistema. Como exceções podem conter informações específicas sobre seu aplicativo ou a fonte de dados, você pode ajudar a manter sua fonte de dados e aplicativos melhor protegida expondo somente informações essenciais para o cliente.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Fundamentos do tratamento de exceções](../../../../docs/standard/exceptions/exception-handling-fundamentals.md)|Descreve as formas básicas de tratamento estruturado de exceções try/catch/finally.|  
|[Práticas recomendadas para exceções](../../../../docs/standard/exceptions/best-practices-for-exceptions.md)|Descreve as práticas recomendadas para tratamento de exceções.|  
  
## <a name="protecting-microsoft-access-and-excel-data-sources"></a>Protegendo o Microsoft Access e fontes de dados do Excel  
 O Microsoft Access e Microsoft Excel podem agir como um repositório de dados para um aplicativo ADO.NET, quando os requisitos de segurança mínima ou inexistente. Os recursos de segurança são eficazes para bloqueio de privilégios, mas não devem ser usados para evitar que mais de meddling por usuários desinformados. Os arquivos de dados físico para o Access e o Excel existem no sistema de arquivos e devem ser acessíveis a todos os usuários. Isso os torna vulnerável a ataques que podem resultar em roubo ou perda de dados pois os arquivos podem ser facilmente copiados ou alterados. Quando segurança robusta é necessária, use SQL Server ou outro banco de dados com base em servidor onde os arquivos de dados físicos não são legíveis do sistema de arquivos.  
  
 Para obter mais informações sobre a proteção de dados do Access e o Excel, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Considerações sobre segurança e diretrizes para o Access 2007](http://go.microsoft.com/fwlink/?LinkId=98354)|Descreve técnicas de segurança para o Access 2007 tais criptografia de arquivos, administrando senhas, convertendo bancos de dados para os novos formatos ACCDB e ACCDE e usando outras opções de segurança.|  
|[Ajudar a proteger um banco de dados do Access com segurança de nível de usuário (MDB)](http://go.microsoft.com/fwlink/?LinkId=47697)|Aplica-se para o Access 2003. Fornece instruções para implementar a segurança em nível de usuário para proteger os dados no Access 2003.|  
|[Noções básicas sobre a função de arquivos de informações do grupo de trabalho na segurança de acesso](http://support.microsoft.com/kb/305542)|Explica a função e a relação entre o arquivo de informações de segurança do Access 2003.|  
|[Perguntas frequentes perguntas sobre segurança do Microsoft Access para versões do Microsoft Access 2.0 até 2000](http://go.microsoft.com/fwlink/?LinkId=47698)|Versão para download de perguntas frequentes sobre o Microsoft Access segurança.|  
|[Solucionar problemas de segurança e proteção](http://go.microsoft.com/fwlink/?LinkId=47703)|Apresenta soluções para problemas comuns com segurança no Excel 2003.|  
  
## <a name="enterprise-services"></a>Serviços corporativos  
 COM+ contém seu próprio modelo de segurança que se baseia em contas do Windows NT e representação de processo/thread. O <xref:System.EnterpriseServices> namespace fornece wrappers que permitem que os aplicativos .NET integrar o código gerenciado com serviços de segurança COM+ por meio de <xref:System.EnterpriseServices.ServicedComponent> classe.  
  
 Para obter mais informações, consulte o seguinte recurso.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Segurança baseada em função COM+ e o .NET Framework](http://msdn.microsoft.com/en-us/02ab22ef-e5e2-4d29-b33a-6e03d94c4981)|Descreve como integrar o código gerenciado com serviços de segurança do COM+.|  
  
## <a name="interoperating-with-unmanaged-code"></a>Interoperação com código não gerenciado  
 O .NET Framework fornece para interação com código não gerenciado, inclusive COM componentes COM+ serviços, bibliotecas de tipo externo e muitos serviços do sistema operacional. Trabalhando com código não gerenciado envolve saiam do perímetro de segurança para código gerenciado. Seu código e qualquer código que chama devem ter não gerenciado permissão de código (<xref:System.Security.Permissions.SecurityPermission> com o <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> sinalizador especificado). Código não gerenciado pode introduzir vulnerabilidades de segurança não intencionais em seu aplicativo. Portanto, você deve evitar a interoperação com código não gerenciado, a menos que seja absolutamente necessário.  
  
 Para obter mais informações, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Interoperação com código não gerenciado](../../../../docs/framework/interop/index.md)|Contém tópicos que descrevem como expor componentes COM para o .NET Framework e como expor os componentes do .NET Framework para COM.|  
|[Interoperabilidade COM avançada](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)|Contém tópicos avançados, como assemblies de interoperabilidade primários, threading e marshaling personalizado.|  
  
## <a name="see-also"></a>Consulte também  
 [Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [SQL Server Security](../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)  
 [Recomendações para estratégias de acesso de dados](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [Construtores de cadeia de Conexão](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
