---
title: "Criando um serviço de fluxo de trabalho de execução longa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f4204de8c113c2ff553afec934b68f0beeb89580
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-long-running-workflow-service"></a>Criando um serviço de fluxo de trabalho de execução longa
Este tópico descreve como criar um serviço de fluxo de trabalho de longa execução. Serviços de fluxo de trabalho de longa execução pode ser executada por longos períodos de tempo. Em algum momento o fluxo de trabalho pode ficar ocioso aguardando algumas informações adicionais. Quando isso ocorre o fluxo de trabalho para um banco de dados SQL é persistente e é removido da memória. Quando as informações adicionais se torna disponíveis a instância de fluxo de trabalho é carregada para a memória e continua executando.  Nesse cenário, você está implementando um sistema de pedidos muito simplificado.  O cliente envia uma mensagem inicial para o serviço de fluxo de trabalho para iniciar a ordem. Ele retorna uma ID de ordem para o cliente. Neste ponto o serviço de fluxo de trabalho está esperando por outra mensagem do cliente e entra no estado ocioso e é mantido para um banco de dados do SQL Server.  Quando o cliente envia a mensagem seguinte para solicitar um item, o serviço de fluxo de trabalho é carregado para a memória e termina de processar o pedido. No exemplo de código, ele retorna uma cadeia de caracteres informando que o item foi adicionado na ordem. O exemplo de código não deve ser um aplicativo do mundo real de tecnologia, mas em vez disso, um exemplo simple que ilustra os serviços de fluxo de trabalho de longa execução. Este tópico pressupõe que você sabe como criar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projetos e soluções.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você deve ter o seguinte software instalado para usar este passo a passo:  
  
1.  Microsoft SQL Server 2008  
  
