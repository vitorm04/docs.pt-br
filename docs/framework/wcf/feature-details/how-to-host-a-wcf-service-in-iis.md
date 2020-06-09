---
title: Como hospedar um serviço WCF no IIS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 326a270c4af38738c910828acd483070ab02ecd1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593081"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="58b92-102">Como hospedar um serviço WCF no IIS</span><span class="sxs-lookup"><span data-stu-id="58b92-102">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="58b92-103">Este tópico descreve as etapas básicas necessárias para criar um serviço de Windows Communication Foundation (WCF) hospedado no Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="58b92-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="58b92-104">Este tópico pressupõe que você está familiarizado com o IIS e compreende como usar a ferramenta de gerenciamento do IIS para criar e gerenciar aplicativos do IIS.</span><span class="sxs-lookup"><span data-stu-id="58b92-104">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="58b92-105">Para obter mais informações sobre o IIS, consulte [serviços de informações da Internet](https://www.iis.net/).</span><span class="sxs-lookup"><span data-stu-id="58b92-105">For more information about IIS see [Internet Information Services](https://www.iis.net/).</span></span> <span data-ttu-id="58b92-106">Um serviço WCF executado no ambiente do IIS aproveita totalmente os recursos do IIS, como reciclagem de processo, desligamento ocioso, monitoramento de integridade do processo e ativação baseada em mensagem.</span><span class="sxs-lookup"><span data-stu-id="58b92-106">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="58b92-107">Essa opção de hospedando requer que o IIS esteja configurado corretamente, mas não requer que nenhum código de hospedagem seja escrito como parte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58b92-107">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="58b92-108">Você pode usar a hospedagem do IIS somente com um transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="58b92-108">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="58b92-109">Para obter mais informações sobre como o WCF e o ASP.NET interagem, consulte [Serviços WCF e ASP.net](wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="58b92-109">For more information about how WCF and ASP.NET interact, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="58b92-110">Para obter mais informações sobre como configurar a segurança, consulte [segurança](security.md).</span><span class="sxs-lookup"><span data-stu-id="58b92-110">For more information about configuring security, see [Security](security.md).</span></span>  
  
 <span data-ttu-id="58b92-111">Para a cópia de origem deste exemplo, consulte [hospedagem do IIS usando código embutido](../samples/iis-hosting-using-inline-code.md).</span><span class="sxs-lookup"><span data-stu-id="58b92-111">For the source copy of this example, see [IIS Hosting Using Inline Code](../samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="58b92-112">Para criar um serviço hospedado pelo IIS</span><span class="sxs-lookup"><span data-stu-id="58b92-112">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="58b92-113">Confirme se o IIS está instalado e em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="58b92-113">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="58b92-114">Para obter mais informações sobre como instalar e configurar o IIS, consulte [Instalando e Configurando o iis 7,0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span><span class="sxs-lookup"><span data-stu-id="58b92-114">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span></span>  
  
2. <span data-ttu-id="58b92-115">Crie uma nova pasta para os arquivos de aplicativo chamados "IISHostedCalcService", verifique se ASP.NET tem acesso ao conteúdo da pasta e use a ferramenta de gerenciamento do IIS para criar um novo aplicativo do IIS que está localizado fisicamente nesse diretório de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58b92-115">Create a new folder for your application files called "IISHostedCalcService", ensure that ASP.NET has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="58b92-116">Ao criar um alias para o diretório do aplicativo, use “IISHostedCalc”.</span><span class="sxs-lookup"><span data-stu-id="58b92-116">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="58b92-117">Crie um novo arquivo denominado “service.svc” no diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58b92-117">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="58b92-118">Edite esse arquivo adicionando o seguinte @ServiceHost elemento.</span><span class="sxs-lookup"><span data-stu-id="58b92-118">Edit this file by adding the following @ServiceHost element.</span></span>  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. <span data-ttu-id="58b92-119">Crie um subdiretório App_Code no diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58b92-119">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="58b92-120">Crie um novo arquivo de código denominado Service.cs no subdiretório App_Code.</span><span class="sxs-lookup"><span data-stu-id="58b92-120">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="58b92-121">Adicione as seguintes instruções de uso na parte superior do arquivo Service.cs.</span><span class="sxs-lookup"><span data-stu-id="58b92-121">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="58b92-122">Adicione a seguinte declaração de namespace depois das instruções de uso.</span><span class="sxs-lookup"><span data-stu-id="58b92-122">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="58b92-123">Defina o contrato de serviço na declaração do namespace conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="58b92-123">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="58b92-124">Implemente o contrato de serviço depois da definição do contrato de serviço conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="58b92-124">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="58b92-125">Crie um arquivo denominado "Web.config" no diretório do aplicativo e adicione o seguinte código de configuração no arquivo.</span><span class="sxs-lookup"><span data-stu-id="58b92-125">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="58b92-126">Em tempo de execução, a infraestrutura do WCF usa as informações para construir um ponto de extremidade com o qual os aplicativos cliente podem se comunicar.</span><span class="sxs-lookup"><span data-stu-id="58b92-126">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     <span data-ttu-id="58b92-127">Este exemplo especifica explicitamente pontos de extremidade no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="58b92-127">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="58b92-128">Se você não adicionar nenhum ponto de extremidade ao serviço, o runtime adicionará pontos de extremidade padrão para você.</span><span class="sxs-lookup"><span data-stu-id="58b92-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="58b92-129">Para obter mais informações sobre pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificada](../simplified-configuration.md) e [configuração simplificada para serviços WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="58b92-129">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="58b92-130">Para verificar se o serviço está hospedado corretamente, abra uma instância do Internet Explorer e navegue para a URL do serviço: `http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="58b92-130">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="58b92-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="58b92-131">Example</span></span>  
 <span data-ttu-id="58b92-132">A listagem a seguir relaciona todo o código do serviço de calculadora hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="58b92-132">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="58b92-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58b92-133">See also</span></span>

- [<span data-ttu-id="58b92-134">Hospedagem no Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="58b92-134">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="58b92-135">Hospedando serviços</span><span class="sxs-lookup"><span data-stu-id="58b92-135">Hosting Services</span></span>](../hosting-services.md)
- [<span data-ttu-id="58b92-136">Serviços WCF e ASP.NET</span><span class="sxs-lookup"><span data-stu-id="58b92-136">WCF Services and ASP.NET</span></span>](wcf-services-and-aspnet.md)
- [<span data-ttu-id="58b92-137">Segurança</span><span class="sxs-lookup"><span data-stu-id="58b92-137">Security</span></span>](security.md)
- <span data-ttu-id="58b92-138">[Recursos de hospedagem do Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="58b92-138">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
