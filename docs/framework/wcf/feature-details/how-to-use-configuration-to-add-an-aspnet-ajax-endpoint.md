---
title: 'Como: usar a configuração para adicionar um ponto de extremidade AJAX ASP.NET'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: db5085d01dbed841109ac46fe4e8b2a0143352e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337611"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="1edaa-102">Como: usar a configuração para adicionar um ponto de extremidade AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1edaa-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="1edaa-103">Windows Communication Foundation (WCF) permite que você crie um serviço que permite que um ponto de extremidade habilitados para AJAX ASP.NET disponível que podem ser chamados do JavaScript em um site do cliente.</span><span class="sxs-lookup"><span data-stu-id="1edaa-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="1edaa-104">Para criar um ponto de extremidade, você pode usar um arquivo de configuração, assim como acontece com todos os outros pontos de extremidade do Windows Communication Foundation (WCF) ou usar um método que não requer quaisquer elementos de configuração.</span><span class="sxs-lookup"><span data-stu-id="1edaa-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="1edaa-105">Este tópico demonstra a abordagem de configuração.</span><span class="sxs-lookup"><span data-stu-id="1edaa-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="1edaa-106">A parte do procedimento que permite que o ponto de extremidade de serviço se torne habilitada para AJAX ASP.NET consiste em configurar o ponto de extremidade para usar o <xref:System.ServiceModel.WebHttpBinding> e adicione o [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="1edaa-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="1edaa-107">Depois de configurar o ponto de extremidade, as etapas para implementar e hospedar o serviço são semelhantes às usadas por qualquer serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="1edaa-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="1edaa-108">Para obter um exemplo de funcionamento, consulte o [serviço de AJAX usando o HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="1edaa-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="1edaa-109">Para obter mais informações sobre como configurar um ponto de extremidade do ASP.NET AJAX sem utilizar a configuração, consulte [como: Adicionar um ponto de extremidade do ASP.NET AJAX sem utilizar a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="1edaa-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="1edaa-110">Para criar um serviço WCF básico</span><span class="sxs-lookup"><span data-stu-id="1edaa-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="1edaa-111">Definir um contrato de serviço WCF básico com uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="1edaa-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="1edaa-112">Marcar cada operação com o <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1edaa-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="1edaa-113">Certifique-se de definir o <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="1edaa-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="1edaa-114">Implemente a `ICalculator` contrato de serviço com um `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="1edaa-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="1edaa-115">Definir um namespace para o `ICalculator` e `CalculatorService` implementações, encapsulando-as em um bloco de namespace.</span><span class="sxs-lookup"><span data-stu-id="1edaa-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="1edaa-116">Para criar um ponto de extremidade do ASP.NET AJAX para o serviço</span><span class="sxs-lookup"><span data-stu-id="1edaa-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="1edaa-117">Criar uma configuração de comportamento e especificar o [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento para pontos de extremidade habilitados para AJAX ASP.NET do serviço.</span><span class="sxs-lookup"><span data-stu-id="1edaa-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2. <span data-ttu-id="1edaa-118">Criar um ponto de extremidade para o serviço que usa o <xref:System.ServiceModel.WebHttpBinding> e o comportamento do AJAX ASP.NET definido na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="1edaa-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
### <a name="to-host-the-service-in-iis"></a><span data-ttu-id="1edaa-119">Para hospedar o serviço no IIS</span><span class="sxs-lookup"><span data-stu-id="1edaa-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="1edaa-120">Para hospedar o serviço no IIS, crie um novo arquivo chamado de serviço com uma extensão. svc no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1edaa-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="1edaa-121">Edite esse arquivo adicionando apropriado [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informações de diretiva para o serviço.</span><span class="sxs-lookup"><span data-stu-id="1edaa-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="1edaa-122">Por exemplo, o conteúdo no arquivo de serviço para o `CalculatorService` exemplo contém as informações a seguir.</span><span class="sxs-lookup"><span data-stu-id="1edaa-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="1edaa-123">Para obter mais informações sobre como hospedar no IIS, consulte [como: Hospedar um serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="1edaa-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="1edaa-124">Para chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="1edaa-124">To call the service</span></span>  
  
1. <span data-ttu-id="1edaa-125">O ponto de extremidade é configurado em um endereço relativo ao arquivo. svc, em branco para que o serviço agora está disponível e pode ser chamado enviando solicitações ao service.svc/\<operação > - por exemplo, service.svc/Add para o `Add` operação.</span><span class="sxs-lookup"><span data-stu-id="1edaa-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="1edaa-126">Você pode usá-lo inserindo a URL do ponto de extremidade para a coleção de Scripts do controle do Gerenciador de Script do AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1edaa-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="1edaa-127">Por exemplo, consulte o [serviço de AJAX usando o HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="1edaa-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1edaa-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1edaa-128">See also</span></span>

- [<span data-ttu-id="1edaa-129">Criando serviços WCF para o ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="1edaa-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="1edaa-130">Como: Migrar serviços Web do ASP.NET habilitado para AJAX para o WCF</span><span class="sxs-lookup"><span data-stu-id="1edaa-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
