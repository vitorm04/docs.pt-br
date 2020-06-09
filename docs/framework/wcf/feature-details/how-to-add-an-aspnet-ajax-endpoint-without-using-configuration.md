---
title: Como adicionar um ponto de extremidade de ASP.NET AJAX sem utilizar a configuração
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 9aab53d6457aa7848fd4acea6317a30da352cc98
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579625"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="36ff8-102">Como adicionar um ponto de extremidade de ASP.NET AJAX sem utilizar a configuração</span><span class="sxs-lookup"><span data-stu-id="36ff8-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="36ff8-103">Windows Communication Foundation (WCF) permite que você crie um serviço que expõe um ponto de extremidade habilitado para AJAX ASP.NET que pode ser chamado do JavaScript em um site de cliente.</span><span class="sxs-lookup"><span data-stu-id="36ff8-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="36ff8-104">Para criar esse ponto de extremidade, você pode usar um arquivo de configuração, assim como com todos os outros pontos de extremidade do WCF, ou usar um método que não exija nenhum elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="36ff8-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="36ff8-105">Este tópico demonstra a segunda abordagem.</span><span class="sxs-lookup"><span data-stu-id="36ff8-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="36ff8-106">Para criar serviços com pontos de extremidade do ASP.NET AJAX sem configuração, os serviços devem ser hospedados pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="36ff8-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="36ff8-107">Para ativar um ponto de extremidade ASP.NET AJAX usando essa abordagem, especifique o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> como o parâmetro Factory na diretiva [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) no arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="36ff8-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="36ff8-108">Essa fábrica personalizada é o componente que configura automaticamente um ponto de extremidade do ASP.NET AJAX para que ele possa ser chamado do JavaScript em um site do cliente.</span><span class="sxs-lookup"><span data-stu-id="36ff8-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="36ff8-109">Para obter um exemplo funcional, consulte o [serviço AJAX sem configuração](../samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="36ff8-109">For a working example, see the [AJAX Service Without Configuration](../samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="36ff8-110">Para obter uma descrição de como configurar um ponto de extremidade do ASP.NET AJAX usando elementos de configuração, consulte [como: usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="36ff8-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="36ff8-111">Para criar um serviço WCF básico</span><span class="sxs-lookup"><span data-stu-id="36ff8-111">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="36ff8-112">Defina um contrato de serviço WCF básico com uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="36ff8-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="36ff8-113">Marque cada operação com o <xref:System.ServiceModel.OperationContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="36ff8-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="36ff8-114">Certifique-se de definir a <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="36ff8-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="36ff8-115">Implemente o `ICalculator` contrato de serviço com um `CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="36ff8-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="36ff8-116">Defina um namespace para as `ICalculator` `CalculatorService` implementações e encapsulando-as em um bloco de namespace.</span><span class="sxs-lookup"><span data-stu-id="36ff8-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="36ff8-117">Para hospedar o serviço em Serviços de Informações da Internet sem configuração</span><span class="sxs-lookup"><span data-stu-id="36ff8-117">To host the service in Internet Information Services without configuration</span></span>  
  
1. <span data-ttu-id="36ff8-118">Crie um novo arquivo chamado Service com uma extensão. svc no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="36ff8-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="36ff8-119">Edite esse arquivo adicionando as informações de diretiva [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) apropriadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="36ff8-119">Edit this file by adding the appropriate [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="36ff8-120">Especifique que o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> deve ser usado na diretiva [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) para configurar automaticamente um ponto de extremidade do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="36ff8-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. <span data-ttu-id="36ff8-121">Crie o serviço e chame-o do cliente.</span><span class="sxs-lookup"><span data-stu-id="36ff8-121">Build the service and call it from the client.</span></span> <span data-ttu-id="36ff8-122">Serviços de Informações da Internet (IIS) ativa o serviço quando chamado.</span><span class="sxs-lookup"><span data-stu-id="36ff8-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="36ff8-123">Para obter mais informações sobre hospedagem no IIS, consulte [como hospedar um serviço WCF no IIS](how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="36ff8-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="36ff8-124">Para chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="36ff8-124">To call the service</span></span>  
  
1. <span data-ttu-id="36ff8-125">O ponto de extremidade é configurado em um endereço vazio relativo ao arquivo. svc, portanto, o serviço agora está disponível e pode ser invocado enviando solicitações para Service. svc/ \<operation> -por exemplo, Service. svc/Add para a `Add` operação.</span><span class="sxs-lookup"><span data-stu-id="36ff8-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="36ff8-126">Você pode usá-lo inserindo a URL do serviço na coleção de scripts do controle Gerenciador de script do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="36ff8-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="36ff8-127">Para obter um exemplo, consulte o [serviço AJAX sem configuração](../samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="36ff8-127">For an example, see the [AJAX Service Without Configuration](../samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="36ff8-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36ff8-128">Example</span></span>  
  
 <span data-ttu-id="36ff8-129">O ponto de extremidade configurado automaticamente é criado em um endereço vazio relativo à URL base.</span><span class="sxs-lookup"><span data-stu-id="36ff8-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="36ff8-130">Um arquivo de configuração também pode ser adicionado e usado com essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="36ff8-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="36ff8-131">Se o arquivo de configuração contiver definições de ponto de extremidade, esses pontos de extremidade serão adicionados ao ponto de extremidades configurado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="36ff8-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="36ff8-132">Por exemplo, o Service. svc usa o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> e o diretório de serviço contém um arquivo Web. config que define um ponto de extremidade para o mesmo serviço usando o <xref:System.ServiceModel.BasicHttpBinding> no endereço relativo "SOAP".</span><span class="sxs-lookup"><span data-stu-id="36ff8-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="36ff8-133">Nesse caso, o serviço contém dois pontos de extremidade: um no Service. svc (que responde às solicitações do AJAX ASP.NET) e outro em Service. svc/SOAP (que responde às solicitações SOAP).</span><span class="sxs-lookup"><span data-stu-id="36ff8-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="36ff8-134">Se o arquivo de configuração definir um ponto de extremidade em um endereço relativo vazio e o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for usado, uma exceção será lançada e o serviço não será iniciado.</span><span class="sxs-lookup"><span data-stu-id="36ff8-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="36ff8-135">Você não pode usar a configuração para modificar as configurações no ponto de extremidade configurado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="36ff8-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="36ff8-136">Se qualquer configuração (como uma cota de leitor) precisar ser modificada, você não deverá usar a abordagem sem configuração removendo o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> do arquivo. svc e criando uma entrada de configuração para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="36ff8-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="36ff8-137">Se o serviço exigir o modo de compatibilidade ASP.NET, por exemplo, se ele usar os <xref:System.Web.HttpContext> mecanismos de autorização de classe ou ASP.net, um arquivo de configuração ainda será necessário para ativar esse modo.</span><span class="sxs-lookup"><span data-stu-id="36ff8-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="36ff8-138">O elemento de configuração necessário é o [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) elemento, que deve ser adicionado da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="36ff8-138">The configuration element required is the [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="36ff8-139">Para obter mais informações, consulte o tópico [Serviços do WCF e ASP.net](wcf-services-and-aspnet.md) .</span><span class="sxs-lookup"><span data-stu-id="36ff8-139">For more information, see the [WCF Services and ASP.NET](wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="36ff8-140">A <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> classe é uma classe derivada de <xref:System.ServiceModel.Activation.ServiceHostFactory> .</span><span class="sxs-lookup"><span data-stu-id="36ff8-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="36ff8-141">Para obter uma explicação detalhada do mecanismo de fábrica do host de serviço, consulte o tópico [ampliando a hospedagem usando o ServiceHostFactory](../extending/extending-hosting-using-servicehostfactory.md) .</span><span class="sxs-lookup"><span data-stu-id="36ff8-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36ff8-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36ff8-142">See also</span></span>

- [<span data-ttu-id="36ff8-143">Criando serviços do WCF para o AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="36ff8-143">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="36ff8-144">Como migrar serviços habilitados para AJAX ASP.NET para o WCF</span><span class="sxs-lookup"><span data-stu-id="36ff8-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
