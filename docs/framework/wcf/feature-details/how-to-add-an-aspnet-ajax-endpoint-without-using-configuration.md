---
title: Como adicionar um ponto de extremidade de ASP.NET AJAX sem utilizar a configuração
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 18c02644319dd9d11be39ac4956a4dcf50db3078
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43470782"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="b1451-102">Como adicionar um ponto de extremidade de ASP.NET AJAX sem utilizar a configuração</span><span class="sxs-lookup"><span data-stu-id="b1451-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="b1451-103">Windows Communication Foundation (WCF) permite que você crie um serviço que expõe um ponto de extremidade habilitados para AJAX ASP.NET que pode ser chamado do JavaScript em um site do cliente.</span><span class="sxs-lookup"><span data-stu-id="b1451-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="b1451-104">Para criar um ponto de extremidade, você pode usar um arquivo de configuração, assim como acontece com todos os outros pontos de extremidade do WCF ou usar um método que não requer quaisquer elementos de configuração.</span><span class="sxs-lookup"><span data-stu-id="b1451-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="b1451-105">Este tópico demonstra a segunda abordagem.</span><span class="sxs-lookup"><span data-stu-id="b1451-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="b1451-106">Para criar serviços com pontos de extremidade do ASP.NET AJAX sem configuração, os serviços devem ser hospedados pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="b1451-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="b1451-107">Para ativar um ponto de extremidade do ASP.NET AJAX usando essa abordagem, especifique o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> como o parâmetro de fábrica na [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva no arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="b1451-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="b1451-108">Esta fábrica personalizada é o componente que configura automaticamente um ponto de extremidade do ASP.NET AJAX para que ele pode ser chamado do JavaScript em um site do cliente.</span><span class="sxs-lookup"><span data-stu-id="b1451-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="b1451-109">Para obter um exemplo de funcionamento, consulte o [serviço de AJAX sem configuração](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="b1451-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="b1451-110">Para obter uma descrição de como configurar um ponto de extremidade do ASP.NET AJAX usando elementos de configuração, consulte [como: usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="b1451-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="b1451-111">Para criar um serviço WCF básico</span><span class="sxs-lookup"><span data-stu-id="b1451-111">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="b1451-112">Definir um contrato de serviço WCF básico com uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="b1451-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="b1451-113">Marcar cada operação com o <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b1451-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="b1451-114">Certifique-se de definir o <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b1451-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  <span data-ttu-id="b1451-115">Implemente a `ICalculator` contrato de serviço com um `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="b1451-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="b1451-116">Definir um namespace para o `ICalculator` e `CalculatorService` implementações, encapsulando-as em um bloco de namespace.</span><span class="sxs-lookup"><span data-stu-id="b1451-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="b1451-117">Para hospedar o serviço nos serviços de informações da Internet sem configuração</span><span class="sxs-lookup"><span data-stu-id="b1451-117">To host the service in Internet Information Services without configuration</span></span>  
  
1.  <span data-ttu-id="b1451-118">Crie um novo arquivo chamado de serviço com uma extensão. svc no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1451-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="b1451-119">Edite esse arquivo adicionando apropriado [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informações de diretiva para o serviço.</span><span class="sxs-lookup"><span data-stu-id="b1451-119">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="b1451-120">Especificar que o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> deve ser usada em de [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva para configurar automaticamente um ponto de extremidade do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="b1451-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  <span data-ttu-id="b1451-121">O serviço de compilação e chamá-lo a partir do cliente.</span><span class="sxs-lookup"><span data-stu-id="b1451-121">Build the service and call it from the client.</span></span> <span data-ttu-id="b1451-122">Serviços de informações da Internet (IIS) ativa o serviço quando chamado.</span><span class="sxs-lookup"><span data-stu-id="b1451-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="b1451-123">Para obter mais informações sobre como hospedar no IIS, consulte [como: hospedar um serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="b1451-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="b1451-124">Para chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="b1451-124">To call the service</span></span>  
  
1.  <span data-ttu-id="b1451-125">O ponto de extremidade é configurado em um endereço relativo ao arquivo. svc, em branco para que o serviço agora está disponível e pode ser chamado enviando solicitações ao service.svc/\<operação > - por exemplo, service.svc/Add para o `Add` operação.</span><span class="sxs-lookup"><span data-stu-id="b1451-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="b1451-126">Você pode usá-lo inserindo a URL do serviço para a coleção de Scripts do controle do Gerenciador de Script do AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b1451-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="b1451-127">Por exemplo, consulte o [serviço de AJAX sem configuração](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="b1451-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1451-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1451-128">Example</span></span>  
  
 <span data-ttu-id="b1451-129">O ponto de extremidade configurado automaticamente é criado em um endereço em branco em relação a URL base.</span><span class="sxs-lookup"><span data-stu-id="b1451-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="b1451-130">Um arquivo de configuração também pode ser adicionado e usado com essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="b1451-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="b1451-131">Se o arquivo de configuração contém as definições de ponto de extremidade, esses pontos de extremidade são adicionados ao ponto de extremidade configurado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b1451-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="b1451-132">Por exemplo, SVC usa o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> e o diretório de serviço contém um arquivo Web. config que define um ponto de extremidade para o mesmo serviço usando o <xref:System.ServiceModel.BasicHttpBinding> no endereço relativo "soap".</span><span class="sxs-lookup"><span data-stu-id="b1451-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="b1451-133">Nesse caso, o serviço contém dois pontos de extremidade: um de cada SVC (que responde às solicitações do ASP.NET AJAX) e outro no service.svc/soap (que responde às solicitações SOAP).</span><span class="sxs-lookup"><span data-stu-id="b1451-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="b1451-134">Se o arquivo de configuração define um ponto de extremidade em um endereço relativo vazio e o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> é usado, uma exceção é lançada e o serviço não for iniciado.</span><span class="sxs-lookup"><span data-stu-id="b1451-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="b1451-135">Você não pode usar a configuração para modificar as configurações no ponto de extremidade configurado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b1451-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="b1451-136">Se qualquer configuração (por exemplo, uma cota do leitor) deve ser modificado, você não deve usar a abordagem sem configuração, removendo o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> do arquivo. svc e criando uma entrada de configuração para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b1451-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="b1451-137">Se seu serviço requer o modo de compatibilidade do ASP.NET - por exemplo, se ele usa o <xref:System.Web.HttpContext> classe ou mecanismos de autorização do ASP.NET - um arquivo de configuração ainda é necessário para ativar esse modo.</span><span class="sxs-lookup"><span data-stu-id="b1451-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="b1451-138">O elemento de configuração necessário é a [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) elemento, que deve ser adicionado da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="b1451-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="b1451-139">Para obter mais informações, consulte o [serviços WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="b1451-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="b1451-140">O <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> classe é uma classe derivada de <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="b1451-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="b1451-141">Para obter uma explicação detalhada do mecanismo de fábrica do host de serviço, consulte o [estendendo hospedagem usando ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="b1451-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1451-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1451-142">See Also</span></span>  
 [<span data-ttu-id="b1451-143">Criando serviços WCF para o ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="b1451-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="b1451-144">Como migrar serviços Web do ASP.NET habilitados para AJAX para o WCF</span><span class="sxs-lookup"><span data-stu-id="b1451-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
