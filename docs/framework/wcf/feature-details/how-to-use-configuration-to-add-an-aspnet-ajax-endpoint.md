---
title: Como utilizar a configuração para adicionar um ponto de extremidade AJAX ASP.NET
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 5314bb000371ee2d3eef2576e1edfa455aa65b90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184831"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="6da85-102">Como utilizar a configuração para adicionar um ponto de extremidade AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6da85-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="6da85-103">O Windows Communication Foundation (WCF) permite que você crie um serviço que disponibilize um ponto final habilitado para ASP.NET AJAX que pode ser chamado de JavaScript em um site da Web do cliente.</span><span class="sxs-lookup"><span data-stu-id="6da85-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="6da85-104">Para criar tal ponto final, você pode usar um arquivo de configuração, como com todos os outros pontos finais do Windows Communication Foundation (WCF) ou usar um método que não exija nenhum elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="6da85-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="6da85-105">Este tópico demonstra a abordagem de configuração.</span><span class="sxs-lookup"><span data-stu-id="6da85-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="6da85-106">A parte do procedimento que permite que o ponto final do serviço se torne ASP.NET <xref:System.ServiceModel.WebHttpBinding> habilitado para AJAX consiste em configurar o ponto final para usar o e adicionar o [ \<ambienteWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento de ponto final.</span><span class="sxs-lookup"><span data-stu-id="6da85-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="6da85-107">Após a configuração do ponto final, as etapas para implementar e hospedar o serviço são semelhantes às usadas por qualquer serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="6da85-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="6da85-108">Para obter um exemplo de trabalho, consulte o [serviço AJAX usando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="6da85-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="6da85-109">Para obter mais informações sobre como configurar um ponto final ASP.NET AJAX sem usar a configuração, consulte [Como: Adicionar um ASP.NET endpoint AJAX sem usar a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="6da85-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="6da85-110">Para criar um serviço básico wcf</span><span class="sxs-lookup"><span data-stu-id="6da85-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="6da85-111">Defina um contrato básico de serviço <xref:System.ServiceModel.ServiceContractAttribute> WCF com uma interface marcada com o atributo.</span><span class="sxs-lookup"><span data-stu-id="6da85-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="6da85-112">Marque cada <xref:System.ServiceModel.OperationContractAttribute>operação com o .</span><span class="sxs-lookup"><span data-stu-id="6da85-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="6da85-113">Certifique-se de <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> definir a propriedade.</span><span class="sxs-lookup"><span data-stu-id="6da85-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="6da85-114">Implementar `ICalculator` o contrato `CalculatorService`de serviço com um .</span><span class="sxs-lookup"><span data-stu-id="6da85-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
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
  
3. <span data-ttu-id="6da85-115">Defina um namespace para as `ICalculator` implementações e `CalculatorService` embrulhe-os em um bloco de namespace.</span><span class="sxs-lookup"><span data-stu-id="6da85-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="6da85-116">Para criar um ponto final ASP.NET AJAX para o serviço</span><span class="sxs-lookup"><span data-stu-id="6da85-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="6da85-117">Crie uma configuração [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) de comportamento e especifique o comportamento de>do WebScript para ASP.NET pontos finais habilitados para AJAX do serviço.</span><span class="sxs-lookup"><span data-stu-id="6da85-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2. <span data-ttu-id="6da85-118">Crie um ponto final para <xref:System.ServiceModel.WebHttpBinding> o serviço que usa o ASP.NET comportamento AJAX definido na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="6da85-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="6da85-119">Para hospedar o serviço no IIS</span><span class="sxs-lookup"><span data-stu-id="6da85-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="6da85-120">Para hospedar o serviço no IIS, crie um novo serviço chamado de arquivo com uma extensão .svc no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6da85-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="6da85-121">Edite este arquivo adicionando as informações [ \@diretivas serviceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) apropriadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="6da85-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="6da85-122">Por exemplo, o conteúdo no `CalculatorService` arquivo de serviço para a amostra contém as seguintes informações.</span><span class="sxs-lookup"><span data-stu-id="6da85-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="6da85-123">Para obter mais informações sobre hospedagem no IIS, consulte [Como hospedar um Serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="6da85-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="6da85-124">Para chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="6da85-124">To call the service</span></span>  
  
1. <span data-ttu-id="6da85-125">O ponto final está configurado em um endereço vazio em relação ao arquivo .svc, de modo que o\<serviço já está disponível e pode `Add` ser invocado enviando solicitações para service.svc/operation> - por exemplo, service.svc/Add para a operação.</span><span class="sxs-lookup"><span data-stu-id="6da85-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="6da85-126">Você pode usá-lo inserindo a URL de ponto final na coleção Scripts do ASP.NET controle do Gerenciador de Scripts AJAX.</span><span class="sxs-lookup"><span data-stu-id="6da85-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="6da85-127">Por exemplo, consulte o [serviço AJAX usando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="6da85-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6da85-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="6da85-128">See also</span></span>

- [<span data-ttu-id="6da85-129">Criando serviços do WCF para o AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6da85-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="6da85-130">Como migrar serviços habilitados para AJAX ASP.NET para o WCF</span><span class="sxs-lookup"><span data-stu-id="6da85-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
