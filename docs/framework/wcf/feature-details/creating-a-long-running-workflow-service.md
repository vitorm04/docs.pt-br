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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 94a62a54fb138e394d8e9fa944e49e6526ae7152
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-long-running-workflow-service"></a><span data-ttu-id="fa96e-102">Criando um serviço de fluxo de trabalho de execução longa</span><span class="sxs-lookup"><span data-stu-id="fa96e-102">Creating a Long-running Workflow Service</span></span>
<span data-ttu-id="fa96e-103">Este tópico descreve como criar um serviço de fluxo de trabalho de longa execução.</span><span class="sxs-lookup"><span data-stu-id="fa96e-103">This topic describes how to create a long-running workflow service.</span></span> <span data-ttu-id="fa96e-104">Serviços de fluxo de trabalho de longa execução pode ser executada por longos períodos de tempo.</span><span class="sxs-lookup"><span data-stu-id="fa96e-104">Long running workflow services may run for long periods of time.</span></span> <span data-ttu-id="fa96e-105">Em algum momento o fluxo de trabalho pode ficar ocioso aguardando algumas informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="fa96e-105">At some point the workflow may go idle waiting for some additional information.</span></span> <span data-ttu-id="fa96e-106">Quando isso ocorre o fluxo de trabalho para um banco de dados SQL é persistente e é removido da memória.</span><span class="sxs-lookup"><span data-stu-id="fa96e-106">When this occurs the workflow is persisted to a SQL database and is removed from memory.</span></span> <span data-ttu-id="fa96e-107">Quando as informações adicionais se torna disponíveis a instância de fluxo de trabalho é carregada para a memória e continua executando.</span><span class="sxs-lookup"><span data-stu-id="fa96e-107">When the additional information becomes available the workflow instance is loaded back into memory and continues executing.</span></span>  <span data-ttu-id="fa96e-108">Nesse cenário, você está implementando um sistema de pedidos muito simplificado.</span><span class="sxs-lookup"><span data-stu-id="fa96e-108">In this scenario you are implementing a very simplified ordering system.</span></span>  <span data-ttu-id="fa96e-109">O cliente envia uma mensagem inicial para o serviço de fluxo de trabalho para iniciar a ordem.</span><span class="sxs-lookup"><span data-stu-id="fa96e-109">The client sends an initial message to the workflow service to start the order.</span></span> <span data-ttu-id="fa96e-110">Ele retorna uma ID de ordem para o cliente.</span><span class="sxs-lookup"><span data-stu-id="fa96e-110">It returns an order ID to the client.</span></span> <span data-ttu-id="fa96e-111">Neste ponto o serviço de fluxo de trabalho está esperando por outra mensagem do cliente e entra no estado ocioso e é mantido para um banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fa96e-111">At this point the workflow service is waiting for another message from the client and goes into the idle state and is persisted to a SQL Server database.</span></span>  <span data-ttu-id="fa96e-112">Quando o cliente envia a mensagem seguinte para solicitar um item, o serviço de fluxo de trabalho é carregado para a memória e termina de processar o pedido.</span><span class="sxs-lookup"><span data-stu-id="fa96e-112">When the client sends the next message to order an item, the workflow service is loaded back into memory and finishes processing the order.</span></span> <span data-ttu-id="fa96e-113">No exemplo de código, ele retorna uma cadeia de caracteres informando que o item foi adicionado na ordem.</span><span class="sxs-lookup"><span data-stu-id="fa96e-113">In the code sample it returns a string stating the item has been added to the order.</span></span> <span data-ttu-id="fa96e-114">O exemplo de código não deve ser um aplicativo do mundo real de tecnologia, mas em vez disso, um exemplo simple que ilustra os serviços de fluxo de trabalho de longa execução.</span><span class="sxs-lookup"><span data-stu-id="fa96e-114">The code sample is not meant to be a real world application of the technology, but rather a simple sample that illustrates long running workflow services.</span></span> <span data-ttu-id="fa96e-115">Este tópico pressupõe que você sabe como criar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projetos e soluções.</span><span class="sxs-lookup"><span data-stu-id="fa96e-115">This topic assumes you know how to create [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projects and solutions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fa96e-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fa96e-116">Prerequisites</span></span>  
 <span data-ttu-id="fa96e-117">Você deve ter o seguinte software instalado para usar este passo a passo:</span><span class="sxs-lookup"><span data-stu-id="fa96e-117">You must have the following software installed to use this walkthrough:</span></span>  
  
