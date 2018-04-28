---
title: Desenvolvendo e implantando WCF Data Services
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d20d4c39a6cca744ac981d1a143d2847d9b20e5a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="developing-and-deploying-wcf-data-services"></a>Desenvolvendo e implantando WCF Data Services
Este tópico fornece informações sobre como desenvolver e implantar o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Para obter mais informações sobre [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], consulte [Introdução](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md) e [visão geral](../../../../docs/framework/data/wcf/wcf-data-services-overview.md).  
  
## <a name="developing-wcf-data-services"></a>Desenvolvendo WCF Data Services  
 Quando você usa o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] para criar um serviço de dados que dá suporte ao [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], deve executar as seguintes tarefas básicas durante o desenvolvimento:  
  
1.  **Definir o modelo de dados**  
  
     O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] oferece suporte a uma variedade de provedores de serviços de dados que permitem que você defina um modelo de dados com base nos dados de uma variedade de fontes de dados, de bancos de dados relacionais a tipos de dados de associação tardia. Para obter mais informações, consulte [provedores de serviços de dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
2.  **Criar o serviço de dados**  
  
     O serviço de dados mais básico expõe uma classe herdada da classe <xref:System.Data.Services.DataService%601>, com um tipo `T` que é o nome qualificado para namespace do contêiner de entidade. Para obter mais informações, consulte [definindo o WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
3.  **Configurar o serviço de dados**  
  
     Por padrão, o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] desativa o acesso a recursos que são expostos por um contêiner de entidade. A interface <xref:System.Data.Services.DataServiceConfiguration> permite configurar o acesso a recursos e a operações de serviço, especificar a versão com suporte do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] e definir outros comportamentos de serviços, como comportamentos de lote ou o número máximo de entidades que podem ser retornadas em um único feed de resposta. Para obter mais informações, consulte [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Este tópico aborda principalmente a desenvolvimento e implantação dos serviços de dados usando o Visual Studio. Para obter informações sobre a flexibilidade fornecida pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] para expor seus dados como [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds, consulte [definindo o WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
### <a name="choosing-a-development-web-server"></a>Escolhendo um servidor Web de desenvolvimento  
 Ao desenvolver um WCF Data Services como um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo ou [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] site da Web usando o Visual Studio, você tem a opção de servidores de Web no qual executar o serviço de dados durante o desenvolvimento. Os seguintes servidores Web integram com o Visual Studio para tornar mais fácil de testar e depurar seus serviços de dados no computador local.  
  
1.  **Servidor IIS local**  
  
     Quando você cria um serviço de dados que é um aplicativo do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ou um site do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] que é executado nos Serviços de Informações da Internet (IIS), recomendamos que você desenvolva e teste o serviço de dados usando o IIS no computador local. Executar o serviço de dados no IIS facilita o rastreamento de solicitações HTTP durante a depuração. Isso também permite que você predetermine os direitos necessários exigidos pelo IIS para acessar arquivos, bancos de dados e outros recursos necessários pelo serviço de dados. Para executar o serviço de dados no IIS, você deverá verificar se o IIS e o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] estão instalados e configurados corretamente e deverá conceder acesso às contas do IIS no sistema de arquivos e em bancos de dados. Para obter mais informações, consulte [como: desenvolver um WCF Data Service em execução no IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
    > [!NOTE]
    >  Você deve executar o Visual Studio com direitos de administrador para habilitar o ambiente de desenvolvedor configurar o servidor IIS local.  
  
2.  **Servidor de desenvolvimento do Visual Studio**  
  
     O Visual Studio inclui um servidor Web interno, o servidor de desenvolvimento do Visual Studio, que é o servidor de Web padrão para [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projetos. Este servidor Web é criado para executar projetos do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] no computador local durante o desenvolvimento. O [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) mostra como criar um serviço de dados que é executado no Visual Studio Development Server.  
  
     Quando você usar o servidor de desenvolvimento do Visual Studio para desenvolver o serviço de dados, você deve estar ciente das seguintes limitações:  
  
    -   Este servidor só pode ser acessado no computador local.  
  
    -   Este servidor escuta no `localhost` e em uma porta específica, não na porta 80, que é a porta padrão para mensagens HTTP. Para obter mais informações, consulte [Servidores Web no Visual Studio para projetos Web ASP.NET](http://msdn.microsoft.com/library/31d4f588-df59-4b7e-b9ea-e1f2dd204328).  
  
    -   Este servidor executa o serviço de dados no contexto de sua conta de usuário atual. Por exemplo, se você estiver executando como um usuário de nível de administrador, um serviço de dados em execução no Visual Studio Development Server terá privilégios de administrador. Isso pode fazer o serviço de dados ser capaz de acessar recursos que ele não tem os direitos de acesso quando implantado em um servidor IIS.  
  
    -   Este servidor não inclui os recursos adicionais do IIS, como autenticação.  
  
    -   Este servidor não pode manipular fluxos HTTP em partes, que são enviados por padrão pelo cliente do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ao acessar dados binários grandes do serviço de dados. Para obter mais informações, consulte [provedor Streaming](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
    -   Este servidor tem problemas ao processar o caractere de ponto (`.`) em uma URL, mesmo que esse caractere tenha suporte pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] em valores chave.  
  
    > [!TIP]
    >  Embora você possa usar o servidor de desenvolvimento do Visual Studio para testar seus serviços de dados durante o desenvolvimento, você deve testá-las novamente após a implantação para um servidor Web que está executando o IIS.  
  
3.  **Ambiente de desenvolvimento do Azure Windows**  
  
     Ferramentas do Windows Azure para Visual Studio inclui um conjunto integrado de ferramentas para desenvolvimento de serviços do Windows Azure no Visual Studio. Com essas ferramentas, você pode desenvolver um serviço de dados que pode ser implantado no Microsoft Azure e você pode testar o serviço de dados no computador local antes da implantação. Use essas ferramentas quando usando o Visual Studio para desenvolver um serviço de dados que é executado na plataforma Windows Azure. Você pode baixar as ferramentas do Windows Azure para Visual Studio a partir de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=201848). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] desenvolvendo um serviço de dados que é executado no Windows Azure, consulte a postagem [Implantando um OData Service no Windows Azure](http://go.microsoft.com/fwlink/?LinkId=201847).  
  
### <a name="development-tips"></a>Dicas de desenvolvimento  
 Você deve considerar o seguinte ao desenvolver um serviço de dados:  
  
-   Determinar os requisitos de segurança de seu serviço de dados, se planejar autenticar usuários ou restringir o acesso para usuários específicos. Para obter mais informações, consulte [protegendo o WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
-   Um programa de inspeção de HTTP pode ser muito útil ao depurar um serviço de dados permitindo que você inspecione o conteúdo de mensagens de solicitação e resposta. Qualquer analisador de pacote de rede que possa exibir pacotes brutos pode ser usado para inspecionar solicitações HTTP para e respostas do serviço de dados.  
  
-   Para depurar um serviço de dados, você pode desejar obter mais informações sobre um erro do serviço de dados do que durante a operação normal. Você pode obter informações de erro adicionais do serviço de dados definindo a propriedade <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> no <xref:System.Data.Services.DataServiceConfiguration> para `true` e definindo a propriedade <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> do atributo <xref:System.ServiceModel.Description.ServiceDebugBehavior> na classe de serviço de dados como `true`. Para obter mais informações, consulte a postagem [depuração WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=201868). Você também pode habilitar o rastreamento no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para exibir as exceções geradas na camada de mensagens HTTP. Para obter mais informações, consulte [Configurando rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
-   Um serviço de dados geralmente é desenvolvido como um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projeto de aplicativo, mas você também pode criar você serviço de dados como um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projeto de site da Web no Visual Studio. Para obter informações sobre as diferenças entre os dois tipos de projetos, consulte [NIB: projetos de aplicativos Web versus projetos de Site da Web no Visual Studio](http://msdn.microsoft.com/library/2861815e-f5a2-4378-a2f8-b8a86dc012f5).  
  
-   Quando você cria um serviço de dados usando o **Adicionar Novo Item** caixa de diálogo no Visual Studio, o serviço de dados é hospedada pelo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] no IIS. Embora o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] e o IIS sejam o host padrão para um serviço de dados, outras opções de hospedagem têm suporte. Para obter mais informações, consulte [hospeda o serviço de dados](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md).  
  
## <a name="deploying-wcf-data-services"></a>Implantando WCF Data Services  
 O WCF Data Service fornece flexibilidade na escolha do processo que hospeda o serviço de dados. Você pode usar o Visual Studio para implantar um serviço de dados para as seguintes plataformas:  
  
-   **Servidor Web hospedados no IIS**  
  
     Quando um serviço de dados é desenvolvido como um projeto do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], ele pode ser implantado em um servidor Web no IIS usando os processos de implantação padrão do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  As seguintes tecnologias de implantação para o Visual Studio fornece [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], dependendo do tipo de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projeto que hospeda o serviço de dados que você está implantando.  
  
    -   **Tecnologias de implantação para aplicativos Web ASP.NET**  
  
        -   [Pacote de implantação da Web](http://msdn.microsoft.com/library/1f9713c8-9540-494c-b80d-9893b970ad6f)  
  
        -   [Publicação de um clique](http://msdn.microsoft.com/library/59226246-99ad-4aec-975d-7c61e8a8911c)  
  
    -   **Tecnologias de implantação para Sites da Web ASP.NET**  
  
        -   [Copie a ferramenta de Site](http://msdn.microsoft.com/library/b819aed4-014b-427e-be80-02317b1bb003)  
  
        -   [Ferramenta Publicar Web Site](http://msdn.microsoft.com/library/d0a1a20f-15be-4940-9485-cb8e4aa8181b)  
  
        -   [XCopy](http://msdn.microsoft.com/library/4312c651-2119-49be-bbeb-ee28bdbfe71e)  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] as opções de implantação para um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo, consulte [visão geral da implantação da Web do Visual Studio e ASP.NET](http://msdn.microsoft.com/library/99bd1927-b59f-4e02-87b4-55c6ba2adbc3).  
  
    > [!TIP]
    >  Antes de tentar implantar o serviço de dados para o IIS, verifique se você testou a implantação para um servidor Web que esteja executando o IIS. Para obter mais informações, consulte [como: desenvolver um WCF Data Service em execução no IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
-   **Windows Azure**  
  
     Você pode implantar um serviço de dados para o Windows Azure usando ferramentas do Windows Azure para Visual Studio. Você pode baixar as ferramentas do Windows Azure para Visual Studio a partir de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=201848). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Implantando um serviço de dados para o Windows Azure, consulte a postagem [Implantando um OData Service no Windows Azure](http://go.microsoft.com/fwlink/?LinkId=201847).  
  
### <a name="deployment-considerations"></a>Considerações de implantação  
 Você deve considerar o seguinte ao implantar um serviço de dados:  
  
-   Quando você implanta um serviço de dados que usa o provedor do [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] para acessar um banco de dados do SQL Server, você também pode ter que propagar as estruturas de dados, os dados ou ambos com a implantação do serviço de dados. O Visual Studio automaticamente pode criar scripts (arquivos. SQL) para fazer isso no banco de dados de destino, e esses scripts podem ser incluídos no pacote de implantação da Web de um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo. Para obter mais informações, consulte [NIB: como: implantar um banco de dados com um projeto de aplicativo Web](http://msdn.microsoft.com/library/683b33f1-8a3d-45cf-af6e-61ab50fc518b). Para uma [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] site da Web, você pode fazer isso usando o **Assistente de publicação de banco de dados** no Visual Studio. Para obter mais informações, consulte [Implantando um banco de dados usando o Assistente de publicação de banco de dados](http://msdn.microsoft.com/library/1e3682e7-8b57-4da6-a393-af9640ccf8b7).  
  
-   Como o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclui uma implementação básica do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], você pode usar o Windows Server AppFabric para monitorar um serviço de dados implantado no IIS executando no Windows Server. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] usando o Windows Server AppFabric para monitorar um serviço de dados, consulte a postagem [de rastreamento do WCF Data Services com o Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=202005).  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem o serviço de dados](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)  
 [Protegendo o WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)
