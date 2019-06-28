---
title: Criando um serviço de fluxo de trabalho de execução longa
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: 1ca0f2ed4c2ab900191165d100848811e5436c3c
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425413"
---
# <a name="creating-a-long-running-workflow-service"></a>Criando um serviço de fluxo de trabalho de execução longa
Este tópico descreve como criar um serviço de fluxo de trabalho de longa execução. Serviços de fluxo de trabalho de longa execução pode ser executada por longos períodos de tempo. Em algum momento o fluxo de trabalho poderá ficar ocioso enquanto aguarda para obter informações adicionais. Quando isso acontece o fluxo de trabalho é mantido para um banco de dados SQL e é removido da memória. Quando as informações adicionais está disponível a instância de fluxo de trabalho é carregada para a memória e continua executando.  Nesse cenário, você está implementando um sistema de pedidos muito simplificado.  O cliente envia uma mensagem inicial para o serviço de fluxo de trabalho para iniciar a ordem. Ele retorna uma ID de pedido para o cliente. Neste ponto o serviço de fluxo de trabalho está aguardando a outra mensagem do cliente e entra no estado ocioso e é mantido para um banco de dados do SQL Server.  Quando o cliente envia a próxima mensagem a um item de ordem, o serviço de fluxo de trabalho é carregado para a memória e termina de processar o pedido. No exemplo de código, ele retorna uma cadeia de caracteres informando que o item foi adicionado ao pedido. O exemplo de código não deve ser um aplicativo do mundo real da tecnologia, mas em vez disso, um exemplo simple que ilustra os serviços de fluxo de trabalho de longa execução. Este tópico pressupõe que você sabe como criar soluções e projetos do Visual Studio 2012.

## <a name="prerequisites"></a>Pré-requisitos
 Você deve ter o seguinte software instalado para usar este passo a passo:

1. Microsoft SQL Server 2008

2. Visual Studio 2012

3. Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]

4. Você está familiarizado com o WCF e o Visual Studio 2012 e sabe como criar projetos/soluções.

### <a name="to-setup-the-sql-database"></a>Para configurar o banco de dados SQL

1. Para instâncias de serviço de fluxo de trabalho a serem persistidos que você deve ter o Microsoft SQL Server instalado e você deve configurar um banco de dados para armazenar as instâncias de fluxo de trabalho persistida. Execute o Microsoft SQL Management Studio clicando o **inicie** botão, selecionando **todos os programas**, **Microsoft SQL Server 2008**, e **Microsoft SQL Management Studio**.

2. Clique o **Connect** botão para fazer logon na instância do SQL Server

3. Clique com botão direito **bancos de dados** no modo de exibição de árvore e selecione **novo banco de dados...** para criar um novo banco de dados chamado `SQLPersistenceStore`.

4. Execute o arquivo de script Sqlworkflowinstancestoreschema localizado no diretório C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en no banco de dados SQLPersistenceStore para configurar os esquemas de banco de dados necessários.

5. Execute o arquivo de script de Sqlworkflowinstancestorelogic localizado no diretório C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en no banco de dados SQLPersistenceStore para configurar a lógica de banco de dados necessários.

### <a name="to-create-the-web-hosted-workflow-service"></a>Para criar a Web hospedado no serviço de fluxo de trabalho

1. Crie uma solução vazia do Visual Studio 2012, nomeie- `OrderProcessing`.

2. Adicionar um novo projeto de aplicativo de serviço de fluxo de trabalho WCF chamado `OrderService` à solução.

3. Na caixa de diálogo de propriedades da projeto, selecione a **Web** guia.

    1. Sob **iniciar ação** selecionar **página específica** e especifique `Service1.xamlx`.

         ![Propriedades de Web de projeto de serviço de fluxo de trabalho](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "criar o serviço de fluxo de trabalho hospedado na web - opção de página específica")

    2. Sob **servidores** selecionar **servidor Web do IIS Local Use**.

         ![Configurações do servidor Web local](./media/creating-a-long-running-workflow-service/use-local-web-server.png "criar o serviço de fluxo de trabalho hospedado na web - opção de usar o servidor de Web do IIS Local")

        > [!WARNING]
        >  Você deve executar o Visual Studio 2012 no modo administrador para fazer essa configuração.

         Essas duas etapas configuram o projeto de serviço de fluxo de trabalho seja hospedado pelo IIS.

4. Abra `Service1.xamlx` se ele estiver não abrir já e exclua o existente **ReceiveRequest** e **SendResponse** atividades.

