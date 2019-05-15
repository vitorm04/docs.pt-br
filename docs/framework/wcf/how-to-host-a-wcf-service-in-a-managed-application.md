---
title: 'Como: hospedar um serviço do WCF em um aplicativo gerenciado'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: b6d1c9c38e2cc5f1b1b7b5538af0339987563de6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637590"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a><span data-ttu-id="26b1d-102">Como: Hospedar um serviço WCF em um aplicativo gerenciado</span><span class="sxs-lookup"><span data-stu-id="26b1d-102">How to: Host a WCF service in a managed app</span></span>

<span data-ttu-id="26b1d-103">Para hospedar um serviço dentro de um aplicativo gerenciado, incorporar o código para o serviço dentro do código de aplicativo gerenciado, definir um ponto de extremidade para o serviço imperativa no código, declarativamente por meio de configuração ou usando os pontos de extremidade padrão e, em seguida, criar um instância do <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="26b1d-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="26b1d-104">Para iniciar o recebimento de mensagens, chame <xref:System.ServiceModel.ICommunicationObject.Open%2A> em <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="26b1d-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="26b1d-105">Isso cria e abre o ouvinte para o serviço.</span><span class="sxs-lookup"><span data-stu-id="26b1d-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="26b1d-106">Hospedar um serviço dessa maneira é conhecido como "auto-hospedagem" porque o aplicativo gerenciado está fazendo o trabalho de hospedagem em si.</span><span class="sxs-lookup"><span data-stu-id="26b1d-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="26b1d-107">Para fechar o serviço, chame <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> em <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="26b1d-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="26b1d-108">Um serviço também pode ser hospedado em um serviço gerenciado do Windows, no Internet Information Services (IIS) ou no serviço de ativação de processos para Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="26b1d-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="26b1d-109">Para obter mais informações sobre as opções para um serviço de hospedagem, consulte [serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="26b1d-109">For more information about hosting options for a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>

<span data-ttu-id="26b1d-110">Hospedar um serviço em um aplicativo gerenciado é a opção mais flexível porque requer que a infra-estrutura mínimos para implantar.</span><span class="sxs-lookup"><span data-stu-id="26b1d-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="26b1d-111">Para obter mais informações sobre hospedagem de serviços em aplicativos gerenciados, consulte [hospedagem em um aplicativo gerenciado](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="26b1d-111">For more information about hosting services in managed applications, see [Hosting in a Managed Application](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

<span data-ttu-id="26b1d-112">O procedimento a seguir demonstra como implementar um serviço auto-hospedado em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="26b1d-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>

## <a name="create-a-self-hosted-service"></a><span data-ttu-id="26b1d-113">Criar um serviço auto-hospedado</span><span class="sxs-lookup"><span data-stu-id="26b1d-113">Create a self-hosted service</span></span>

1. <span data-ttu-id="26b1d-114">Crie um novo aplicativo de console:</span><span class="sxs-lookup"><span data-stu-id="26b1d-114">Create a new console application:</span></span>

   1. <span data-ttu-id="26b1d-115">Abra o Visual Studio e selecione **New** > **projeto** do **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="26b1d-115">Open Visual Studio and select **New** > **Project** from the **File** menu.</span></span>

   2. <span data-ttu-id="26b1d-116">No **modelos instalados** lista, selecione **Visual c#** ou **Visual Basic**e, em seguida, selecione **Windows Desktop**.</span><span class="sxs-lookup"><span data-stu-id="26b1d-116">In the **Installed Templates** list, select **Visual C#** or **Visual Basic**, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="26b1d-117">Selecione o **aplicativo de Console** modelo.</span><span class="sxs-lookup"><span data-stu-id="26b1d-117">Select the **Console App** template.</span></span> <span data-ttu-id="26b1d-118">Tipo de `SelfHost` no **nome** caixa e, em seguida, escolha **Okey**.</span><span class="sxs-lookup"><span data-stu-id="26b1d-118">Type `SelfHost` in the **Name** box and then choose **OK**.</span></span>

2. <span data-ttu-id="26b1d-119">Clique com botão direito **SelfHost** na **Gerenciador de soluções** e selecione **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="26b1d-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="26b1d-120">Selecione **System. ServiceModel** da **.NET** guia e, em seguida, escolha **Okey**.</span><span class="sxs-lookup"><span data-stu-id="26b1d-120">Select **System.ServiceModel** from the **.NET** tab and then choose **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="26b1d-121">Se o **Gerenciador de soluções** janela não estiver visível, selecione **Gerenciador de soluções** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="26b1d-121">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="26b1d-122">Clique duas vezes em **Program.cs** ou **Module1.vb** na **Gerenciador de soluções** para abri-lo na janela de código, se ele não ainda estiver aberto.</span><span class="sxs-lookup"><span data-stu-id="26b1d-122">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window, if it's not already open.</span></span> <span data-ttu-id="26b1d-123">Adicione as seguintes instruções na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="26b1d-123">Add the following statements at the top of the file:</span></span>

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. <span data-ttu-id="26b1d-124">Definir e implementar um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="26b1d-124">Define and implement a service contract.</span></span> <span data-ttu-id="26b1d-125">Este exemplo define um `HelloWorldService` que retorna uma mensagem com base na entrada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="26b1d-125">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > <span data-ttu-id="26b1d-126">Para obter mais informações sobre como definir e implementar uma interface de serviço, consulte [como: Definir um contrato de serviço](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) e [como: Implementar um contrato de serviço](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="26b1d-126">For more information about how to define and implement a service interface, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span></span>

5. <span data-ttu-id="26b1d-127">Na parte superior dos `Main` método, crie uma instância da <xref:System.Uri> classe com o endereço base para o serviço.</span><span class="sxs-lookup"><span data-stu-id="26b1d-127">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. <span data-ttu-id="26b1d-128">Criar uma instância das <xref:System.ServiceModel.ServiceHost> classe, passando um <xref:System.Type> que representa o tipo de serviço e a base de identificador de recurso uniforme (URI) para resolver o <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="26b1d-128">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="26b1d-129">Habilitar a publicação de metadados e, em seguida, chame o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método no <xref:System.ServiceModel.ServiceHost> para inicializar o serviço e prepará-lo para receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="26b1d-129">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > <span data-ttu-id="26b1d-130">Este exemplo usa pontos de extremidade padrão e nenhum arquivo de configuração é necessário para este serviço.</span><span class="sxs-lookup"><span data-stu-id="26b1d-130">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="26b1d-131">Se nenhum ponto de extremidade estiverem configurados, o tempo de execução cria um ponto de extremidade para cada endereço base para cada contrato de serviço implementado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="26b1d-131">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="26b1d-132">Para obter mais informações sobre pontos de extremidade padrão, consulte [configuração simplificado](../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="26b1d-132">For more information about default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

7. <span data-ttu-id="26b1d-133">Pressione **Ctrl**+**Shift**+**B** para compilar a solução.</span><span class="sxs-lookup"><span data-stu-id="26b1d-133">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="test-the-service"></a><span data-ttu-id="26b1d-134">Testar o serviço</span><span class="sxs-lookup"><span data-stu-id="26b1d-134">Test the service</span></span>

1. <span data-ttu-id="26b1d-135">Pressione **Ctrl**+**F5** para executar o serviço.</span><span class="sxs-lookup"><span data-stu-id="26b1d-135">Press **Ctrl**+**F5** to run the service.</span></span>

2. <span data-ttu-id="26b1d-136">Abra **cliente de teste do WCF**.</span><span class="sxs-lookup"><span data-stu-id="26b1d-136">Open **WCF Test Client**.</span></span>

    > [!TIP]
    > <span data-ttu-id="26b1d-137">Para abrir **cliente de teste do WCF**, abra o Prompt de comando do desenvolvedor para Visual Studio e executar **WcfTestClient.exe**.</span><span class="sxs-lookup"><span data-stu-id="26b1d-137">To open **WCF Test Client**, open Developer Command Prompt for Visual Studio and execute **WcfTestClient.exe**.</span></span>

3. <span data-ttu-id="26b1d-138">Selecione **Adicionar serviço** da **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="26b1d-138">Select **Add Service** from the **File** menu.</span></span>

4. <span data-ttu-id="26b1d-139">Tipo de `http://localhost:8080/hello` para a caixa de endereço e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="26b1d-139">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="26b1d-140">Verifique se o serviço está em execução ou a etapa atual falhar.</span><span class="sxs-lookup"><span data-stu-id="26b1d-140">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="26b1d-141">Se você tiver alterado o endereço base no código, em seguida, use o endereço base modificado nesta etapa.</span><span class="sxs-lookup"><span data-stu-id="26b1d-141">If you have changed the base address in the code, then use the modified base address in this step.</span></span>

5. <span data-ttu-id="26b1d-142">Clique duas vezes em **SayHello** sob o **meus projetos de serviço** nó.</span><span class="sxs-lookup"><span data-stu-id="26b1d-142">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="26b1d-143">Digite seu nome na **valor** coluna na **solicitar** lista e clique em **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="26b1d-143">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span>

   <span data-ttu-id="26b1d-144">Será exibida uma mensagem de resposta na **resposta** lista.</span><span class="sxs-lookup"><span data-stu-id="26b1d-144">A reply message appears in the **Response** list.</span></span>

## <a name="example"></a><span data-ttu-id="26b1d-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26b1d-145">Example</span></span>

<span data-ttu-id="26b1d-146">O exemplo a seguir cria uma <xref:System.ServiceModel.ServiceHost> objeto para hospedar um serviço do tipo `HelloWorldService`e, em seguida, chama o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método em <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="26b1d-146">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="26b1d-147">Um endereço base é fornecido no código, a publicação de metadados está habilitada e pontos de extremidade padrão são usados.</span><span class="sxs-lookup"><span data-stu-id="26b1d-147">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="26b1d-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26b1d-148">See also</span></span>

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [<span data-ttu-id="26b1d-149">Como: Hospedar um serviço WCF no IIS</span><span class="sxs-lookup"><span data-stu-id="26b1d-149">How to: Host a WCF Service in IIS</span></span>](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [<span data-ttu-id="26b1d-150">Auto-hospedagem</span><span class="sxs-lookup"><span data-stu-id="26b1d-150">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="26b1d-151">Hospedando serviços</span><span class="sxs-lookup"><span data-stu-id="26b1d-151">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="26b1d-152">Como: Definir um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="26b1d-152">How to: Define a Service Contract</span></span>](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="26b1d-153">Como: Implementar um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="26b1d-153">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="26b1d-154">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="26b1d-154">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="26b1d-155">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="26b1d-155">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="26b1d-156">Associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="26b1d-156">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
