---
title: "Como hospedar um serviço WCF no IIS"
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
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b23d3f69d52299fcf3ca8b5ff56d0c4673026b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="30137-102">Como hospedar um serviço WCF no IIS</span><span class="sxs-lookup"><span data-stu-id="30137-102">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="30137-103">Este tópico descreve as etapas básicas necessárias para criar um serviço [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] que é hospedado por um IIS (Serviços de Informações da Internet).</span><span class="sxs-lookup"><span data-stu-id="30137-103">This topic outlines the basic steps required to create a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="30137-104">Este tópico pressupõe que você está familiarizado com o IIS e compreende como usar a ferramenta de gerenciamento do IIS para criar e gerenciar aplicativos do IIS.</span><span class="sxs-lookup"><span data-stu-id="30137-104">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="30137-105">Consulte IIS [Internet Information Services](http://go.microsoft.com/fwlink/?LinkId=132449).</span><span class="sxs-lookup"><span data-stu-id="30137-105"> IIS see [Internet Information Services](http://go.microsoft.com/fwlink/?LinkId=132449).</span></span> <span data-ttu-id="30137-106">Um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que é executado no ambiente do IIS aproveita os recursos do IIS, como a reciclagem do processo, desligamento ocioso, monitoramento de integridade do processo e a ativação baseada em mensagem.</span><span class="sxs-lookup"><span data-stu-id="30137-106">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="30137-107">Essa opção de hospedando requer que o IIS esteja configurado corretamente, mas não requer que nenhum código de hospedagem seja escrito como parte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30137-107">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="30137-108">Você pode usar a hospedagem do IIS somente com um transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="30137-108">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="30137-109">como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] interagir, consulte [serviços WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="30137-109"> how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] interact, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="30137-110">Configurando a segurança, consulte [segurança](../../../../docs/framework/wcf/feature-details/security.md).</span><span class="sxs-lookup"><span data-stu-id="30137-110"> configuring security, see [Security](../../../../docs/framework/wcf/feature-details/security.md).</span></span>  
  
 <span data-ttu-id="30137-111">Para a cópia de origem deste exemplo, consulte [IIS hospedagem utilizando código embutido](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span><span class="sxs-lookup"><span data-stu-id="30137-111">For the source copy of this example, see [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="30137-112">Para criar um serviço hospedado pelo IIS</span><span class="sxs-lookup"><span data-stu-id="30137-112">To create a service hosted by IIS</span></span>  
  
1.  <span data-ttu-id="30137-113">Confirme se o IIS está instalado e em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="30137-113">Confirm that IIS is installed and running on your computer.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="30137-114">instalar e configurar o IIS consulte [instalando e configurando o IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=132128)</span><span class="sxs-lookup"><span data-stu-id="30137-114"> installing and configuring IIS see [Installing and Configuring IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=132128)</span></span>  
  
2.  <span data-ttu-id="30137-115">Crie uma nova pasta para os arquivos do aplicativo denominada “IISHostedCalcService”, certifique-se de que o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] tenha acesso ao conteúdo da pasta e use a ferramenta de gerenciamento do IIS para criar um novo aplicativo do IIS que esteja fisicamente localizado no diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30137-115">Create a new folder for your application files called "IISHostedCalcService", ensure that [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="30137-116">Ao criar um alias para o diretório do aplicativo, use “IISHostedCalc”.</span><span class="sxs-lookup"><span data-stu-id="30137-116">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3.  <span data-ttu-id="30137-117">Crie um novo arquivo denominado “service.svc” no diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30137-117">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="30137-118">Editar esse arquivo adicionando as seguintes @ServiceHost elemento.</span><span class="sxs-lookup"><span data-stu-id="30137-118">Edit this file by adding the following @ServiceHost element.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  <span data-ttu-id="30137-119">Crie um subdiretório App_Code no diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30137-119">Create an App_Code subdirectory within the application directory.</span></span>  
  
5.  <span data-ttu-id="30137-120">Crie um novo arquivo de código denominado Service.cs no subdiretório App_Code.</span><span class="sxs-lookup"><span data-stu-id="30137-120">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6.  <span data-ttu-id="30137-121">Adicione as seguintes instruções de uso na parte superior do arquivo Service.cs.</span><span class="sxs-lookup"><span data-stu-id="30137-121">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  <span data-ttu-id="30137-122">Adicione a seguinte declaração de namespace depois das instruções de uso.</span><span class="sxs-lookup"><span data-stu-id="30137-122">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  <span data-ttu-id="30137-123">Defina o contrato de serviço na declaração do namespace conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="30137-123">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="30137-124">Implemente o contrato de serviço depois da definição do contrato de serviço conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="30137-124">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="30137-125">Crie um arquivo denominado "Web.config" no diretório do aplicativo e adicione o seguinte código de configuração no arquivo.</span><span class="sxs-lookup"><span data-stu-id="30137-125">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="30137-126">Em tempo de execução, a infraestrutura do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa as informações para construir um ponto de extremidade com o qual os aplicativos-cliente possam se comunicar.</span><span class="sxs-lookup"><span data-stu-id="30137-126">At runtime, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     <span data-ttu-id="30137-127">Este exemplo especifica explicitamente pontos de extremidade no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="30137-127">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="30137-128">Se você não adicionar nenhum ponto de extremidade ao serviço, o tempo de execução adicionará pontos de extremidade padrão para você.</span><span class="sxs-lookup"><span data-stu-id="30137-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="30137-129">Consulte de pontos de extremidade, associações e comportamentos padrão [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="30137-129"> default endpoints, bindings, and behaviors see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="30137-130">Para verificar se o serviço está hospedado corretamente, abra uma instância do Internet Explorer e navegue para a URL do serviço: `http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="30137-130">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="30137-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30137-131">Example</span></span>  
 <span data-ttu-id="30137-132">A listagem a seguir relaciona todo o código do serviço de calculadora hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="30137-132">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="30137-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30137-133">See Also</span></span>  
 [<span data-ttu-id="30137-134">Hospedagem nos Serviços de Informações da Internet</span><span class="sxs-lookup"><span data-stu-id="30137-134">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [<span data-ttu-id="30137-135">Hospedando serviços</span><span class="sxs-lookup"><span data-stu-id="30137-135">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="30137-136">Serviços do WCF e ASP.NET</span><span class="sxs-lookup"><span data-stu-id="30137-136">WCF Services and ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [<span data-ttu-id="30137-137">Segurança</span><span class="sxs-lookup"><span data-stu-id="30137-137">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
 [<span data-ttu-id="30137-138">Recursos de hospedagem do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="30137-138">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
