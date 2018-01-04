---
title: "Como hospedar um serviço do WCF em um aplicativo gerenciado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6491faa6134c1e80e07294d8f888200c04fa8704
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-wcf-service-in-a-managed-application"></a><span data-ttu-id="bfd39-102">Como hospedar um serviço do WCF em um aplicativo gerenciado</span><span class="sxs-lookup"><span data-stu-id="bfd39-102">How to: Host a WCF Service in a Managed Application</span></span>
<span data-ttu-id="bfd39-103">Para hospedar um serviço dentro de um aplicativo gerenciado, o código inserido para o serviço dentro do código de aplicativo gerenciado, definir um ponto de extremidade para o serviço de imperativa no código, declarativamente por meio de configuração ou usando os pontos de extremidade padrão e, em seguida, criar um instância do <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="bfd39-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
 <span data-ttu-id="bfd39-104">Para iniciar o recebimento de mensagens, chame <xref:System.ServiceModel.ICommunicationObject.Open%2A> em <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="bfd39-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="bfd39-105">Isso cria e abre o ouvinte para o serviço.</span><span class="sxs-lookup"><span data-stu-id="bfd39-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="bfd39-106">Hospedar um serviço dessa maneira é conhecida como "hospedagem interna" porque o aplicativo gerenciado está fazendo o trabalho de hospedagem em si.</span><span class="sxs-lookup"><span data-stu-id="bfd39-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="bfd39-107">Para fechar o serviço, chame <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> em <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="bfd39-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
 <span data-ttu-id="bfd39-108">Um serviço também pode ser hospedado em um serviço gerenciado do Windows, no Internet Information Services (IIS) ou no serviço de ativação de processo para Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="bfd39-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="bfd39-109">opções para um serviço de hospedagem, consulte [serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="bfd39-109"> hosting options for a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
 <span data-ttu-id="bfd39-110">Hospedar um serviço em um aplicativo gerenciado é a opção mais flexível porque ela exige a menor infra-estrutura para implantar.</span><span class="sxs-lookup"><span data-stu-id="bfd39-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="bfd39-111">hospedagem de serviços em aplicativos gerenciados, consulte [hospedando um aplicativo gerenciado](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="bfd39-111"> hosting services in managed applications, see [Hosting in a Managed Application](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>  
  
 <span data-ttu-id="bfd39-112">O procedimento a seguir demonstra como implementar um serviço hospedado automaticamente em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="bfd39-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>  
  
### <a name="to-create-a-self-hosted-service"></a><span data-ttu-id="bfd39-113">Para criar um serviço auto-hospedado</span><span class="sxs-lookup"><span data-stu-id="bfd39-113">To create a self-hosted service</span></span>  
  
1.  <span data-ttu-id="bfd39-114">Abra [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] e selecione **novo**, **projeto...**  do **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="bfd39-114">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and select **New**, **Project...** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="bfd39-115">No **modelos instalados** lista, selecione **Visual C#**, **Windows** ou **Visual Basic**, **Windows**.</span><span class="sxs-lookup"><span data-stu-id="bfd39-115">In the **Installed Templates** list, select **Visual C#**, **Windows** or **Visual Basic**, **Windows**.</span></span> <span data-ttu-id="bfd39-116">Dependendo de seu [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] configurações, um ou ambos podem estar sob o **outras linguagens** nó no **modelos instalados** lista.</span><span class="sxs-lookup"><span data-stu-id="bfd39-116">Depending on your [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] settings, one or both of these may be under the **Other Languages** node in the **Installed Templates** list.</span></span>  
  
3.  <span data-ttu-id="bfd39-117">Selecione **aplicativo de Console** do **Windows** lista.</span><span class="sxs-lookup"><span data-stu-id="bfd39-117">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="bfd39-118">Tipo `SelfHost` no **nome** caixa e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="bfd39-118">Type `SelfHost` in the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="bfd39-119">Clique com botão direito **SelfHost** na **Solution Explorer** e selecione **adicionar referência...** . Selecione **System. ServiceModel** do **.NET** guia e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="bfd39-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference...**. Select **System.ServiceModel** from the **.NET** tab and click **OK**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="bfd39-120">Se o **Solution Explorer** janela não estiver visível, selecione **Solution Explorer** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="bfd39-120">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="bfd39-121">Clique duas vezes em **Program.cs** ou **Module1. vb** na **Solution Explorer** para abri-lo na janela de código, se ainda não estiver aberto.</span><span class="sxs-lookup"><span data-stu-id="bfd39-121">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window if it is not already open.</span></span> <span data-ttu-id="bfd39-122">Adicione as instruções a seguir na parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="bfd39-122">Add the following statements at the top of the file.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  <span data-ttu-id="bfd39-123">Definir e implementar um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="bfd39-123">Define and implement a service contract.</span></span> <span data-ttu-id="bfd39-124">Este exemplo define um `HelloWorldService` que retorna uma mensagem com base na entrada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="bfd39-124">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="bfd39-125">como definir e implementar uma interface de serviço, consulte [como: definir um contrato de serviço](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) e [como: implementar um contrato de serviço](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="bfd39-125"> how to define and implement a service interface, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span></span>  
  
