---
title: 'Como: publicar metadados utilizando código para um serviço'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 870142724321629d6dbeccd4118b814283901776
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297961"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="14a00-102">Como: publicar metadados utilizando código para um serviço</span><span class="sxs-lookup"><span data-stu-id="14a00-102">How to: Publish Metadata for a Service Using Code</span></span>
<span data-ttu-id="14a00-103">Esse é um dos dois tópicos que discutem os metadados de publicação para um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="14a00-103">This is one of two how-to topics that discuss publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="14a00-104">Há duas maneiras para especificar como um serviço deve publicar metadados, usando um arquivo de configuração e código.</span><span class="sxs-lookup"><span data-stu-id="14a00-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="14a00-105">Este tópico mostra como publicar metadados para um serviço usando um código.</span><span class="sxs-lookup"><span data-stu-id="14a00-105">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="14a00-106">Este tópico mostra como publicar metadados de maneira não segura.</span><span class="sxs-lookup"><span data-stu-id="14a00-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="14a00-107">Qualquer cliente pode recuperar os metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="14a00-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="14a00-108">Se você precisar de seu serviço para publicar os metadados de uma maneira segura.</span><span class="sxs-lookup"><span data-stu-id="14a00-108">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="14a00-109">ver [ponto de extremidade do personalizado proteger metadados](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="14a00-109">see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="14a00-110">Para obter mais informações sobre metadados de publicação em um arquivo de configuração, consulte [como: Publicar metadados para um serviço usando um arquivo de configuração](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="14a00-110">For more information about publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="14a00-111">Metadados de publicação permite que os clientes recuperar os metadados usando uma solicitação GET do WS-Transfer ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="14a00-111">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="14a00-112">Para certificar-se de que o código está funcionando você deve criar um serviço WCF básico.</span><span class="sxs-lookup"><span data-stu-id="14a00-112">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="14a00-113">Um serviço auto-hospedado básico é fornecido no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="14a00-113">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="14a00-114">Para publicar os metadados no código</span><span class="sxs-lookup"><span data-stu-id="14a00-114">To publish metadata in code</span></span>  
  
1. <span data-ttu-id="14a00-115">Dentro do método principal de um aplicativo de console, instanciar um <xref:System.ServiceModel.ServiceHost> objeto, passando o tipo de serviço e o endereço básico.</span><span class="sxs-lookup"><span data-stu-id="14a00-115">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. <span data-ttu-id="14a00-116">Criar um bloco try, imediatamente abaixo do código para a etapa 1, e captura qualquer exceção que é gerada enquanto o serviço está em execução.</span><span class="sxs-lookup"><span data-stu-id="14a00-116">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. <span data-ttu-id="14a00-117">Verifique se o host de serviço já contém um <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, se não estiver, crie um novo <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instância.</span><span class="sxs-lookup"><span data-stu-id="14a00-117">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. <span data-ttu-id="14a00-118">Defina o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> propriedade</span><span class="sxs-lookup"><span data-stu-id="14a00-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to</span></span> `true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. <span data-ttu-id="14a00-119">O <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contém um <xref:System.ServiceModel.Description.MetadataExporter> propriedade.</span><span class="sxs-lookup"><span data-stu-id="14a00-119">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="14a00-120">O <xref:System.ServiceModel.Description.MetadataExporter> contém um <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="14a00-120">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="14a00-121">Definir o valor de <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> propriedade para <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span><span class="sxs-lookup"><span data-stu-id="14a00-121">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="14a00-122">O <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> propriedade também pode ser definida como <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span><span class="sxs-lookup"><span data-stu-id="14a00-122">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="14a00-123">Quando definido como <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> o exportador de metadados gera informações de política com os metadados que "está em conformidade com WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="14a00-123">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="14a00-124">Quando definido como <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> o exportador de metadados gera informações de política que está em conformidade com WS-Policy 1.2.</span><span class="sxs-lookup"><span data-stu-id="14a00-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. <span data-ttu-id="14a00-125">Adicionar o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instância à coleção de comportamentos do host de serviço.</span><span class="sxs-lookup"><span data-stu-id="14a00-125">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. <span data-ttu-id="14a00-126">Adicione o ponto de extremidade de troca de metadados para o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="14a00-126">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. <span data-ttu-id="14a00-127">Adicione um ponto de extremidade do aplicativo para o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="14a00-127">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  <span data-ttu-id="14a00-128">Se você não adicionar nenhum ponto de extremidade ao serviço, o tempo de execução adicionará pontos de extremidade padrão para você.</span><span class="sxs-lookup"><span data-stu-id="14a00-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="14a00-129">Neste exemplo, porque o serviço tem um <xref:System.ServiceModel.Description.ServiceMetadataBehavior> definido como `true`, o serviço tem metadados de publicação habilitados.</span><span class="sxs-lookup"><span data-stu-id="14a00-129">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> <span data-ttu-id="14a00-130">Para obter mais informações sobre pontos de extremidade padrão, consulte [configuração simplificado](../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="14a00-130">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="14a00-131">Abra o host de serviço e aguarde até que as chamadas de entrada.</span><span class="sxs-lookup"><span data-stu-id="14a00-131">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="14a00-132">Quando o usuário pressiona ENTER, feche o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="14a00-132">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="14a00-133">Compile e execute o aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="14a00-133">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="14a00-134">Usar o Internet Explorer para navegar até o endereço base do serviço (http://localhost:8001/MetadataSample neste exemplo) e verifique se a publicação de metadados está ligada.</span><span class="sxs-lookup"><span data-stu-id="14a00-134">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="14a00-135">Você deve ver uma página da Web exibida informando que "Simple Service" na parte superior e imediatamente abaixo de "Você ter criado um serviço".</span><span class="sxs-lookup"><span data-stu-id="14a00-135">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="14a00-136">Caso contrário, exibe uma mensagem na parte superior da página resultante: "Publicação de metadados para este serviço está desabilitada no momento."</span><span class="sxs-lookup"><span data-stu-id="14a00-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="14a00-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="14a00-137">Example</span></span>  
 <span data-ttu-id="14a00-138">O exemplo de código a seguir mostra a implementação de um serviço WCF básico que publica metadados para o serviço no código.</span><span class="sxs-lookup"><span data-stu-id="14a00-138">The following code example shows the implementation of a basic WCF service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="14a00-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14a00-139">See also</span></span>

- [<span data-ttu-id="14a00-140">Como: hospedar um serviço do WCF em um aplicativo gerenciado</span><span class="sxs-lookup"><span data-stu-id="14a00-140">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="14a00-141">Self-Host</span><span class="sxs-lookup"><span data-stu-id="14a00-141">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="14a00-142">Visão geral da arquitetura de metadados</span><span class="sxs-lookup"><span data-stu-id="14a00-142">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="14a00-143">Utilizando metadados</span><span class="sxs-lookup"><span data-stu-id="14a00-143">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="14a00-144">Como: publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="14a00-144">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
