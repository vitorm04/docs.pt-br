---
title: Como utilizar a configuração para adicionar um ponto de extremidade AJAX ASP.NET
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 3ccfb34614707c17885da3ed37f545bbab808869
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978262"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="4ddd4-102">Como utilizar a configuração para adicionar um ponto de extremidade AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4ddd4-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="4ddd4-103">Windows Communication Foundation (WCF) permite que você crie um serviço que disponibiliza um ponto de extremidade habilitado para AJAX ASP.NET que pode ser chamado do JavaScript em um site de cliente.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="4ddd4-104">Para criar esse ponto de extremidade, você pode usar um arquivo de configuração, assim como com todos os outros pontos de extremidade do Windows Communication Foundation (WCF) ou usar um método que não exija nenhum elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="4ddd4-105">Este tópico demonstra a abordagem de configuração.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="4ddd4-106">A parte do procedimento que permite que o ponto de extremidade de serviço se torne ASP.NET habilitado para AJAX consiste em configurar o ponto de extremidade para usar a <xref:System.ServiceModel.WebHttpBinding> e adicionar o comportamento de ponto de extremidade [\<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) .</span><span class="sxs-lookup"><span data-stu-id="4ddd4-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="4ddd4-107">Depois de configurar o ponto de extremidade, as etapas para implementar e hospedar o serviço são semelhantes às usadas por qualquer serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="4ddd4-108">Para obter um exemplo funcional, consulte o [serviço AJAX usando http post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="4ddd4-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="4ddd4-109">Para obter mais informações sobre como configurar um ponto de extremidade do ASP.NET AJAX sem usar a configuração, consulte [como adicionar um ponto de extremidade do ASP.NET AJAX sem usar a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="4ddd4-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="4ddd4-110">Para criar um serviço WCF básico</span><span class="sxs-lookup"><span data-stu-id="4ddd4-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="4ddd4-111">Defina um contrato de serviço WCF básico com uma interface marcada com o atributo <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="4ddd4-112">Marque cada operação com a <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="4ddd4-113">Certifique-se de definir a propriedade <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="4ddd4-114">Implemente o contrato de serviço `ICalculator` com um `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }
        // Other operations omitted…
    }
    ```  
  
3. <span data-ttu-id="4ddd4-115">Defina um namespace para as implementações de `ICalculator` e `CalculatorService` encapsulando-as em um bloco de namespace.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="4ddd4-116">Para criar um ponto de extremidade do ASP.NET AJAX para o serviço</span><span class="sxs-lookup"><span data-stu-id="4ddd4-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="4ddd4-117">Crie uma configuração de comportamento e especifique o comportamento [\<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) para pontos de extremidade habilitados para AJAX ASP.net do serviço.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2. <span data-ttu-id="4ddd4-118">Crie um ponto de extremidade para o serviço que usa o <xref:System.ServiceModel.WebHttpBinding> e o comportamento ASP.NET AJAX definido na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="4ddd4-119">Para hospedar o serviço no IIS</span><span class="sxs-lookup"><span data-stu-id="4ddd4-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="4ddd4-120">Para hospedar o serviço no IIS, crie um novo arquivo chamado serviço com uma extensão. svc no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="4ddd4-121">Edite esse arquivo adicionando as informações de diretiva [ServiceHost do\@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) apropriadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="4ddd4-122">Por exemplo, o conteúdo no arquivo de serviço para o exemplo de `CalculatorService` contém as informações a seguir.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="4ddd4-123">Para obter mais informações sobre hospedagem no IIS, consulte [como hospedar um serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="4ddd4-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="4ddd4-124">Para chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="4ddd4-124">To call the service</span></span>  
  
1. <span data-ttu-id="4ddd4-125">O ponto de extremidade é configurado em um endereço vazio em relação ao arquivo. svc, portanto, o serviço agora está disponível e pode ser invocado enviando solicitações à operação Service. svc/\<>-por exemplo, Service. svc/Add para a operação `Add`.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="4ddd4-126">Você pode usá-lo inserindo a URL do ponto de extremidade na coleção de scripts do controle Gerenciador de script do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="4ddd4-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="4ddd4-127">Para obter um exemplo, consulte o [serviço AJAX usando http post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="4ddd4-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ddd4-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ddd4-128">See also</span></span>

- [<span data-ttu-id="4ddd4-129">Criando serviços WCF para o ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="4ddd4-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="4ddd4-130">Como migrar serviços Web do ASP.NET habilitados para AJAX para o WCF</span><span class="sxs-lookup"><span data-stu-id="4ddd4-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
