---
title: 'Como: adicionar um ponto de extremidade de ASP.NET AJAX sem utilizar a configuração'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 4a7ff48e529ab58c8744edea22d52ad12a4d7b96
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895082"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="2425b-102">Como: adicionar um ponto de extremidade de ASP.NET AJAX sem utilizar a configuração</span><span class="sxs-lookup"><span data-stu-id="2425b-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="2425b-103">Windows Communication Foundation (WCF) permite que você crie um serviço que expõe um ponto de extremidade habilitado para AJAX ASP.NET que pode ser chamado do JavaScript em um site de cliente.</span><span class="sxs-lookup"><span data-stu-id="2425b-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="2425b-104">Para criar esse ponto de extremidade, você pode usar um arquivo de configuração, assim como com todos os outros pontos de extremidade do WCF, ou usar um método que não exija nenhum elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="2425b-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="2425b-105">Este tópico demonstra a segunda abordagem.</span><span class="sxs-lookup"><span data-stu-id="2425b-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="2425b-106">Para criar serviços com pontos de extremidade do ASP.NET AJAX sem configuração, os serviços devem ser hospedados pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="2425b-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="2425b-107">Para ativar um ponto de extremidade ASP.NET AJAX usando essa abordagem, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> especifique o como o parâmetro Factory [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) na diretiva ServiceHost no arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="2425b-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="2425b-108">Essa fábrica personalizada é o componente que configura automaticamente um ponto de extremidade do ASP.NET AJAX para que ele possa ser chamado do JavaScript em um site do cliente.</span><span class="sxs-lookup"><span data-stu-id="2425b-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="2425b-109">Para obter um exemplo funcional, consulte o [serviço AJAX sem configuração](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="2425b-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="2425b-110">Para obter uma descrição de como configurar um ponto de extremidade do ASP.NET AJAX usando elementos [de configuração, consulte Como: Use a configuração para adicionar um ponto de](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)extremidade do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="2425b-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="2425b-111">Para criar um serviço WCF básico</span><span class="sxs-lookup"><span data-stu-id="2425b-111">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="2425b-112">Defina um contrato de serviço WCF básico com uma interface marcada com <xref:System.ServiceModel.ServiceContractAttribute> o atributo.</span><span class="sxs-lookup"><span data-stu-id="2425b-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="2425b-113">Marque cada operação com o <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2425b-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="2425b-114">Certifique-se de definir <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> a propriedade.</span><span class="sxs-lookup"><span data-stu-id="2425b-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="2425b-115">Implemente `ICalculator` o contrato de serviço `CalculatorService`com um.</span><span class="sxs-lookup"><span data-stu-id="2425b-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="2425b-116">Defina um namespace para as `ICalculator` implementações e `CalculatorService` encapsulando-as em um bloco de namespace.</span><span class="sxs-lookup"><span data-stu-id="2425b-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="2425b-117">Para hospedar o serviço em Serviços de Informações da Internet sem configuração</span><span class="sxs-lookup"><span data-stu-id="2425b-117">To host the service in Internet Information Services without configuration</span></span>  
  
1. <span data-ttu-id="2425b-118">Crie um novo arquivo chamado Service com uma extensão. svc no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2425b-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="2425b-119">Edite esse arquivo adicionando as informações de diretiva [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) apropriadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="2425b-119">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="2425b-120">Especifique que o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> deve ser usado [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) na diretiva ServiceHost para configurar automaticamente um ponto de extremidade do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="2425b-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```text
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. <span data-ttu-id="2425b-121">Crie o serviço e chame-o do cliente.</span><span class="sxs-lookup"><span data-stu-id="2425b-121">Build the service and call it from the client.</span></span> <span data-ttu-id="2425b-122">Serviços de Informações da Internet (IIS) ativa o serviço quando chamado.</span><span class="sxs-lookup"><span data-stu-id="2425b-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="2425b-123">Para obter mais informações sobre hospedagem no IIS, [consulte Como: Hospede um serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="2425b-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="2425b-124">Para chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="2425b-124">To call the service</span></span>  
  
1. <span data-ttu-id="2425b-125">O ponto de extremidade é configurado em um endereço vazio relativo ao arquivo. svc, portanto, o serviço agora está disponível e pode ser invocado enviando solicitações para Service.\<svc/operation >-por exemplo, Service. svc/Add `Add` para a operação.</span><span class="sxs-lookup"><span data-stu-id="2425b-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="2425b-126">Você pode usá-lo inserindo a URL do serviço na coleção de scripts do controle Gerenciador de script do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="2425b-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="2425b-127">Para obter um exemplo, consulte o [serviço AJAX sem configuração](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="2425b-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2425b-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2425b-128">Example</span></span>  
  
 <span data-ttu-id="2425b-129">O ponto de extremidade configurado automaticamente é criado em um endereço vazio relativo à URL base.</span><span class="sxs-lookup"><span data-stu-id="2425b-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="2425b-130">Um arquivo de configuração também pode ser adicionado e usado com essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="2425b-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="2425b-131">Se o arquivo de configuração contiver definições de ponto de extremidade, esses pontos de extremidade serão adicionados ao ponto de extremidades configurado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="2425b-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="2425b-132">Por exemplo, o Service. svc usa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> o e o diretório de serviço contém um arquivo Web. config que define um ponto de extremidade para o <xref:System.ServiceModel.BasicHttpBinding> mesmo serviço usando o no endereço relativo "SOAP".</span><span class="sxs-lookup"><span data-stu-id="2425b-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="2425b-133">Nesse caso, o serviço contém dois pontos de extremidade: um no Service. svc (que responde às solicitações do AJAX ASP.NET) e outro em Service. svc/SOAP (que responde às solicitações SOAP).</span><span class="sxs-lookup"><span data-stu-id="2425b-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="2425b-134">Se o arquivo de configuração definir um ponto de extremidade em um endereço relativo <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> vazio e o for usado, uma exceção será lançada e o serviço não será iniciado.</span><span class="sxs-lookup"><span data-stu-id="2425b-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="2425b-135">Você não pode usar a configuração para modificar as configurações no ponto de extremidade configurado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="2425b-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="2425b-136">Se qualquer configuração (como uma cota de leitor) precisar ser modificada, você não deverá usar a abordagem sem configuração removendo o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> do arquivo. svc e criando uma entrada de configuração para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2425b-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="2425b-137">Se o serviço exigir o modo de compatibilidade ASP.net, por exemplo, se ele <xref:System.Web.HttpContext> usar os mecanismos de autorização de classe ou ASP.net, um arquivo de configuração ainda será necessário para ativar esse modo.</span><span class="sxs-lookup"><span data-stu-id="2425b-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="2425b-138">O elemento de configuração necessário é o elemento [ \<> do ServiceHostingEnvironment](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) , que deve ser adicionado da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="2425b-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="2425b-139">Para obter mais informações, consulte o tópico [Serviços do WCF e ASP.net](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) .</span><span class="sxs-lookup"><span data-stu-id="2425b-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="2425b-140">A <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> classe é uma classe derivada de <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="2425b-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="2425b-141">Para obter uma explicação detalhada do mecanismo de fábrica do host de serviço, consulte o tópico [ampliando a hospedagem usando o ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) .</span><span class="sxs-lookup"><span data-stu-id="2425b-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2425b-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2425b-142">See also</span></span>

- [<span data-ttu-id="2425b-143">Criando serviços WCF para o ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="2425b-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="2425b-144">Como: Migrar serviços Web do ASP.NET habilitados para AJAX para o WCF</span><span class="sxs-lookup"><span data-stu-id="2425b-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
