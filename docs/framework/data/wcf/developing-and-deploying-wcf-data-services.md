---
title: Desenvolvendo e implantando WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: 5c473f818ea874392011065dc3d07101d2ef3bf5
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607952"
---
# <a name="develop-and-deploy-wcf-data-services"></a>Desenvolver e implantar serviços de dados WCF

Este artigo fornece informações sobre o desenvolvimento e a implantação de Serviços de Dados WCF. Para obter informações mais básicas sobre os Serviços de Dados WCF, consulte [Getting Started](getting-started-with-wcf-data-services.md) e [Overview](wcf-data-services-overview.md).

## <a name="develop-wcf-data-services"></a>Desenvolver serviços de dados WCF

Quando você usa o WCF Data Services para criar um serviço de dados que suporta o OData (Open Data Protocol, protocolo de dados abertos), você deve executar as seguintes tarefas básicas durante o desenvolvimento:

1. **Definir o modelo de dados**

     O WCF Data Services suporta uma variedade de provedores de serviços de dados que permitem definir um modelo de dados com base em dados de uma variedade de fontes de dados, desde bancos de dados relacionais até tipos de dados vinculados ao final. Para obter mais informações, consulte [Provedores de Serviços de Dados](data-services-providers-wcf-data-services.md).

2. **Criar o serviço de dados**

     O serviço de dados mais básico expõe uma classe herdada da classe <xref:System.Data.Services.DataService%601>, com um tipo `T` que é o nome qualificado para namespace do contêiner de entidade. Para obter mais informações, consulte [Definindo os Serviços de Dados wcf](defining-wcf-data-services.md).

3. **Configurar o serviço de dados**

     Por padrão, o WCF Data Services desativa o acesso a recursos expostos por um contêiner de entidade. A <xref:System.Data.Services.DataServiceConfiguration> interface permite configurar o acesso a recursos e operações de serviço, especificar a versão suportada do OData e definir outros comportamentos em todo o serviço, como comportamentos de loteamento ou o número máximo de entidades que podem ser retornadas em um único feed de resposta. Para obter mais informações, consulte [Configurando o Serviço de Dados](configuring-the-data-service-wcf-data-services.md).

Este artigo abrange principalmente o desenvolvimento e a implantação de serviços de dados usando o Visual Studio. Para obter informações sobre a flexibilidade fornecida pelos Serviços de Dados wcf para expor seus dados como feeds OData, consulte [Definindo serviços de dados WCF](defining-wcf-data-services.md).

### <a name="choose-a-development-web-server"></a>Escolha um servidor web de desenvolvimento

Quando você desenvolve um WCF Data Service como um aplicativo ASP.NET ou ASP.NET site usando o Visual Studio 2015, você tem uma escolha de servidores Web nos quais executar o serviço de dados durante o desenvolvimento. Os seguintes servidores web integram-se ao Visual Studio para facilitar o teste e depuração de seus serviços de dados no computador local.