7.  <span data-ttu-id="bfd39-126">Na parte superior do `Main` método, crie uma instância do <xref:System.Uri> classe com o endereço base para o serviço.</span><span class="sxs-lookup"><span data-stu-id="bfd39-126">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  <span data-ttu-id="bfd39-127">Criar uma instância do <xref:System.ServiceModel.ServiceHost> classe, passando um <xref:System.Type> que representa o tipo de serviço e a base de identificador de recurso uniforme (URI) para resolver o <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="bfd39-127">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="bfd39-128">Habilitar a publicação de metadados e, em seguida, chame o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método o <xref:System.ServiceModel.ServiceHost> para inicializar o serviço e prepará-lo para receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="bfd39-128">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]       
  
    > [!NOTE]
    >  <span data-ttu-id="bfd39-129">Este exemplo usa pontos de extremidade padrão, e nenhum arquivo de configuração é necessário para este serviço.</span><span class="sxs-lookup"><span data-stu-id="bfd39-129">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="bfd39-130">Se nenhum ponto de extremidade estiverem configurados, o tempo de execução cria um ponto de extremidade para cada endereço base para cada contrato de serviço implementado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="bfd39-130">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="bfd39-131">pontos de extremidade padrão, consulte [configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bfd39-131"> default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="bfd39-132">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="bfd39-132">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
### <a name="to-test-the-service"></a><span data-ttu-id="bfd39-133">Para testar o serviço</span><span class="sxs-lookup"><span data-stu-id="bfd39-133">To test the service</span></span>  
  
1.  <span data-ttu-id="bfd39-134">Pressione Ctrl + F5 para executar o serviço.</span><span class="sxs-lookup"><span data-stu-id="bfd39-134">Press Ctrl + F5 to run the service.</span></span>  
  
2.  <span data-ttu-id="bfd39-135">Abra **cliente de teste do WCF**.</span><span class="sxs-lookup"><span data-stu-id="bfd39-135">Open **WCF Test Client**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="bfd39-136">Para abrir **cliente de teste do WCF**, abra um [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] prompt de comando e execute **WcfTestClient.exe**.</span><span class="sxs-lookup"><span data-stu-id="bfd39-136">To open **WCF Test Client**, open a [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] command prompt and execute **WcfTestClient.exe**.</span></span>  
  
3.  <span data-ttu-id="bfd39-137">Selecione **Adicionar serviço...**  do **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="bfd39-137">Select **Add Service...** from the **File** menu.</span></span>  
  
4.  <span data-ttu-id="bfd39-138">Tipo `http://localhost:8080/hello` para a caixa de endereço e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="bfd39-138">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="bfd39-139">Verifique se o serviço está em execução ou a etapa atual falhar.</span><span class="sxs-lookup"><span data-stu-id="bfd39-139">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="bfd39-140">Se você tiver alterado o endereço base no código, em seguida, use o endereço base modificado nesta etapa.</span><span class="sxs-lookup"><span data-stu-id="bfd39-140">If you have changed the base address in the code, then use the modified base address in this step.</span></span>  
  
5.  <span data-ttu-id="bfd39-141">Clique duas vezes em **SayHello** sob o **meus projetos de serviço** nó.</span><span class="sxs-lookup"><span data-stu-id="bfd39-141">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="bfd39-142">Digite seu nome no **valor** coluna o **solicitação** lista e clique em **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="bfd39-142">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span> <span data-ttu-id="bfd39-143">Será exibida uma mensagem de resposta no **resposta** lista.</span><span class="sxs-lookup"><span data-stu-id="bfd39-143">A reply message appears in the **Response** list.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfd39-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bfd39-144">Example</span></span>  
 <span data-ttu-id="bfd39-145">O exemplo a seguir cria um <xref:System.ServiceModel.ServiceHost> objeto para hospedar um serviço do tipo `HelloWorldService`e, em seguida, chama o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="bfd39-145">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="bfd39-146">Um endereço base é fornecido no código, a publicação de metadados está habilitada e pontos de extremidade padrão são usados.</span><span class="sxs-lookup"><span data-stu-id="bfd39-146">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="bfd39-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfd39-147">See Also</span></span>  
 <xref:System.Uri>  
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>  
 <xref:System.Configuration.ConfigurationManager>  
 [<span data-ttu-id="bfd39-148">Como hospedar um serviço WCF no IIS</span><span class="sxs-lookup"><span data-stu-id="bfd39-148">How to: Host a WCF Service in IIS</span></span>](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [<span data-ttu-id="bfd39-149">Auto-hospedagem</span><span class="sxs-lookup"><span data-stu-id="bfd39-149">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="bfd39-150">Hospedando serviços</span><span class="sxs-lookup"><span data-stu-id="bfd39-150">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="bfd39-151">Como definir um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="bfd39-151">How to: Define a Service Contract</span></span>](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [<span data-ttu-id="bfd39-152">Como implementar um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="bfd39-152">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [<span data-ttu-id="bfd39-153">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="bfd39-153">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="bfd39-154">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="bfd39-154">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="bfd39-155">Associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="bfd39-155">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