1.  <span data-ttu-id="fa96e-118">Microsoft SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="fa96e-118">Microsoft SQL Server 2008</span></span>  
  
2.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
3.  <span data-ttu-id="fa96e-119">Microsoft[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa96e-119">Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span></span>  
  
4.  <span data-ttu-id="fa96e-120">Você está familiarizado com o WCF e [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] e sabe como criar projetos/soluções.</span><span class="sxs-lookup"><span data-stu-id="fa96e-120">You are familiar with WCF and [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and know how to create projects/solutions.</span></span>  
  
### <a name="to-setup-the-sql-database"></a><span data-ttu-id="fa96e-121">Para configurar o banco de dados SQL</span><span class="sxs-lookup"><span data-stu-id="fa96e-121">To Setup the SQL Database</span></span>  
  
1.  <span data-ttu-id="fa96e-122">Para que instâncias de serviço de fluxo de trabalho para ser persistente, você deve ter o Microsoft SQL Server instalado e você deve configurar um banco de dados para armazenar as instâncias de fluxo de trabalho persistentes.</span><span class="sxs-lookup"><span data-stu-id="fa96e-122">In order for workflow service instances to be persisted you must have Microsoft SQL Server installed and you must configure a database to store the persisted workflow instances.</span></span> <span data-ttu-id="fa96e-123">Execute o Microsoft SQL Management Studio clicando o **iniciar** botão selecionando **todos os programas**, **Microsoft SQL Server 2008**, e **Microsoft SQL Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="fa96e-123">Run Microsoft SQL Management Studio by clicking the **Start** button, selecting **All Programs**, **Microsoft SQL Server 2008**, and **Microsoft SQL Management Studio**.</span></span>  
  
2.  <span data-ttu-id="fa96e-124">Clique o **conectar** botão para fazer logon na instância do SQL Server</span><span class="sxs-lookup"><span data-stu-id="fa96e-124">Click the **Connect** button to log on to the SQL Server instance</span></span>  
  
3.  <span data-ttu-id="fa96e-125">Clique com botão direito **bancos de dados** no modo de exibição de árvore e selecione **novo banco de dados.**</span><span class="sxs-lookup"><span data-stu-id="fa96e-125">Right click **Databases** in the tree view and select **New Database..**</span></span> <span data-ttu-id="fa96e-126">para criar um novo banco de dados chamado `SQLPersistenceStore`.</span><span class="sxs-lookup"><span data-stu-id="fa96e-126">to create a new database called `SQLPersistenceStore`.</span></span>  
  
4.  <span data-ttu-id="fa96e-127">Execute o arquivo de script SqlWorkflowInstanceStoreSchema.sql localizado no diretório C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en no banco de dados SQLPersistenceStore para configurar os esquemas de banco de dados necessárias.</span><span class="sxs-lookup"><span data-stu-id="fa96e-127">Run the SqlWorkflowInstanceStoreSchema.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database schemas.</span></span>  
  
5.  <span data-ttu-id="fa96e-128">Execute o arquivo de script SqlWorkflowInstanceStoreLogic.sql localizado no diretório C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en no banco de dados SQLPersistenceStore para configurar a lógica de banco de dados necessárias.</span><span class="sxs-lookup"><span data-stu-id="fa96e-128">Run the SqlWorkflowInstanceStoreLogic.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database logic.</span></span>  
  
### <a name="to-create-the-web-hosted-workflow-service"></a><span data-ttu-id="fa96e-129">Para criar a Web hospedado no serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="fa96e-129">To Create the Web Hosted Workflow Service</span></span>  
  
1.  <span data-ttu-id="fa96e-130">Criar um vazio [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] solução, nomeie-o `OrderProcessing`.</span><span class="sxs-lookup"><span data-stu-id="fa96e-130">Create an empty [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] solution, name it `OrderProcessing`.</span></span>  
  
2.  <span data-ttu-id="fa96e-131">Adicionar um novo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projeto de aplicativo de serviço de fluxo de trabalho chamado `OrderService` à solução.</span><span class="sxs-lookup"><span data-stu-id="fa96e-131">Add a new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Workflow Service Application project called `OrderService` to the solution.</span></span>  
  
3.  <span data-ttu-id="fa96e-132">Na caixa de diálogo de propriedades da projeto, selecione o **Web** guia.</span><span class="sxs-lookup"><span data-stu-id="fa96e-132">In the project properties dialog, select the **Web** tab.</span></span>  
  
    1.  <span data-ttu-id="fa96e-133">Em **iniciar ação** selecione **página específica** e especifique `Service1.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="fa96e-133">Under **Start Action** select **Specific Page** and specify `Service1.xamlx`.</span></span>  
  
         <span data-ttu-id="fa96e-134">![Propriedades de Web do projeto de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")</span><span class="sxs-lookup"><span data-stu-id="fa96e-134">![Workflow Service Project Web Properties](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")</span></span>  
  
    2.  <span data-ttu-id="fa96e-135">Em **servidores** selecione **servidor Web do IIS Local Use**.</span><span class="sxs-lookup"><span data-stu-id="fa96e-135">Under **Servers** select **Use Local IIS Web server**.</span></span>  
  
         <span data-ttu-id="fa96e-136">![Configurações do servidor Web local](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")</span><span class="sxs-lookup"><span data-stu-id="fa96e-136">![Local Web Server Settings](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")</span></span>  
  
        > [!WARNING]
        >  <span data-ttu-id="fa96e-137">Você deve executar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] no modo de administrador para fazer essa configuração.</span><span class="sxs-lookup"><span data-stu-id="fa96e-137">You must run [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] in administrator mode to make this setting.</span></span>  
  
         <span data-ttu-id="fa96e-138">Essas duas etapas configuram o projeto de serviço de fluxo de trabalho para ser hospedado pelo IIS.</span><span class="sxs-lookup"><span data-stu-id="fa96e-138">These two steps configure the workflow service project to be hosted by IIS.</span></span>  
  
4.  <span data-ttu-id="fa96e-139">Abra `Service1.xamlx` se ele é aberto, não e exclua o existente **ReceiveRequest** e **SendResponse** atividades.</span><span class="sxs-lookup"><span data-stu-id="fa96e-139">Open `Service1.xamlx` if it is not open already and delete the existing **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
5.  <span data-ttu-id="fa96e-140">Selecione o **serviço sequencial** atividade e clique no **variáveis** link e adicionar as variáveis mostradas na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa96e-140">Select the **Sequential Service** activity and click the **Variables** link and add the variables shown in the following illustration.</span></span> <span data-ttu-id="fa96e-141">Isso adiciona algumas variáveis que serão usados posteriormente no serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fa96e-141">Doing this adds some variables that will be used later on in the workflow service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fa96e-142">Se CorrelationHandle não estiver na lista suspensa tipo de variável, selecione **procurar tipos** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="fa96e-142">If CorrelationHandle is not in the Variable Type drop-down, select **Browse for types** from the drop-down.</span></span> <span data-ttu-id="fa96e-143">Digite CorrelationHandle no **nome do tipo** selecione CorrelationHandle na caixa de listagem e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="fa96e-143">Type CorrelationHandle in the **Type name** box, select CorrelationHandle from the listbox and click **OK**.</span></span>  
  
     <span data-ttu-id="fa96e-144">![Adicionar variáveis](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")</span><span class="sxs-lookup"><span data-stu-id="fa96e-144">![Add Variables](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")</span></span>  
  
6.  <span data-ttu-id="fa96e-145">Arraste e solte um **ReceiveAndSendReply** modelo de atividade para o **serviço sequencial** atividade.</span><span class="sxs-lookup"><span data-stu-id="fa96e-145">Drag and drop a **ReceiveAndSendReply** activity template into the **Sequential Service** activity.</span></span> <span data-ttu-id="fa96e-146">Esse conjunto de atividades irá receber uma mensagem de um cliente e enviar uma resposta de volta.</span><span class="sxs-lookup"><span data-stu-id="fa96e-146">This set of activities will receive a message from a client and send a reply back.</span></span>  
  
    1.  <span data-ttu-id="fa96e-147">Selecione o **Receive** atividade e defina as propriedades realçadas na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa96e-147">Select the **Receive** activity and set the properties highlighted in the following illustration.</span></span>  
  
         <span data-ttu-id="fa96e-148">![Conjunto de propriedades de atividade de recebimento](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")</span><span class="sxs-lookup"><span data-stu-id="fa96e-148">![Set Receive Activity Properties](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")</span></span>  
  
         <span data-ttu-id="fa96e-149">A propriedade DisplayName define o nome exibido para a atividade de recebimento no designer.</span><span class="sxs-lookup"><span data-stu-id="fa96e-149">The DisplayName property sets the name displayed for the Receive activity in the designer.</span></span> <span data-ttu-id="fa96e-150">As propriedades ServiceContractName e OperationName especificam o nome do contrato de serviço e operação que são implementadas pela atividade de recebimento.</span><span class="sxs-lookup"><span data-stu-id="fa96e-150">The ServiceContractName and OperationName properties specify the name of the service contract and operation that are implemented by the Receive activity.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fa96e-151">como os contratos são usados no fluxo de trabalho de serviços consulte [usando contratos no fluxo de trabalho](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="fa96e-151"> how contracts are used in Workflow services see [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  
  
    2.  <span data-ttu-id="fa96e-152">Clique o **definir...**  link no **ReceiveStartOrder** atividade e defina as propriedades mostradas na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa96e-152">Click the **Define...** link in the **ReceiveStartOrder** activity and set the properties shown in the following illustration.</span></span>  <span data-ttu-id="fa96e-153">Observe que o **parâmetros** botão de opção é selecionada, um parâmetro denominado `p_customerName` está associada ao `customerName` variável.</span><span class="sxs-lookup"><span data-stu-id="fa96e-153">Notice that the **Parameters** radio button is selected, a parameter named `p_customerName` is bound to the `customerName` variable.</span></span> <span data-ttu-id="fa96e-154">Isso configura o **Receive** atividade receber alguns dados e associar dados a variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="fa96e-154">This configures the **Receive** activity to receive some data and bind that data to local variables.</span></span>  
  
         <span data-ttu-id="fa96e-155">![Definindo os dados recebidos pela atividade de recebimento](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")</span><span class="sxs-lookup"><span data-stu-id="fa96e-155">![Setting the data received by the Receive activity](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")</span></span>  
  
    3.  <span data-ttu-id="fa96e-156">Selecione o **SendReplyToReceive** atividade e defina a propriedade realçada mostrada na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa96e-156">Select The **SendReplyToReceive** activity and set the highlighted property shown in the following illustration.</span></span>  
  
         <span data-ttu-id="fa96e-157">![Definindo as propriedades da atividade SendReply](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")</span><span class="sxs-lookup"><span data-stu-id="fa96e-157">![Setting the properties of the SendReply activity](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")</span></span>  
  
    4.  <span data-ttu-id="fa96e-158">Clique o **definir...**  link no **SendReplyToStartOrder** atividade e defina as propriedades mostradas na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa96e-158">Click the **Define...** link in the **SendReplyToStartOrder** activity and set the properties shown in the following illustration.</span></span> <span data-ttu-id="fa96e-159">Observe que o **parâmetros** botão de opção é selecionada; um parâmetro denominado `p_orderId` está associada ao `orderId` variável.</span><span class="sxs-lookup"><span data-stu-id="fa96e-159">Notice that the **Parameters** radio button is selected; a parameter named `p_orderId` is bound to the `orderId` variable.</span></span> <span data-ttu-id="fa96e-160">Essa configuração especifica que a atividade SendReplyToStartOrder retornará um valor de cadeia de caracteres de tipo para o chamador.</span><span class="sxs-lookup"><span data-stu-id="fa96e-160">This setting specifies that the SendReplyToStartOrder activity will return a value of type string to the caller.</span></span>  
  
         <span data-ttu-id="fa96e-161">![Configurando os dados de conteúdo de atividade de SendReply](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")</span><span class="sxs-lookup"><span data-stu-id="fa96e-161">![Configuring the SendReply activity content data](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")</span></span>  
  
    5.  <span data-ttu-id="fa96e-162">Arrastar e soltar uma atividade de atribuição entre o **Receive** e **SendReply** atividades e defina as propriedades conforme mostrado na ilustração a seguir:</span><span class="sxs-lookup"><span data-stu-id="fa96e-162">Drag and drop an Assign activity in between the **Receive** and **SendReply** activities and set the properties as shown in the following illustration:</span></span>  
  
         <span data-ttu-id="fa96e-163">![Adicionar uma atividade atribuir](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")</span><span class="sxs-lookup"><span data-stu-id="fa96e-163">![Adding an assign activity](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")</span></span>  
  
         <span data-ttu-id="fa96e-164">Isso cria uma nova ID de ordem e coloca o valor na variável orderId.</span><span class="sxs-lookup"><span data-stu-id="fa96e-164">This creates a new order ID and places the value in the orderId variable.</span></span>  
  
    6.  <span data-ttu-id="fa96e-165">Selecione o **ReplyToStartOrder** atividade.</span><span class="sxs-lookup"><span data-stu-id="fa96e-165">Select the **ReplyToStartOrder** activity.</span></span> <span data-ttu-id="fa96e-166">Na janela Propriedades, clique no botão de reticências para **CorrelationInitializers**.</span><span class="sxs-lookup"><span data-stu-id="fa96e-166">In the properties window click the ellipsis button for **CorrelationInitializers**.</span></span> <span data-ttu-id="fa96e-167">Selecione o **adicionar inicializador** link, digite `orderIdHandle` na caixa de texto de inicializador, selecione o inicializador de correlação de consulta para o tipo de correlação e selecione p_orderId na caixa suspensa consultas XPATH.</span><span class="sxs-lookup"><span data-stu-id="fa96e-167">Select the **Add initializer** link, enter `orderIdHandle` in the Initializer text box, select Query correlation initializer for the Correlation type, and select p_orderId under the XPATH Queries dropdown box.</span></span> <span data-ttu-id="fa96e-168">Essas configurações são mostradas na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa96e-168">These settings are shown in the following illustration.</span></span> <span data-ttu-id="fa96e-169">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="fa96e-169">Click **OK**.</span></span>  <span data-ttu-id="fa96e-170">Isso inicializa a correlação entre o cliente e esta instância do serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fa96e-170">This initializes a correlation between the client and this instance of the workflow service.</span></span> <span data-ttu-id="fa96e-171">Quando uma mensagem que contém esta ordem de que ID é recebida, ela é roteada para esta instância do serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fa96e-171">When a message containing this order ID is received it is routed to this instance of the workflow service.</span></span>  
  
         <span data-ttu-id="fa96e-172">![Adicionando um inicializador de correlação](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")</span><span class="sxs-lookup"><span data-stu-id="fa96e-172">![Adding a correlation initializer](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")</span></span>  
  
7.  <span data-ttu-id="fa96e-173">Arrastar e soltar outra **ReceiveAndSendReply** atividade no final do fluxo de trabalho (fora de **sequência** que contém o primeiro **Receive** e  **SendReply** atividades).</span><span class="sxs-lookup"><span data-stu-id="fa96e-173">Drag and drop another **ReceiveAndSendReply** activity to the end of the workflow (outside the **Sequence** containing the first **Receive** and **SendReply** activities).</span></span> <span data-ttu-id="fa96e-174">Isso receberá a segunda mensagem enviada pelo cliente e responder a ele.</span><span class="sxs-lookup"><span data-stu-id="fa96e-174">This will receive the second message sent by the client and respond to it.</span></span>  
  
    1.  <span data-ttu-id="fa96e-175">Selecione o **sequência** que contém o recém-adicionado **Receive** e **SendReply** atividades e clique no **variáveis** botão.</span><span class="sxs-lookup"><span data-stu-id="fa96e-175">Select the **Sequence** that contains the newly added **Receive** and **SendReply** activities and click the **Variables** button.</span></span> <span data-ttu-id="fa96e-176">Adicione a variável realçada na ilustração a seguir:</span><span class="sxs-lookup"><span data-stu-id="fa96e-176">Add the variable highlighted in the following illustration:</span></span>  
  
         <span data-ttu-id="fa96e-177">![Adicionando novas variáveis](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")</span><span class="sxs-lookup"><span data-stu-id="fa96e-177">![Adding new variables](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")</span></span>  
  
    2.  <span data-ttu-id="fa96e-178">Selecione o **Receive** atividade e defina as propriedades mostradas na ilustração a seguir:</span><span class="sxs-lookup"><span data-stu-id="fa96e-178">Select the **Receive** activity and set the properties shown in the following illustration:</span></span>  
  
         <span data-ttu-id="fa96e-179">![Definir as propriedades de atividade de recebimento](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")</span><span class="sxs-lookup"><span data-stu-id="fa96e-179">![Set the Receive acitivity properties](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")</span></span>  
  
    3.  <span data-ttu-id="fa96e-180">Clique o **definir...**  link no **ReceiveAddItem** atividade e adicione os parâmetros mostrados na ilustração a seguir: Isso configura a atividade de recebimento para aceitar dois parâmetros, a ID da ordem e a ID do item que estão sendo ordenada.</span><span class="sxs-lookup"><span data-stu-id="fa96e-180">Click the **Define...** link in the **ReceiveAddItem** activity and add the parameters shown in the following illustration:This configures the receive activity to accept two parameters, the order ID and the ID of the item being ordered.</span></span>  
  
         <span data-ttu-id="fa96e-181">![Especificar parâmetros para o segundo recebem](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")</span><span class="sxs-lookup"><span data-stu-id="fa96e-181">![Specifying parameters for the second receive](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")</span></span>  
  
    4.  <span data-ttu-id="fa96e-182">Clique o **CorrelateOn** reticências botão e digite `orderIdHandle`.</span><span class="sxs-lookup"><span data-stu-id="fa96e-182">Click the **CorrelateOn** ellipsis button and enter `orderIdHandle`.</span></span> <span data-ttu-id="fa96e-183">Em **consultas XPath**, clique na seta suspensa e selecione `p_orderId`.</span><span class="sxs-lookup"><span data-stu-id="fa96e-183">Under **XPath Queries**, click the drop down arrow and select `p_orderId`.</span></span> <span data-ttu-id="fa96e-184">Isso configura a correlação na segunda atividade de recebimento.</span><span class="sxs-lookup"><span data-stu-id="fa96e-184">This configures the correlation on the second receive activity.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fa96e-185">Consulte correlação [correlação](../../../../docs/framework/wcf/feature-details/correlation.md).</span><span class="sxs-lookup"><span data-stu-id="fa96e-185"> correlation see [Correlation](../../../../docs/framework/wcf/feature-details/correlation.md).</span></span>  
  
         <span data-ttu-id="fa96e-186">![Definindo a propriedade CorrelatesOn](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")</span><span class="sxs-lookup"><span data-stu-id="fa96e-186">![Setting the CorrelatesOn property](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")</span></span>  
  
    5.  <span data-ttu-id="fa96e-187">Arraste e solte um **se** atividade imediatamente após o **ReceiveAddItem** atividade.</span><span class="sxs-lookup"><span data-stu-id="fa96e-187">Drag and drop an **If** activity immediately after the **ReceiveAddItem** activity.</span></span> <span data-ttu-id="fa96e-188">Essa atividade atua como um se instrução.</span><span class="sxs-lookup"><span data-stu-id="fa96e-188">This activity acts just like an if statement.</span></span>  
  
        1.  <span data-ttu-id="fa96e-189">Definir o **condição** propriedade`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span><span class="sxs-lookup"><span data-stu-id="fa96e-189">Set the **Condition** property to `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span></span>  
  
        2.  <span data-ttu-id="fa96e-190">Arrastar e soltar um **atribuir** atividade para o **, em seguida,** seção e outro para o **Else** seção define as propriedades do **atribuir** atividades, conforme mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa96e-190">Drag and drop an **Assign** activity in to the **Then** section and another into the **Else** section set the properties of the **Assign** activities as shown in the following illustration.</span></span>  
  
             <span data-ttu-id="fa96e-191">![Atribuindo o resultado da chamada de serviço](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")</span><span class="sxs-lookup"><span data-stu-id="fa96e-191">![Assigning the result of the service call](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")</span></span>  
  
             <span data-ttu-id="fa96e-192">Se a condição for `true` o **, em seguida,** seção será executada.</span><span class="sxs-lookup"><span data-stu-id="fa96e-192">If the condition is `true` the **Then** section will be executed.</span></span> <span data-ttu-id="fa96e-193">Se a condição for `false` o **Else** seção será executada.</span><span class="sxs-lookup"><span data-stu-id="fa96e-193">If the condition is `false` the **Else** section is executed.</span></span>  
  
        3.  <span data-ttu-id="fa96e-194">Selecione o **SendReplyToReceive** atividade e defina o **DisplayName** propriedade mostrada na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa96e-194">Select the **SendReplyToReceive** activity and set the **DisplayName** property shown in the following illustration.</span></span>  
  
             <span data-ttu-id="fa96e-195">![Definindo as propriedades de atividade de SendReply](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")</span><span class="sxs-lookup"><span data-stu-id="fa96e-195">![Setting the SendReply activity properties](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")</span></span>  
  
        4.  <span data-ttu-id="fa96e-196">Clique o **definir...**  link no **SetReplyToAddItem** atividade e configurá-lo, conforme mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa96e-196">Click the **Define ...** link in the **SetReplyToAddItem** activity and configure it as shown in the following illustration.</span></span> <span data-ttu-id="fa96e-197">Isso configura o **SendReplyToAddItem** atividade para retornar o valor de `orderResult` variável.</span><span class="sxs-lookup"><span data-stu-id="fa96e-197">This configures the **SendReplyToAddItem** activity to return the value in the `orderResult` variable.</span></span>  
  
             <span data-ttu-id="fa96e-198">![Definir a associação de dados para a atividade de SendReply](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")</span><span class="sxs-lookup"><span data-stu-id="fa96e-198">![Setting the data binding for the SendReply activit](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")</span></span>  
  
8.  <span data-ttu-id="fa96e-199">Abra o arquivo Web. config e adicione os seguintes elementos de \<comportamento > seção para habilitar a persistência de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fa96e-199">Open the web.config file and add the following elements in the \<behavior> section to enable workflow persistence.</span></span>  
  
    ```xml  
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />  
              <workflowIdle timeToUnload="0"/>  
    ```  
  
    > [!WARNING]
    >  <span data-ttu-id="fa96e-200">Certifique-se de substituir seu host e o nome da instância do SQL server no trecho de código anterior.</span><span class="sxs-lookup"><span data-stu-id="fa96e-200">Make sure to replace your host and SQL server instance name in the previous code snippet.</span></span>  
  
9. <span data-ttu-id="fa96e-201">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="fa96e-201">Build the solution.</span></span>  
  
### <a name="to-create-a-client-application-to-call-the-workflow-service"></a><span data-ttu-id="fa96e-202">Para criar um aplicativo cliente para chamar o serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="fa96e-202">To Create a Client Application to Call the Workflow Service</span></span>  
  
1.  <span data-ttu-id="fa96e-203">Adicionar um novo projeto de aplicativo de Console chamado `OrderClient` à solução.</span><span class="sxs-lookup"><span data-stu-id="fa96e-203">Add a new Console application project called `OrderClient` to the solution.</span></span>  
  
2.  <span data-ttu-id="fa96e-204">Adicione referências para os seguintes assemblies para o `OrderClient` projeto</span><span class="sxs-lookup"><span data-stu-id="fa96e-204">Add references to the following assemblies to the `OrderClient` project</span></span>  
  
    1.  <span data-ttu-id="fa96e-205">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="fa96e-205">System.ServiceModel.dll</span></span>  
  
    2.  <span data-ttu-id="fa96e-206">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="fa96e-206">System.ServiceModel.Activities.dll</span></span>  
  
3.  <span data-ttu-id="fa96e-207">Adicione uma referência de serviço para o serviço de fluxo de trabalho e especifique `OrderService` como o namespace.</span><span class="sxs-lookup"><span data-stu-id="fa96e-207">Add a service reference to the workflow service and specify `OrderService` as the namespace.</span></span>  
  
4.  <span data-ttu-id="fa96e-208">No `Main()` método do projeto cliente adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="fa96e-208">In the `Main()` method of the client project add the following code:</span></span>  
  
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
  
5.  <span data-ttu-id="fa96e-209">Compile a solução e executar o `OrderClient` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa96e-209">Build the solution and run the `OrderClient` application.</span></span> <span data-ttu-id="fa96e-210">O cliente exibirá o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="fa96e-210">The client will display the following text:</span></span>  
  
    ```Output  
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...  
    ```  
  
6.  <span data-ttu-id="fa96e-211">Para verificar se o serviço de fluxo de trabalho foram persistentes, iniciar o SQL Server Management Studio, vá para o **iniciar** menu, selecionando **todos os programas**, **doMicrosoftSQLServer2008**, **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="fa96e-211">To verify that the workflow service has been persisted, start the SQL Server Management Studio by going to the **Start** menu, Selecting **All Programs**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.</span></span>  
  
    1.  <span data-ttu-id="fa96e-212">No painel esquerdo, expanda, **bancos de dados**, **SQLPersistenceStore**, **exibições** botão direito do mouse **System.Activities.DurableInstancing.Instances**  e selecione **selecionar 1000 linhas superiores**.</span><span class="sxs-lookup"><span data-stu-id="fa96e-212">In the left hand pane expand, **Databases**, **SQLPersistenceStore**, **Views** and right click **System.Activities.DurableInstancing.Instances** and select **Select Top 1000 Rows**.</span></span> <span data-ttu-id="fa96e-213">No **resultados** painel Verifique se houver pelo menos uma instância listada.</span><span class="sxs-lookup"><span data-stu-id="fa96e-213">In the **Results** pane verify you see at least one instance listed.</span></span> <span data-ttu-id="fa96e-214">Pode haver outras instâncias de execuções anteriores se ocorreu uma exceção durante a execução.</span><span class="sxs-lookup"><span data-stu-id="fa96e-214">There may be other instances from prior runs if an exception occurred while running.</span></span> <span data-ttu-id="fa96e-215">Você pode excluir linhas existentes, clicando com o botão direito em **System.Activities.DurableInstancing.Instances** e selecionando **Editar Top 200 linhas**, pressione a **Execute** botão Selecionar todas as linhas no painel de resultados e selecionando **excluir**.</span><span class="sxs-lookup"><span data-stu-id="fa96e-215">You can delete existing rows by right clicking **System.Activities.DurableInstancing.Instances** and selecting **Edit Top 200 rows**, pressing the **Execute** button, selecting all rows in the results pane and selecting **delete**.</span></span>  <span data-ttu-id="fa96e-216">Para verificar a instância exibida no banco de dados é a instância do seu aplicativo criado, verifique se o modo de exibição de instâncias está vazio antes de executar o cliente.</span><span class="sxs-lookup"><span data-stu-id="fa96e-216">To verify the instance displayed in the database is the instance your application created, verify the instances view is empty prior to running the client.</span></span> <span data-ttu-id="fa96e-217">Depois que o cliente está em execução novamente executar a consulta (Selecionar 1000 linhas superiores) e verifique se foi adicionada uma nova instância.</span><span class="sxs-lookup"><span data-stu-id="fa96e-217">Once the client is running re-run the query (Select Top 1000 Rows) and verify a new instance has been added.</span></span>  
  
7.  <span data-ttu-id="fa96e-218">Pressione enter para enviar a mensagem do item add para o serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fa96e-218">Press enter to send the add item message to the workflow service.</span></span> <span data-ttu-id="fa96e-219">O cliente exibirá o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="fa96e-219">The client will display the following text:</span></span>  
  
    ```Output  
    Sending add item messageService returned: Item added to orderPress any key to continue . . .  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fa96e-220">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa96e-220">See Also</span></span>  
 [<span data-ttu-id="fa96e-221">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="fa96e-221">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
