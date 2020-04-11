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
ms.openlocfilehash: 8a1a0c2c55267940463e2c9ab82bb52345269260
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121607"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Como: Desenvolver um serviço de dados WCF em execução no IIS

Este artigo mostra como usar o WCF Data Services para criar um serviço de dados baseado no banco de dados de amostra do Northwind hospedado por um aplicativo da Web ASP.NET em execução no Internet Information Services (IIS). Para um exemplo de como criar o mesmo serviço de dados Northwind como um aplicativo web ASP.NET que é executado no ASP.NET Development Server, consulte o [wcf data services quickstart](quickstart-wcf-data-services.md).

> [!NOTE]
> Para criar o serviço de dados Northwind, instale primeiro o banco de dados de amostras northwind no computador local. Para instalar o banco de dados, execute o script Transact-SQL dos bancos de dados de [amostra de Northwind e pubs para o Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).

Este artigo mostra como criar um serviço de dados usando o provedor Entity Framework. Outros provedores de serviços de dados estão disponíveis. Para obter mais informações, consulte [Provedores de Serviços de Dados](data-services-providers-wcf-data-services.md).

Após criar o serviço, você deve fornecer explicitamente acesso aos recursos de serviço de dados. Para obter mais informações, [consulte Como habilitar o acesso ao Serviço de Dados.](how-to-enable-access-to-the-data-service-wcf-data-services.md)

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a>Crie o aplicativo web ASP.NET que é executado no IIS

1. No Visual Studio, no menu **Arquivo**, selecione **Novo** > **Projeto**.

2. Na caixa de diálogo **Novo Projeto,** selecione a categoria > **instalada** [**Visual C#** ou **Visual Basic]** **>.**

3. Selecione o modelo **Aplicativo Web ASP .NET** .

4. Digite `NorthwindService` como o nome do projeto.

5. Clique em **OK**.

6. No **menu Projeto,** selecione **NorthwindService Properties**.

7. Selecione a guia **Web** e, em seguida, selecione **Usar servidor web IIS local**.

8. Clique **em Criar diretório virtual** e clique em **OK**.

9. No prompt de comando com privilégios de administrador, execute um dos seguintes comandos (dependendo do sistema operacional):

    - Sistemas de 32 bits:

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - Sistemas de 64 bits:

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     Isso garantirá que o Windows Communication Foundation (WCF) será registrado no computador.

10. No prompt de comando com privilégios de administrador, execute um dos seguintes comandos (dependendo do sistema operacional):

    - Sistemas de 32 bits:

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - Sistemas de 64 bits:

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     Isso garantirá que o IIS será executado corretamente após a instalação do WCF no computador. Talvez seja necessário também reiniciar o IIS.

11. Quando o aplicativo ASP.NET for executado no IIS7, você também deverá executar as seguintes etapas:

    1. Abra o IIS Manager e navegue até o aplicativo PhotoService em **Site padrão da Web**.

    2. Em **Exibição de Recursos**, clique duas vezes em **Autenticação**.

    3. Na página **Autenticação**, selecione **Autenticação anônima**.

    4. No painel **Ações,** clique em **Editar** para definir o principal de segurança sob o qual os usuários anônimos se conectarão ao site.

    5. Na caixa de diálogo Editar credenciais de **autenticação anônima,** selecione **identidade do pool de aplicativos**.

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

1. No **Solution Explorer,** clique com o botão direito do mouse no nome do projeto ASP.NET e clique em **Adicionar** > **novo item**.

2. Na caixa de diálogo **Adicionar novo item,** selecione **ADO.NET Modelo de Dados da Entidade**.

3. Para o nome do modelo `Northwind.edmx`de dados, digite .

4. No Assistente de Modelo de Dados da Entidade, selecione **Gerar a partir do banco de dados**e clique em **Seguir**.

5. Conecte o modelo de dados ao banco de dados fazendo uma das seguintes etapas e clique em **"Aseguir:**

    - Se você não tiver uma conexão de banco de dados já configurada, clique em **Nova Conexão** e crie uma nova conexão. Para obter mais informações, consulte [Como: Criar conexões para bancos de dados do Servidor SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)). Esta instância do SQL Server deve ter o banco de dados de amostra northwind anexado.

         \- ou –

    - Se você tiver uma conexão de banco de dados já configurada para se conectar ao banco de dados Northwind, selecione a conexão da lista de conexões.

6. Na página final do assistente, selecione as caixas de seleção para todas as tabelas no banco de dados e desmarque as caixas de seleção para exibições e procedimentos armazenados.

7. Clique em **Concluir** para fechar o assistente.

## <a name="create-the-data-service"></a>Criar o serviço de dados

1. No **Solution Explorer,** clique com o botão direito do mouse no nome do seu projeto ASP.NET e clique em **Adicionar** > **novo item**.

2. Na caixa de diálogo **Adicionar novo item,** selecione **WCF Data Service**.

   ![Modelo de item do WCF Data Service no Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > O modelo **wcf data service** está disponível no Visual Studio 2015, mas não no Visual Studio 2017 ou posterior.

3. Para o nome do `Northwind`serviço, digite .

     O Visual Studio cria a marcação XML e os arquivos de código do novo serviço. Por padrão, a janela do editor de códigos é aberta. No **Solution Explorer,** o serviço tem o nome, Northwind, e a extensão .svc.cs ou .svc.vb.

4. No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindEntities`. A definição da classe deve ter a seguinte aparência:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a>Confira também

- [Expor seus dados como um serviço](exposing-your-data-as-a-service-wcf-data-services.md)