5. Selecione o **Sequential Service** atividade e clique no **variáveis** vincular e adicione as variáveis mostradas na ilustração a seguir. Isso adiciona algumas variáveis que serão usados posteriormente no serviço de fluxo de trabalho.

    > [!NOTE]
    >  Se o CorrelationHandle não estiver na lista suspensa tipo de variável, selecione **procurar tipos** na lista suspensa. Digite CorrelationHandle na **nome do tipo** selecione CorrelationHandle na caixa de listagem e clique em **Okey**.

     ![Adicione variáveis](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "adicionar variáveis à atividade Sequential Service.")

6. Arraste e solte uma **ReceiveAndSendReply** modelo de atividade para o **Sequential Service** atividade. Esse conjunto de atividades será receber uma mensagem de um cliente e enviar uma resposta de volta.

    1. Selecione o **Receive** atividade e defina as propriedades realçadas na ilustração a seguir.

         ![Definir propriedades de atividade receber](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "definir as propriedades de atividade de recebimento.")

         A propriedade DisplayName define o nome exibido para a atividade Receive no designer. As propriedades ServiceContractName e OperationName especificam o nome do contrato de serviço e operação são implementados pela atividade Receive. Para obter mais informações sobre como os contratos são usados nos serviços de fluxo de trabalho, consulte [utilizando contratos no fluxo de trabalho](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).

    2. Clique o **defina...**  link na **ReceiveStartOrder** atividade e defina as propriedades mostradas na ilustração a seguir.  Observe que o **parâmetros** botão de opção é selecionado, um parâmetro denominado `p_customerName` está associado a `customerName` variável. Isso configura a **Receive** atividade receber alguns dados e associar dados a variáveis locais.

         ![Definindo os dados recebidos pela atividade Receive](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "definir as propriedades de dados recebidos pela atividade Receive.")

    3. Selecione o **SendReplyToReceive** atividade e defina a propriedade realçada mostrada na ilustração a seguir.

         ![Definindo as propriedades da atividade SendReply](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")

    4. Clique o **defina...**  link na **SendReplyToStartOrder** atividade e defina as propriedades mostradas na ilustração a seguir. Observe que o **parâmetros** botão de opção é selecionado; um parâmetro chamado `p_orderId` está associado a `orderId` variável. Essa configuração especifica que a atividade SendReplyToStartOrder retornará um valor de cadeia de caracteres de tipo para o chamador.

         ![Configurando os dados de conteúdo de atividade de SendReply](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "definir a configuração para a atividade de SetReplyToStartOrder.")

    5. Arrastar e soltar uma atividade de atribuição entre o **Receive** e **SendReply** atividades e defina as propriedades conforme mostrado na ilustração a seguir:

         ![Adicionar uma atividade assign](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "adicionar uma atividade de atribuição.")

         Isso cria uma nova ID de ordem e coloca o valor na variável orderId.

    6. Selecione o **ReplyToStartOrder** atividade. Na janela Propriedades, clique no botão de reticências para **CorrelationInitializers**. Selecione o **adicionar inicializador** link, digite `orderIdHandle` na caixa de texto de inicializador, selecione o inicializador de correlação de consulta para o tipo de correlação e selecione p_orderId sob a caixa de lista suspensa de consultas XPATH. Essas configurações são mostradas na ilustração a seguir. Clique em **OK**.  Isso inicializa uma correlação entre o cliente e essa instância do serviço de fluxo de trabalho. Quando uma mensagem que contém essa ordem de que ID é recebida, ela é roteada para esta instância do serviço de fluxo de trabalho.

         ![Adicionando um inicializador de correlação](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "adicionar um inicializador de correlação.")

7. Arraste e solte outra **ReceiveAndSendReply** atividade até o final do fluxo de trabalho (fora do **sequência** que contém o primeiro **Receive** e  **SendReply** atividades). Isso irá receber a segunda mensagem enviada pelo cliente e responder a ele.

    1. Selecione o **sequência** que contém o recém-adicionado **Receive** e **SendReply** atividades e clique no **variáveis** botão. Adicione a variável realçada na ilustração a seguir:

         ![Adicionando novas variáveis](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "adicionar a variável de ItemId.")
         
         Também adicione `orderResult` como **cadeia de caracteres** no `Sequence` escopo.

    2. Selecione o **Receive** atividade e defina as propriedades mostradas na ilustração a seguir:

         ![Definir as propriedades de atividade de recebimento](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "definir as propriedades de atividades de recebimento.")
         
         > [!NOTE]
         >  Não se esqueça de alterar **ServiceContractName** campo com `../IAddItem`.

    3. Clique o **defina...**  link na **ReceiveAddItem** atividade e adicione os parâmetros mostrados na ilustração a seguir: Isso configura a atividade de recebimento para aceitar dois parâmetros, a ID da ordem e a ID do item que estão sendo ordenada.

         ![Especificando parâmetros para o segundo recebimento](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "configurar a atividade de recebimento para receber dois parâmetros.")

    4. Clique o **CorrelateOn** reticências e digitar `orderIdHandle`. Sob **consultas XPath**, clique na seta suspensa e selecione `p_orderId`. Isso configura a correlação na segunda atividade de recebimento. Para obter mais informações sobre a correlação, consulte [correlação](../../../../docs/framework/wcf/feature-details/correlation.md).

         ![Definindo a propriedade CorrelatesOn](./media/creating-a-long-running-workflow-service/correlateson-setting.png "defina a propriedade CorrelatesOn.")

    5. Arraste e solte uma **se** atividade imediatamente após o **ReceiveAddItem** atividade. Essa atividade atua como um se instrução.

        1. Defina as **condição** propriedade `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`

        2. Arrastar e soltar uma **atribuir** atividade para o **, em seguida,** seção e outro para o **Else** seção definir as propriedades do **atribuir** atividades, conforme mostrado na ilustração a seguir.

             ![Atribuir o resultado da chamada de serviço](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "atribuir o resultado da chamada de serviço.")

             Se a condição for `true` as **, em seguida,** seção será executada. Se a condição for `false` as **Else** seção será executada.

        3. Selecione o **SendReplyToReceive** atividade e conjunto de **DisplayName** propriedade mostrada na ilustração a seguir.

             ![Definindo as propriedades da atividade SendReply](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "defina a propriedade de atividade de SendReply.")

        4. Clique o **defina...**  link na **SetReplyToAddItem** atividade e configurá-lo, conforme mostrado na ilustração a seguir. Isso configura a **SendReplyToAddItem** atividade para retornar o valor de `orderResult` variável.

             ![Definindo a associação de dados para a atividade de SendReply](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "definir propriedade de atividade SendReplyToAddItem.")

8. Abra o arquivo Web. config e adicione os seguintes elementos no \<comportamento > seção para habilitar a persistência de fluxo de trabalho.

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    >  Certifique-se de substituir seu host e o nome da instância do SQL server no trecho de código anterior.

9. Compile a solução.

### <a name="to-create-a-client-application-to-call-the-workflow-service"></a>Para criar um aplicativo cliente para chamar o serviço de fluxo de trabalho

1. Adicionar um novo projeto de aplicativo de Console chamado `OrderClient` à solução.

2. Adicione referências aos assemblies a seguir para o `OrderClient` projeto

    1. System.ServiceModel.dll

    2. System.ServiceModel.Activities.dll

3. Adicionar uma referência de serviço para o serviço de fluxo de trabalho e especificar `OrderService` como o namespace.

4. No `Main()` método do projeto cliente adicione o seguinte código:

    ```
    static void Main(string[] args)
    {
       // Send initial message to start the workflow service
       Console.WriteLine("Sending start message");
       StartOrderClient startProxy = new StartOrderClient();
       string orderId = startProxy.StartOrder("Kim Abercrombie");

       // The workflow service is now waiting for the second message to be sent
       Console.WriteLine("Workflow service is idle...");
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");
       Console.ReadLine();

       // Send the second message
       Console.WriteLine("Sending add item message");
       AddItemClient addProxy = new AddItemClient();
       AddItem item = new AddItem();
       item.p_itemId = "Zune HD";
       item.p_orderId = orderId;

       string orderResult = addProxy.AddItem(item);
       Console.WriteLine("Service returned: " + orderResult);
    }
    ```

5. Compile a solução e executar o `OrderClient` aplicativo. O cliente exibirá o seguinte texto:

    ```Output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. Para verificar que o serviço de fluxo de trabalho tiver sido persistido, inicie o SQL Server Management Studio, vá para o **inicie** menu, selecionando **todos os programas**, **doMicrosoftSQLServer2008**, **SQL Server Management Studio**.

    1. No painel esquerdo, expanda, **bancos de dados**, **SQLPersistenceStore**, **modos de exibição** e clique com botão direito **System.Activities.DurableInstancing.Instances**  e selecione **selecionar 1000 linhas superiores**. No **resultados** painel, verifique se você ver pelo menos uma instância listada. Pode haver outras instâncias de execuções anteriores se ocorreu uma exceção durante a execução. Você pode excluir linhas existentes, clicando com o botão direito **System.Activities.DurableInstancing.Instances** e selecionando **Editar Top 200 linhas**, pressione a **Execute** botão, Selecionar todas as linhas no painel de resultados e selecionando **excluir**.  Para verificar a instância exibida no banco de dados a instância do seu aplicativo é criado, verifique se a exibição de instâncias está vazia antes de executar o cliente. Depois que o cliente está em execução de executar novamente a consulta (Selecionar 1000 linhas superiores) e verifique se foi adicionada uma nova instância.

7. Pressione enter para enviar a mensagem do item Adicionar para o serviço de fluxo de trabalho. O cliente exibirá o seguinte texto:

    ```Output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a>Consulte também

- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
