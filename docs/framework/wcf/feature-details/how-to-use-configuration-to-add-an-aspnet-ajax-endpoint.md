---
title: "Como utilizar a configuração para adicionar um ponto de extremidade AJAX ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e1b46239366c38b54a38e3ce62b59c81eeb3316c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="69657-102">Como utilizar a configuração para adicionar um ponto de extremidade AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="69657-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="69657-103">permite que você crie um serviço que permite que um ponto de extremidade AJAX ASP.NET habilitado disponível que pode ser chamado do JavaScript em um site do cliente.</span><span class="sxs-lookup"><span data-stu-id="69657-103"> allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="69657-104">Para criar um ponto de extremidade, você pode usar um arquivo de configuração, assim como acontece com todos os outros [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pontos de extremidade, ou use um método que não requer nenhum elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="69657-104">To create such an endpoint, you can either use a configuration file, as with all other [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="69657-105">Este tópico demonstra o método de configuração.</span><span class="sxs-lookup"><span data-stu-id="69657-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="69657-106">A parte do procedimento que permite que o ponto de extremidade de serviço seja habilitado pelo AJAX ASP.NET consiste em configurar o ponto de extremidade para usar o <xref:System.ServiceModel.WebHttpBinding> e adicionar o [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="69657-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="69657-107">Depois de configurar o ponto de extremidade, as etapas para implementar e hospedar o serviço são semelhantes àquelas usadas por qualquer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="69657-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="69657-108">Para obter um exemplo de funcionamento, consulte o [AJAX Service usando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="69657-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="69657-109">como configurar um ponto de extremidade do ASP.NET AJAX sem utilizar a configuração, consulte [como: adicionar um ASP.NET AJAX ponto de extremidade sem usando a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="69657-109"> how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="69657-110">Para criar um serviço WCF básico</span><span class="sxs-lookup"><span data-stu-id="69657-110">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="69657-111">Definir um basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contrato de serviço com uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="69657-111">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="69657-112">Marcar cada operação com o <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="69657-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="69657-113">Certifique-se de definir o <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="69657-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```  
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  <span data-ttu-id="69657-114">Implementar o `ICalculator` contrato de serviço com um `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="69657-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="69657-115">Definir um namespace para o `ICalculator` e `CalculatorService` implementações encapsulando-os em um bloco de namespace.</span><span class="sxs-lookup"><span data-stu-id="69657-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="69657-116">Para criar um ponto de extremidade AJAX ASP.NET para o serviço</span><span class="sxs-lookup"><span data-stu-id="69657-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1.  <span data-ttu-id="69657-117">Criar uma configuração de comportamento e especificar o [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento para habilitado para AJAX ASP.NET pontos de extremidade do serviço.</span><span class="sxs-lookup"><span data-stu-id="69657-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="69657-118">Criar um ponto de extremidade para o serviço que usa o <xref:System.ServiceModel.WebHttpBinding> e o comportamento de ASP.NET AJAX definido na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="69657-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"   
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>   
    ```  
  
### <a name="to-host-the-service-in-iis"></a><span data-ttu-id="69657-119">Para hospedar o serviço no IIS</span><span class="sxs-lookup"><span data-stu-id="69657-119">To host the service in IIS</span></span>  
  
1.  <span data-ttu-id="69657-120">Para hospedar o serviço no IIS, crie um novo arquivo chamado serviço com uma extensão. svc no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="69657-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="69657-121">Editar esse arquivo adicionando apropriada [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informações de diretiva para o serviço.</span><span class="sxs-lookup"><span data-stu-id="69657-121">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="69657-122">Por exemplo, o conteúdo do arquivo de serviço para o `CalculatorService` exemplo contém as informações a seguir.</span><span class="sxs-lookup"><span data-stu-id="69657-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="69657-123">hospedagem no IIS, consulte [como: hospedar um serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="69657-123"> hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="69657-124">Para chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="69657-124">To call the service</span></span>  
  
1.  <span data-ttu-id="69657-125">O ponto de extremidade é configurado em um endereço vazio em relação ao arquivo. svc, portanto, o serviço agora está disponível e pode ser chamado enviando solicitações para service.svc/\<operação > - por exemplo, service.svc/Add para o `Add` operação.</span><span class="sxs-lookup"><span data-stu-id="69657-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="69657-126">Você pode usá-lo digitando a URL de ponto de extremidade para a coleção de Scripts do controle de Gerenciador de Script do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="69657-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="69657-127">Para obter um exemplo, consulte o [AJAX Service usando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="69657-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69657-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69657-128">See Also</span></span>  
 [<span data-ttu-id="69657-129">Criando serviços WCF para o ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="69657-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="69657-130">Como migrar serviços Web do ASP.NET habilitados para AJAX para o WCF</span><span class="sxs-lookup"><span data-stu-id="69657-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
