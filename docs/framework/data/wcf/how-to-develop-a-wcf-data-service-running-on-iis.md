---
title: 'Como: desenvolver um serviço de dados do WCF em execução no IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 89be7aa8339a4edf6d6ab9c0c243e4320d2fdfa8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052970"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Como: Desenvolver um serviço de dados WCF em execução no IIS

Este tópico mostra como usar WCF Data Services para criar um serviço de dados que é baseado no exemplo Northwind que é hospedado por um aplicativo Web ASP.NET em execução no Serviços de Informações da Internet (IIS). Para obter um exemplo de como criar o mesmo serviço de dados Northwind como um aplicativo Web ASP.NET que é executado no ASP.NET Development Server, consulte o guia de [início rápido WCF Data Services](quickstart-wcf-data-services.md).

> [!NOTE]
> Para criar o serviço de dados Northwind, o banco de dados de exemplo Northwind deve estar instalado no computador local. Para baixar esse banco de dados de exemplo, consulte a página de download, [bancos de dados de exemplo para SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).

Este tópico mostra como criar um serviço de dados usando o provedor de Entity Framework. Outros provedores de serviços de dados estão disponíveis. Para obter mais informações, consulte [provedores de serviços de dados](data-services-providers-wcf-data-services.md).

Após criar o serviço, você deve fornecer explicitamente acesso aos recursos de serviço de dados. Para obter mais informações, confira [Como: Habilite o acesso ao serviço](how-to-enable-access-to-the-data-service-wcf-data-services.md)de dados.

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a>Criar o aplicativo Web ASP.NET que é executado no IIS

1. No Visual Studio, no menu **arquivo** , selecione **novo** > **projeto**.

2. Na caixa de diálogo **novo projeto** , selecione a categoria **da Web** > **instalada** [ **C# Visual** ou **Visual Basic**] >.

3. Selecione o modelo de **aplicativo Web ASP.net** .

4. Insira `NorthwindService` como o nome do projeto.

5. Clique em **OK**.

6. No menu **projeto** , selecione **NorthwindService Propriedades**.

7. Selecione a guia **Web** e, em seguida, selecione **usar servidor Web IIS local**.

8. Clique em **criar diretório virtual** e em **OK**.

9. No prompt de comando com privilégios de administrador, execute um dos seguintes comandos (dependendo do sistema operacional):

    - sistemas de 32 bits:

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - Sistemas de 64 bits:

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     Isso garantirá que o Windows Communication Foundation (WCF) será registrado no computador.

10. No prompt de comando com privilégios de administrador, execute um dos seguintes comandos (dependendo do sistema operacional):

    - sistemas de 32 bits:

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - Sistemas de 64 bits:

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     Isso garantirá que o IIS será executado corretamente após a instalação do WCF no computador. Talvez seja necessário também reiniciar o IIS.

11. Quando o aplicativo ASP.NET for executado no IIS7, você também deverá executar as seguintes etapas:

    1. Abra o Gerenciador do IIS e navegue até o aplicativo de serviço em **site da Web padrão**.

    2. Na **exibição recursos**, clique duas vezes em **autenticação**.

    3. Na página **autenticação** , selecione **autenticação anônima**.

    4. No painel **ações** , clique em **Editar** para definir a entidade de segurança sob a qual os usuários anônimos se conectarão ao site.

    5. Na caixa de diálogo **Editar credenciais de autenticação anônima** , selecione **identidade do pool de aplicativos**.

    > [!IMPORTANT]
    > Ao usar a conta de Serviço de Rede, você concede a usuários anônimos acesso completo à rede interna associado a essa conta.

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

## <a name="define-the-data-model"></a>Definir o modelo de dados

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nome do projeto ASP.net e clique em **Adicionar** > **novo item**.

2. Na caixa de diálogo **Adicionar novo item** , selecione **ADO.NET modelo de dados de entidade**.

3. Para o nome do modelo de dados, digite `Northwind.edmx`.

4. No assistente de Modelo de Dados de Entidade, selecione **gerar do banco de dados**e clique em **Avançar**.

5. Conecte o modelo de dados ao banco de dado executando uma das etapas a seguir e clique em **Avançar**:

    - Se você não tiver uma conexão de banco de dados já configurada, clique em **nova conexão** e crie uma nova conexão. Para obter mais informações, confira [Como: Crie conexões com bancos de dados](https://go.microsoft.com/fwlink/?LinkId=123631)SQL Server. Esta instância de SQL Server deve ter o banco de dados de exemplo Northwind anexado.

         \- ou -

    - Se você tiver uma conexão de banco de dados já configurada para se conectar ao banco de dados Northwind, selecione a conexão da lista de conexões.

6. Na página final do assistente, selecione as caixas de seleção para todas as tabelas no banco de dados e desmarque as caixas de seleção para exibições e procedimentos armazenados.

7. Clique em **Concluir** para fechar o assistente.

## <a name="create-the-data-service"></a>Criar o serviço de dados

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nome do seu projeto ASP.net e clique em **Adicionar** > **novo item**.

2. Na caixa de diálogo **Adicionar novo item** , selecione **WCF Data Service**.

   ![Modelo de item do WCF Data Service no Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > O modelo do **WCF Data Service** está disponível no visual Studio 2015, mas não no visual Studio 2017.

3. Para o nome do serviço, digite `Northwind`.

     O Visual Studio cria a marcação XML e os arquivos de código do novo serviço. Por padrão, a janela do editor de códigos é aberta. No **Gerenciador de soluções**, o serviço tem o nome, Northwind e a extensão. svc.cs ou. svc. vb.

4. No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindEntities`. A definição da classe deve ter a seguinte aparência:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a>Consulte também

- [Expondo seus dados como um serviço](exposing-your-data-as-a-service-wcf-data-services.md)