2.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
3.  Microsoft[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
4.  Você está familiarizado com o WCF e [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] e sabe como criar projetos/soluções.  
  
### <a name="to-setup-the-sql-database"></a>Para configurar o banco de dados SQL  
  
1.  Para que instâncias de serviço de fluxo de trabalho para ser persistente, você deve ter o Microsoft SQL Server instalado e você deve configurar um banco de dados para armazenar as instâncias de fluxo de trabalho persistentes. Execute o Microsoft SQL Management Studio clicando o **iniciar** botão selecionando **todos os programas**, **Microsoft SQL Server 2008**, e **Microsoft SQL Management Studio**.  
  
2.  Clique o **conectar** botão para fazer logon na instância do SQL Server  
  
3.  Clique com botão direito **bancos de dados** no modo de exibição de árvore e selecione **novo banco de dados.** para criar um novo banco de dados chamado `SQLPersistenceStore`.  
  
4.  Execute o arquivo de script SqlWorkflowInstanceStoreSchema.sql localizado no diretório C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en no banco de dados SQLPersistenceStore para configurar os esquemas de banco de dados necessárias.  
  
5.  Execute o arquivo de script SqlWorkflowInstanceStoreLogic.sql localizado no diretório C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en no banco de dados SQLPersistenceStore para configurar a lógica de banco de dados necessárias.  
  
### <a name="to-create-the-web-hosted-workflow-service"></a>Para criar a Web hospedado no serviço de fluxo de trabalho  
  
1.  Criar um vazio [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] solução, nomeie-o `OrderProcessing`.  
  
2.  Adicionar um novo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projeto de aplicativo de serviço de fluxo de trabalho chamado `OrderService` à solução.  
  
3.  Na caixa de diálogo de propriedades da projeto, selecione o **Web** guia.  
  
    1.  Em **iniciar ação** selecione **página específica** e especifique `Service1.xamlx`.  
  
         ![Propriedades de Web do projeto de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")  
  
    2.  Em **servidores** selecione **servidor Web do IIS Local Use**.  
  
         ![Configurações do servidor Web local](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")  
  
        > [!WARNING]
        >  Você deve executar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] no modo de administrador para fazer essa configuração.  
  
         Essas duas etapas configuram o projeto de serviço de fluxo de trabalho para ser hospedado pelo IIS.  
  
4.  Abra `Service1.xamlx` se ele é aberto, não e exclua o existente **ReceiveRequest** e **SendResponse** atividades.  
  
5.  Selecione o **serviço sequencial** atividade e clique no **variáveis** link e adicionar as variáveis mostradas na ilustração a seguir. Isso adiciona algumas variáveis que serão usados posteriormente no serviço de fluxo de trabalho.  
  
    > [!NOTE]
    >  Se CorrelationHandle não estiver na lista suspensa tipo de variável, selecione **procurar tipos** na lista suspensa. Digite CorrelationHandle no **nome do tipo** selecione CorrelationHandle na caixa de listagem e clique em **Okey**.  
  
     ![Adicionar variáveis](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")  
  
6.  Arraste e solte um **ReceiveAndSendReply** modelo de atividade para o **serviço sequencial** atividade. Esse conjunto de atividades irá receber uma mensagem de um cliente e enviar uma resposta de volta.  
  
    1.  Selecione o **Receive** atividade e defina as propriedades realçadas na ilustração a seguir.  
  
         ![Conjunto de propriedades de atividade de recebimento](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")  
  
         A propriedade DisplayName define o nome exibido para a atividade de recebimento no designer. As propriedades ServiceContractName e OperationName especificam o nome do contrato de serviço e operação que são implementadas pela atividade de recebimento. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como os contratos são usados no fluxo de trabalho de serviços consulte [usando contratos no fluxo de trabalho](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  
  
    2.  Clique o **definir...**  link no **ReceiveStartOrder** atividade e defina as propriedades mostradas na ilustração a seguir.  Observe que o **parâmetros** botão de opção é selecionada, um parâmetro denominado `p_customerName` está associada ao `customerName` variável. Isso configura o **Receive** atividade receber alguns dados e associar dados a variáveis locais.  
  
         ![Definindo os dados recebidos pela atividade de recebimento](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")  
  
    3.  Selecione o **SendReplyToReceive** atividade e defina a propriedade realçada mostrada na ilustração a seguir.  
  
         ![Definindo as propriedades da atividade SendReply](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")  
  
    4.  Clique o **definir...**  link no **SendReplyToStartOrder** atividade e defina as propriedades mostradas na ilustração a seguir. Observe que o **parâmetros** botão de opção é selecionada; um parâmetro denominado `p_orderId` está associada ao `orderId` variável. Essa configuração especifica que a atividade SendReplyToStartOrder retornará um valor de cadeia de caracteres de tipo para o chamador.  
  
         ![Configurando os dados de conteúdo de atividade de SendReply](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")  
  
    5.  Arrastar e soltar uma atividade de atribuição entre o **Receive** e **SendReply** atividades e defina as propriedades conforme mostrado na ilustração a seguir:  
  
         ![Adicionar uma atividade atribuir](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")  
  
         Isso cria uma nova ID de ordem e coloca o valor na variável orderId.  
  
    6.  Selecione o **ReplyToStartOrder** atividade. Na janela Propriedades, clique no botão de reticências para **CorrelationInitializers**. Selecione o **adicionar inicializador** link, digite `orderIdHandle` na caixa de texto de inicializador, selecione o inicializador de correlação de consulta para o tipo de correlação e selecione p_orderId na caixa suspensa consultas XPATH. Essas configurações são mostradas na ilustração a seguir. Clique em **OK**.  Isso inicializa a correlação entre o cliente e esta instância do serviço de fluxo de trabalho. Quando uma mensagem que contém esta ordem de que ID é recebida, ela é roteada para esta instância do serviço de fluxo de trabalho.  
  
         ![Adicionando um inicializador de correlação](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")  
  
7.  Arrastar e soltar outra **ReceiveAndSendReply** atividade no final do fluxo de trabalho (fora de **sequência** que contém o primeiro **Receive** e  **SendReply** atividades). Isso receberá a segunda mensagem enviada pelo cliente e responder a ele.  
  
    1.  Selecione o **sequência** que contém o recém-adicionado **Receive** e **SendReply** atividades e clique no **variáveis** botão. Adicione a variável realçada na ilustração a seguir:  
  
         ![Adicionando novas variáveis](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")  
  
    2.  Selecione o **Receive** atividade e defina as propriedades mostradas na ilustração a seguir:  
  
         ![Definir as propriedades de atividade de recebimento](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")  
  
    3.  Clique o **definir...**  link no **ReceiveAddItem** atividade e adicione os parâmetros mostrados na ilustração a seguir: Isso configura a atividade de recebimento para aceitar dois parâmetros, a ID da ordem e a ID do item que estão sendo ordenada.  
  
         ![Especificar parâmetros para o segundo recebem](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")  
  
    4.  Clique o **CorrelateOn** reticências botão e digite `orderIdHandle`. Em **consultas XPath**, clique na seta suspensa e selecione `p_orderId`. Isso configura a correlação na segunda atividade de recebimento. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Consulte correlação [correlação](../../../../docs/framework/wcf/feature-details/correlation.md).  
  
         ![Definindo a propriedade CorrelatesOn](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")  
  
    5.  Arraste e solte um **se** atividade imediatamente após o **ReceiveAddItem** atividade. Essa atividade atua como um se instrução.  
  
        1.  Definir o **condição** propriedade`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`  
  
        2.  Arrastar e soltar um **atribuir** atividade para o **, em seguida,** seção e outro para o **Else** seção define as propriedades do **atribuir** atividades, conforme mostrado na ilustração a seguir.  
  
             ![Atribuindo o resultado da chamada de serviço](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")  
  
             Se a condição for `true` o **, em seguida,** seção será executada. Se a condição for `false` o **Else** seção será executada.  
  
        3.  Selecione o **SendReplyToReceive** atividade e defina o **DisplayName** propriedade mostrada na ilustração a seguir.  
  
             ![Definindo as propriedades de atividade de SendReply](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")  
  
        4.  Clique o **definir...**  link no **SetReplyToAddItem** atividade e configurá-lo, conforme mostrado na ilustração a seguir. Isso configura o **SendReplyToAddItem** atividade para retornar o valor de `orderResult` variável.  
  
             ![Definir a associação de dados para a atividade de SendReply](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")  
  
8.  Abra o arquivo Web. config e adicione os seguintes elementos de \<comportamento > seção para habilitar a persistência de fluxo de trabalho.  
  
    ```xml  
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />  
              <workflowIdle timeToUnload="0"/>  
    ```  
  
    > [!WARNING]
    >  Certifique-se de substituir seu host e o nome da instância do SQL server no trecho de código anterior.  
  
9. Compile a solução.  
  
### <a name="to-create-a-client-application-to-call-the-workflow-service"></a>Para criar um aplicativo cliente para chamar o serviço de fluxo de trabalho  
  
1.  Adicionar um novo projeto de aplicativo de Console chamado `OrderClient` à solução.  
  
2.  Adicione referências para os seguintes assemblies para o `OrderClient` projeto  
  
    1.  System.ServiceModel.dll  
  
    2.  System.ServiceModel.Activities.dll  
  
3.  Adicione uma referência de serviço para o serviço de fluxo de trabalho e especifique `OrderService` como o namespace.  
  
4.  No `Main()` método do projeto cliente adicione o seguinte código:  
  
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
  
5.  Compile a solução e executar o `OrderClient` aplicativo. O cliente exibirá o seguinte texto:  
  
    ```Output  
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...  
    ```  
  
6.  Para verificar se o serviço de fluxo de trabalho foram persistentes, iniciar o SQL Server Management Studio, vá para o **iniciar** menu, selecionando **todos os programas**, **doMicrosoftSQLServer2008**, **SQL Server Management Studio**.  
  
    1.  No painel esquerdo, expanda, **bancos de dados**, **SQLPersistenceStore**, **exibições** botão direito do mouse **System.Activities.DurableInstancing.Instances**  e selecione **selecionar 1000 linhas superiores**. No **resultados** painel Verifique se houver pelo menos uma instância listada. Pode haver outras instâncias de execuções anteriores se ocorreu uma exceção durante a execução. Você pode excluir linhas existentes, clicando com o botão direito em **System.Activities.DurableInstancing.Instances** e selecionando **Editar Top 200 linhas**, pressione a **Execute** botão Selecionar todas as linhas no painel de resultados e selecionando **excluir**.  Para verificar a instância exibida no banco de dados é a instância do seu aplicativo criado, verifique se o modo de exibição de instâncias está vazio antes de executar o cliente. Depois que o cliente está em execução novamente executar a consulta (Selecionar 1000 linhas superiores) e verifique se foi adicionada uma nova instância.  
  
7.  Pressione enter para enviar a mensagem do item add para o serviço de fluxo de trabalho. O cliente exibirá o seguinte texto:  
  
    ```Output  
    Sending add item messageService returned: Item added to orderPress any key to continue . . .  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
