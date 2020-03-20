---
title: Como adicionar um ponto de extremidade de ASP.NET AJAX sem utilizar a configuração
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 9935e2a7738796fff9a037b09237a6acbf7bf988
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185129"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="402a5-102">Como adicionar um ponto de extremidade de ASP.NET AJAX sem utilizar a configuração</span><span class="sxs-lookup"><span data-stu-id="402a5-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="402a5-103">O Windows Communication Foundation (WCF) permite que você crie um serviço que exponha um ponto final ASP.NET habilitado para AJAX que pode ser chamado de JavaScript em um site do cliente.</span><span class="sxs-lookup"><span data-stu-id="402a5-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="402a5-104">Para criar tal ponto final, você pode usar um arquivo de configuração, como com todos os outros pontos finais do WCF, ou usar um método que não exija nenhum elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="402a5-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="402a5-105">Este tópico demonstra a segunda abordagem.</span><span class="sxs-lookup"><span data-stu-id="402a5-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="402a5-106">Para criar serviços com ASP.NET pontos finais do AJAX sem configuração, os serviços devem ser hospedados pelos Serviços de Informação da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="402a5-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="402a5-107">Para ativar um ponto final ASP.NET AJAX <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> usando essa abordagem, especifique como parâmetro de fábrica na diretiva [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) no arquivo .svc.</span><span class="sxs-lookup"><span data-stu-id="402a5-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="402a5-108">Esta fábrica personalizada é o componente que configura automaticamente um ponto final ASP.NET AJAX para que ele possa ser chamado de JavaScript em um site da Web do cliente.</span><span class="sxs-lookup"><span data-stu-id="402a5-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="402a5-109">Para um exemplo de trabalho, consulte o [serviço AJAX sem configuração](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="402a5-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="402a5-110">Para obter um esboço de como configurar um ponto final ASP.NET AJAX usando elementos de configuração, consulte [Como: Usar configuração para adicionar um ponto final ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="402a5-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="402a5-111">Para criar um serviço básico wcf</span><span class="sxs-lookup"><span data-stu-id="402a5-111">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="402a5-112">Defina um contrato básico de serviço <xref:System.ServiceModel.ServiceContractAttribute> WCF com uma interface marcada com o atributo.</span><span class="sxs-lookup"><span data-stu-id="402a5-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="402a5-113">Marque cada <xref:System.ServiceModel.OperationContractAttribute>operação com o .</span><span class="sxs-lookup"><span data-stu-id="402a5-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="402a5-114">Certifique-se de <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> definir a propriedade.</span><span class="sxs-lookup"><span data-stu-id="402a5-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="402a5-115">Implementar `ICalculator` o contrato `CalculatorService`de serviço com um .</span><span class="sxs-lookup"><span data-stu-id="402a5-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="402a5-116">Defina um namespace para as `ICalculator` implementações e `CalculatorService` embrulhe-os em um bloco de namespace.</span><span class="sxs-lookup"><span data-stu-id="402a5-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="402a5-117">Para hospedar o serviço em Serviços de Informação da Internet sem configuração</span><span class="sxs-lookup"><span data-stu-id="402a5-117">To host the service in Internet Information Services without configuration</span></span>  
  
1. <span data-ttu-id="402a5-118">Crie um novo serviço chamado de arquivo com uma extensão .svc no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="402a5-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="402a5-119">Edite este arquivo adicionando as informações [ \@diretivas serviceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) apropriadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="402a5-119">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="402a5-120">Especifique se o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> é usado na [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva ServiceHost para configurar automaticamente um ponto final ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="402a5-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. <span data-ttu-id="402a5-121">Construa o serviço e chame-o do cliente.</span><span class="sxs-lookup"><span data-stu-id="402a5-121">Build the service and call it from the client.</span></span> <span data-ttu-id="402a5-122">O Internet Information Services (IIS) ativa o serviço quando chamado.</span><span class="sxs-lookup"><span data-stu-id="402a5-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="402a5-123">Para obter mais informações sobre hospedagem no IIS, consulte [Como hospedar um Serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="402a5-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="402a5-124">Para chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="402a5-124">To call the service</span></span>  
  
1. <span data-ttu-id="402a5-125">O ponto final está configurado em um endereço vazio em relação ao arquivo .svc, de modo que o\<serviço já está disponível e pode `Add` ser invocado enviando solicitações para service.svc/operation> - por exemplo, service.svc/Add para a operação.</span><span class="sxs-lookup"><span data-stu-id="402a5-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="402a5-126">Você pode usá-lo inserindo a URL de serviço na coleção Scripts do ASP.NET controle do Gerenciador de Scripts AJAX.</span><span class="sxs-lookup"><span data-stu-id="402a5-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="402a5-127">Por exemplo, consulte o [serviço AJAX sem configuração](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="402a5-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="402a5-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="402a5-128">Example</span></span>  
  
 <span data-ttu-id="402a5-129">O ponto final configurado automaticamente é criado em um endereço vazio em relação à URL base.</span><span class="sxs-lookup"><span data-stu-id="402a5-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="402a5-130">Um arquivo de configuração também pode ser adicionado e usado com essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="402a5-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="402a5-131">Se o arquivo de configuração contiver definições de ponto final, esses pontos finais serão adicionados ao ponto final configurado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="402a5-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="402a5-132">Por exemplo, service.svc <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> usa o diretório e o diretório de serviço contém um arquivo Web.config que define um ponto final para o mesmo serviço usando o <xref:System.ServiceModel.BasicHttpBinding> endereço relativo "sabão".</span><span class="sxs-lookup"><span data-stu-id="402a5-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="402a5-133">Neste caso, o serviço contém dois pontos finais: um no service.svc (que responde a pedidos de ASP.NET AJAX) e outro em service.svc/soap (que responde a solicitações SOAP).</span><span class="sxs-lookup"><span data-stu-id="402a5-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="402a5-134">Se o arquivo de configuração definir um ponto <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> final em um endereço relativo vazio e for usado, uma exceção será lançada e o serviço não será acionado.</span><span class="sxs-lookup"><span data-stu-id="402a5-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="402a5-135">Não é possível usar a configuração para modificar as configurações no ponto final configurado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="402a5-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="402a5-136">Se qualquer configuração (como uma cota de leitor) for modificada, você <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> não deve usar a abordagem sem configuração removendo o arquivo .svc e criando uma entrada de configuração para o ponto final.</span><span class="sxs-lookup"><span data-stu-id="402a5-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="402a5-137">Se o seu serviço exigir ASP.NET modo de <xref:System.Web.HttpContext> compatibilidade - por exemplo, se ele usa os mecanismos de autorização de classe ou ASP.NET - um arquivo de configuração ainda é necessário para ativar este modo.</span><span class="sxs-lookup"><span data-stu-id="402a5-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="402a5-138">O elemento de configuração necessário é o [ \<elemento serviceHostingEnvironment>,](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) que deve ser adicionado da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="402a5-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="402a5-139">Para obter mais informações, consulte o tópico [WCF Services e ASP.NET.](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)</span><span class="sxs-lookup"><span data-stu-id="402a5-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="402a5-140">A <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> classe é uma <xref:System.ServiceModel.Activation.ServiceHostFactory>classe derivada de .</span><span class="sxs-lookup"><span data-stu-id="402a5-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="402a5-141">Para obter uma explicação detalhada do mecanismo de fábrica do host de serviço, consulte o tópico [Extensão da hospedagem usando serviceHostFactory.](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)</span><span class="sxs-lookup"><span data-stu-id="402a5-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="402a5-142">Confira também</span><span class="sxs-lookup"><span data-stu-id="402a5-142">See also</span></span>

- [<span data-ttu-id="402a5-143">Criando serviços do WCF para o AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="402a5-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="402a5-144">Como migrar serviços habilitados para AJAX ASP.NET para o WCF</span><span class="sxs-lookup"><span data-stu-id="402a5-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