1. **Servidor de IIS local**

     Quando você cria um serviço de dados que é um aplicativo de ASP.NET ou ASP.NET site que funciona no Internet Information Services (IIS), recomendamos que você desenvolva e teste seu serviço de dados usando o IIS no computador local. Executar o serviço de dados no IIS facilita o rastreamento de solicitações HTTP durante a depuração. Isso também permite que você predetermine os direitos necessários exigidos pelo IIS para acessar arquivos, bancos de dados e outros recursos exigidos pelo serviço de dados. Para executar seu serviço de dados no IIS, certifique-se de que tanto o IIS quanto o Windows Communication Foundation (WCF) estejam instalados e configurados corretamente e concedam acesso a contas IIS no sistema de arquivos e bancos de dados. Para obter mais informações, consulte [Como desenvolver um serviço de dados WCF em execução no IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

    > [!NOTE]
    > Você deve executar o Visual Studio com os direitos de administrador para permitir que o ambiente de desenvolvimento configure o servidor IIS local.

2. **Visual Studio Development Server**

     O Visual Studio inclui um servidor Web integrado, o Visual Studio Development Server, que é o servidor Web padrão para projetos ASP.NET. Este servidor Web foi projetado para executar projetos ASP.NET no computador local durante o desenvolvimento. O [quickstart do WCF Data Services](quickstart-wcf-data-services.md) mostra como criar um serviço de dados que é executado no Visual Studio Development Server.

     Esteja ciente das seguintes limitações ao usar o Visual Studio Development Server para desenvolver o serviço de dados:

    - Este servidor só pode ser acessado no computador local.

    - Este servidor escuta no `localhost` e em uma porta específica, não na porta 80, que é a porta padrão para mensagens HTTP. Para obter mais informações, consulte [Servidores Web no Visual Studio para projetos Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

    - Este servidor executa o serviço de dados no contexto de sua conta de usuário atual. Por exemplo, se você estiver executando como um usuário de nível de administrador, um serviço de dados em execução no Visual Studio Development Server terá privilégios no nível do administrador. Isso pode fazer o serviço de dados ser capaz de acessar recursos que ele não tem os direitos de acesso quando implantado em um servidor IIS.

    - Este servidor não inclui os recursos adicionais do IIS, como autenticação.

    - Esse servidor não pode lidar com fluxos HTTP em pedaços, que são enviados por padrão pelo cliente WCF Data Services ao acessar grandes dados binários do serviço de dados. Para obter mais informações, consulte [Provedor de Streaming](streaming-provider-wcf-data-services.md).

    - Este servidor tem problemas com`.`o processamento do caractere period ( ) em uma URL, mesmo que este caractere seja suportado pelo WCF Data Services em valores-chave.

    > [!TIP]
    > Mesmo que você possa usar o Visual Studio Development Server para testar seus serviços de dados durante o desenvolvimento, você deve testá-los novamente depois de implantá-los em um servidor Web que está executando o IIS.

3. **Ambiente de Desenvolvimento Azure**

     O Windows Azure Tools for Visual Studio inclui um conjunto integrado de ferramentas para o desenvolvimento de serviços Azure no Visual Studio. Com essas ferramentas, você pode desenvolver um serviço de dados que pode ser implantado no Azure, e você pode testar o serviço de dados no computador local antes da implantação. Use essas ferramentas ao usar o Visual Studio para desenvolver um serviço de dados que seja executado na plataforma Azure. Para obter informações sobre a instalação das ferramentas, consulte as [ferramentas do Azure para o Visual Studio 2015](../../../azure/sdk/vs2015-install.md). Para obter mais informações sobre o desenvolvimento de um serviço de dados que seja executado no Azure, consulte o post [Implantando um Serviço de OData no Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="development-tips"></a>Dicas de desenvolvimento

Considere o seguinte quando você desenvolve um serviço de dados:

- Se você planeja autenticar usuários ou restringir o acesso a usuários específicos, determine os requisitos de segurança do seu serviço de dados. Para obter mais informações, consulte [Protegendo os Serviços de Dados WCF](securing-wcf-data-services.md).

- Um programa de inspeção HTTP pode ser útil ao depurar um serviço de dados, permitindo que você inspecione o conteúdo das mensagens de solicitação e resposta. Qualquer analisador de pacote de rede que possa exibir pacotes brutos pode ser usado para inspecionar solicitações HTTP para e respostas do serviço de dados.

- Ao depurar um serviço de dados, você pode querer obter mais informações sobre um erro do serviço de dados do que durante a operação regular. Você pode obter informações de erro adicionais do serviço de dados definindo a propriedade <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> no <xref:System.Data.Services.DataServiceConfiguration> para `true` e definindo a propriedade <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> do atributo <xref:System.ServiceModel.Description.ServiceDebugBehavior> na classe de serviço de dados como `true`. Para obter mais informações, consulte o post [Depuração de Serviços de Dados WCF](https://docs.microsoft.com/archive/blogs/phaniraj/debugging-wcf-data-services). Você também pode habilitar o rastreamento no WCF para visualizar as exceções levantadas na camada de mensagens HTTP. Para obter mais informações, consulte [Configuração de rastreamento](../../wcf/diagnostics/tracing/configuring-tracing.md).

- Um serviço de dados geralmente é desenvolvido como um projeto de aplicativo ASP.NET, mas você também pode criar seu serviço de dados como um ASP.NET projeto de site no Visual Studio. Para obter informações sobre as diferenças entre os dois tipos de projetos, consulte Projetos de [Aplicações Web versus Projetos de Sites no Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd547590(v=vs.110)).

- Quando você cria um serviço de dados usando a caixa de diálogo **Adicionar novo item** no Visual Studio, o serviço de dados é hospedado por ASP.NET no IIS. Enquanto ASP.NET e IIS é o host padrão para um serviço de dados, outras opções de hospedagem são suportadas. Para obter mais informações, consulte [Hosting the Data Service](hosting-the-data-service-wcf-data-services.md).

## <a name="deploy-wcf-data-services"></a>Implantar serviços de dados WCF

O WCF Data Service fornece flexibilidade na escolha do processo que hospeda o serviço de dados. Você pode usar o Visual Studio para implantar um serviço de dados nas seguintes plataformas:

- **Servidor Web hospedado no IIS**

    Quando um serviço de dados é desenvolvido como um projeto ASP.NET, ele pode ser implantado em um servidor Web IIS usando os processos de implantação de ASP.NET padrão. O Visual Studio fornece as seguintes tecnologias de implantação para ASP.NET, dependendo do tipo de projeto ASP.NET que hospeda o serviço de dados que você está implantando.

  - **Tecnologias de implantação para aplicativos Web ASP.NET**

    - [Como: Criar um pacote de implantação web no Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465323(v=vs.110))

    - [Como: Implantar um projeto web usando um clique publicar no Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))

  - **Tecnologias de implantação para sites Web ASP.NET**

    - [Como: Copiar arquivos do site com a ferramenta copiar o site](https://docs.microsoft.com/previous-versions/aspnet/c95809c0(v=vs.100))

    - [Como: Publicar sites](https://docs.microsoft.com/previous-versions/aspnet/20yh9f1b(v=vs.100))

    - [Passo a passo: Implantando um aplicativo web ASP.NET usando xcopy](https://docs.microsoft.com/previous-versions/aspnet/f735abw9(v=vs.100))

     Para obter mais informações sobre as opções de implantação de um aplicativo ASP.NET, consulte [visão geral de implantação da Web para o Visual Studio e ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/dd394698(v=vs.110)).

    > [!TIP]
    > Antes de tentar implantar o serviço de dados para o IIS, verifique se você testou a implantação para um servidor Web que esteja executando o IIS. Para obter mais informações, consulte [Como desenvolver um serviço de dados WCF em execução no IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

- **Azure**

     Você pode implantar um serviço de dados no Azure usando [o Azure Tools for Visual Studio](../../../azure/sdk/vs2015-install.md). Para obter mais informações sobre como implantar um serviço de dados no Azure, consulte [Implantando um Serviço de Dados no Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="deployment-considerations"></a>Considerações de implantação

Considere o seguinte ao implantar um serviço de dados:

- Quando você implanta um serviço de dados que usa o provedor Entity Framework para acessar um banco de dados SQL Server, você também pode ter que propagar estruturas de dados, dados ou ambos com a implantação do serviço de dados. O Visual Studio pode criar scripts (.sql files) automaticamente para fazer isso no banco de dados de destino, e esses scripts podem ser incluídos no pacote de implantação da Web de um aplicativo ASP.NET. Para obter mais informações, consulte [Como implantar um banco de dados com um projeto de aplicativo web.](https://docs.microsoft.com/previous-versions/dd465343(v=vs.100)) Para um site ASP.NET, você pode fazer isso usando o **Assistente de Publicação de Banco de Dados** no Visual Studio. Para obter mais informações, consulte [Publicando um banco de dados SQL](https://docs.microsoft.com/previous-versions/aspnet/bb907585(v=vs.100)).

- Como o WCF Data Services inclui uma implementação básica do WCF, você pode usar o Windows Server AppFabric para monitorar um serviço de dados implantado no IIS em execução no Windows Server. Para obter mais informações sobre como usar o Windows Server AppFabric para monitorar um serviço de dados, consulte o post [Tracking WCF Data Services com o Windows Server AppFabric](https://docs.microsoft.com/archive/blogs/rjacobs/tracking-wcf-data-services-with-windows-server-appfabric).

## <a name="see-also"></a>Confira também

- [Hospedar o serviço de dados](hosting-the-data-service-wcf-data-services.md)
- [Protegendo o WCF Data Services](securing-wcf-data-services.md)
- [Configurando WCF Data Services](defining-wcf-data-services.md)
