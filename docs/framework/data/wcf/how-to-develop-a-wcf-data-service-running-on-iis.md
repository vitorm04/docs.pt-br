---
title: 'Como: Desenvolver um WCF Data Service em execução no IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: c9b0128de6459c65e42fc2935222aecc643ec1d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Como: Desenvolver um WCF Data Service em execução no IIS
Este tópico mostra como usar [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] para criar um serviço de dados se baseia em dados de exemplo Northwind que é hospedado por um aplicativo Web ASP.NET que está em execução nos serviços de informações da Internet (IIS). Para obter um exemplo de como criar o mesmo serviço de dados Northwind como um aplicativo Web ASP.NET que é executado no servidor de desenvolvimento ASP.NET, consulte o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
> [!NOTE]
>  Para criar o serviço de dados Northwind, o banco de dados de exemplo Northwind deve estar instalado no computador local. Para baixar esse banco de dados de exemplo, consulte a página de download [bancos de dados do SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).  
  
 Este tópico mostra como criar um serviço de dados usando o provedor de Entity Framework. Outros provedores de serviços de dados estão disponíveis. Para obter mais informações, consulte [provedores de serviços de dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
 Após criar o serviço, você deve fornecer explicitamente acesso aos recursos de serviço de dados. Para obter mais informações, consulte [como: habilitar acesso ao serviço de dados](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).  
  
### <a name="to-create-the-aspnet-web-application-that-runs-on-iis"></a>Para criar o aplicativo Web ASP.NET executado no IIS  
  
1.  No Visual Studio, no **arquivo** menu, selecione **novo**e, em seguida, selecione **projeto**.  
  
2.  No **novo projeto** caixa de diálogo, selecione Visual Basic ou Visual c# como linguagem de programação.  
  
3.  No **modelos** painel, selecione **aplicativo Web ASP.NET**. Observação: se você usar o Visual Studio Web Developer, crie um novo site em vez de um novo aplicativo Web.  
  
4.  Tipo `NorthwindService` como o nome do projeto.  
  
5.  Clique em **OK**.  
  
6.  Sobre o **projeto** menu, selecione **NorthwindService propriedades**.  
  
7.  Selecione o **Web** guia e, em seguida, selecione **usar servidor Web do IIS Local**.  
  
8.  Clique em **criar diretório Virtual** e, em seguida, clique em **Okey**.  
  
9. No prompt de comando com privilégios de administrador, execute um dos seguintes comandos (dependendo do sistema operacional):  
  
    -   sistemas de 32 bits:  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
    -   Sistemas de 64 bits:  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
     Isso garantirá que o Windows Communication Foundation (WCF) será registrado no computador.  
  
10. No prompt de comando com privilégios de administrador, execute um dos seguintes comandos (dependendo do sistema operacional):  
  
    -   sistemas de 32 bits:  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
    -   Sistemas de 64 bits:  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
     Isso garantirá que o IIS será executado corretamente após a instalação do WCF no computador. Talvez seja necessário também reiniciar o IIS.  
  
11. Quando o aplicativo ASP.NET for executado no IIS7, você também deverá executar as seguintes etapas:  
  
    1.  Abra o Gerenciador do IIS e navegue até o aplicativo PhotoService em **Default Web Site**.  
  
    2.  Em **exibição de recursos**, clique duas vezes em **autenticação**.  
  
    3.  Sobre o **autenticação** página, selecione **autenticação anônima**.  
  
    4.  No **ações** painel, clique em **editar** para definir a segurança principal em que usuários anônimos conectará ao site.  
  
    5.  No **Editar credenciais de autenticação anônima** caixa de diálogo, selecione **identidade do pool de aplicativos**.  
  
    > [!IMPORTANT]
    >  Ao usar a conta de Serviço de Rede, você concede a usuários anônimos acesso completo à rede interna associado a essa conta.  
  
12. Usando o SQL Server Management Studio, o utilitário sqlcmd.exe ou o Editor Transact-SQL no Visual Studio, execute o seguinte comando Transact-SQL na instância do SQL Server que tem o banco de dados Northwind anexado:  
  
    ```sql  
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;  
    GO   
    ```  
  
     Isso cria um logon na instância do SQL Server para a conta do Windows usada para executar o IIS. Assim, o IIS pode se conectar à instância do SQL Server.  
  
13. Com o banco de dados Northwind anexado, execute os seguintes comandos Transact-SQL:  
  
    ```sql  
    USE Northwind  
    GO  
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]   
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];  
    GO  
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]   
    WITH DEFAULT_DATABASE=[Northwind];   
    GO  
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'  
    GO  
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'  
    GO   
    ```  
  
     Isso concede direitos ao novo logon, que permite ao IIS ler e gravar dados no banco de dados Northwind.  
  
### <a name="to-define-the-data-model"></a>Para definir o modelo de dados  
  
1.  Em **Solution Explorer**, clique no nome do projeto ASP.NET e, em seguida, clique em **Adicionar Novo Item.**  
  
2.  No **Adicionar Novo Item** caixa de diálogo, selecione **modelo de dados de entidade ADO.NET**.  
  
3.  Para o nome do modelo de dados, digite `Northwind.edmx`.  
  
4.  No Assistente de modelo de dados de entidade, selecione **gerar do banco de dados**e, em seguida, clique em **próximo**.  
  
5.  Conecte o modelo de dados para o banco de dados seguindo um destes procedimentos e, em seguida, clique em **próximo**:  
  
    -   Se você não tiver uma conexão de banco de dados já configurado, clique em **nova Conexão** e criar uma nova conexão. Para obter mais informações, consulte [como: criar conexões com bancos de dados do SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631). Esta instância do SQL Server deve ter o banco de dados de exemplo e anexado.  
  
         \- ou -  
  
    -   Se você tiver uma conexão de banco de dados já configurada para se conectar ao banco de dados Northwind, selecione a conexão da lista de conexões.  
  
6.  Na página final do assistente, selecione as caixas de seleção para todas as tabelas no banco de dados e desmarque as caixas de seleção para exibições e procedimentos armazenados.  
  
7.  Clique em **concluir** para fechar o assistente.  
  
    > [!NOTE]
    >  Esse modelo de dados gerado expõe as propriedades de chave estrangeira em tipos de entidade. Os modelos de dados criados por meio do Visual Studio 2008 não incluem essas propriedades de chave estrangeira. Por isso, você deverá atualizar as classes de serviço de dados do cliente de todos os aplicativos cliente que foram criados para acessar o serviço de dados Northwind criado por meio do Visual Studio 2008 antes de tentar acessar essa versão do serviço de dados Northwind.  
  
### <a name="to-create-the-data-service"></a>Para criar o serviço de dados  
  
1.  Em **Solution Explorer**, clique no nome do seu projeto do ASP.NET e, em seguida, clique em **Adicionar Novo Item**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo, selecione **serviço de dados ADO.NET**.  
  
3.  Para o nome do serviço, digite `Northwind`.  
  
     O Visual Studio cria a marcação XML e os arquivos de código do novo serviço. Por padrão, a janela do editor de códigos é aberta. Em **Solution Explorer**, o serviço terá o nome do Northwind, com a extensão. svc.cs ou. svc.vb.  
  
4.  No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindEntities`. A definição da classe deve ter a seguinte aparência:  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
## <a name="see-also"></a>Consulte também  
 [Expondo seus dados como um serviço](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
