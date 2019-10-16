---
title: Configurando serviços WCF em código
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: c6bcf08511470d28e1087108d95e477683b0338b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320639"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="2dd44-102">Configurando serviços WCF em código</span><span class="sxs-lookup"><span data-stu-id="2dd44-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="2dd44-103">Windows Communication Foundation (WCF) permite que os desenvolvedores configurem serviços usando arquivos de configuração ou código.</span><span class="sxs-lookup"><span data-stu-id="2dd44-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="2dd44-104">Os arquivos de configuração são úteis quando um serviço precisa ser configurado depois de ser implantado.</span><span class="sxs-lookup"><span data-stu-id="2dd44-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="2dd44-105">Ao usar arquivos de configuração, um profissional de TI apenas precisa atualizar o arquivo de configuração, nenhuma recompilação é necessária.</span><span class="sxs-lookup"><span data-stu-id="2dd44-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="2dd44-106">Os arquivos de configuração, porém, podem ser complexos e difíceis de manter.</span><span class="sxs-lookup"><span data-stu-id="2dd44-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="2dd44-107">Não há suporte para depurar arquivos de configuração e os elementos de configuração são referenciados por nomes, o que torna os arquivos de configuração de criação sujeitos a erros e difíceis.</span><span class="sxs-lookup"><span data-stu-id="2dd44-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="2dd44-108">O WCF também permite que você configure serviços no código.</span><span class="sxs-lookup"><span data-stu-id="2dd44-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="2dd44-109">Em versões anteriores do WCF (4,0 e anteriores) a configuração de serviços no código era fácil em cenários de hospedagem interna, a classe <xref:System.ServiceModel.ServiceHost> permitia configurar pontos de extremidade e comportamentos antes de chamar ServiceHost. Open.</span><span class="sxs-lookup"><span data-stu-id="2dd44-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="2dd44-110">No entanto, em cenários hospedados na Web, você não tem acesso direto à classe <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="2dd44-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="2dd44-111">Para configurar um serviço Web hospedado, você precisava criar um `System.ServiceModel.ServiceHostFactory` que criou o <xref:System.ServiceModel.Activation.ServiceHostFactory> e executar qualquer configuração necessária.</span><span class="sxs-lookup"><span data-stu-id="2dd44-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="2dd44-112">A partir do .NET 4,5, o WCF fornece uma maneira mais fácil de configurar os serviços hospedados internamente e Web no código.</span><span class="sxs-lookup"><span data-stu-id="2dd44-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="2dd44-113">O método Configure</span><span class="sxs-lookup"><span data-stu-id="2dd44-113">The Configure method</span></span>  
 <span data-ttu-id="2dd44-114">Basta definir um método estático público chamado `Configure` com a seguinte assinatura em sua classe de implementação de serviço:</span><span class="sxs-lookup"><span data-stu-id="2dd44-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="2dd44-115">O método configure usa uma instância <xref:System.ServiceModel.ServiceConfiguration> que permite ao desenvolvedor adicionar pontos de extremidade e comportamentos.</span><span class="sxs-lookup"><span data-stu-id="2dd44-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="2dd44-116">Esse método é chamado pelo WCF antes de o host de serviço ser aberto.</span><span class="sxs-lookup"><span data-stu-id="2dd44-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="2dd44-117">Quando definido, quaisquer definições de configuração de serviço especificadas em um arquivo app. config ou Web. config serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="2dd44-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="2dd44-118">O trecho de código a seguir ilustra como definir o método `Configure` e adicionar um ponto de extremidade de serviço, um comportamento de ponto de extremidade e comportamentos de serviço:</span><span class="sxs-lookup"><span data-stu-id="2dd44-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return $"You entered: {value}";
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 <span data-ttu-id="2dd44-119">Para habilitar um protocolo como o HTTPS para um serviço, você pode adicionar explicitamente um ponto de extremidade que usa o protocolo ou pode adicionar pontos de extremidades automaticamente chamando EnableProtocol (Binding), que adiciona um ponto de extremidade para cada endereço base compatível com o protocolo e cada contrato de serviço definido.</span><span class="sxs-lookup"><span data-stu-id="2dd44-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="2dd44-120">O código a seguir ilustra como usar o método imconfiguration. EnableProtocol:</span><span class="sxs-lookup"><span data-stu-id="2dd44-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable "Add Service Reference" support   
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });   
       // set up support for http, https, net.tcp, net.pipe   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 <span data-ttu-id="2dd44-121">As configurações na seção < `protocolMappings` > só serão usadas se nenhum ponto de extremidade do aplicativo for adicionado ao <xref:System.ServiceModel.ServiceConfiguration> programaticamente. Opcionalmente, você pode carregar a configuração de serviço do arquivo de configuração de aplicativo padrão chamando <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> e, em seguida, alterar as configurações.</span><span class="sxs-lookup"><span data-stu-id="2dd44-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="2dd44-122">A classe <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> também permite que você carregue a configuração de uma configuração centralizada.</span><span class="sxs-lookup"><span data-stu-id="2dd44-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="2dd44-123">O código a seguir ilustra como implementar isso:</span><span class="sxs-lookup"><span data-stu-id="2dd44-123">The following code illustrates how to implement this:</span></span>  
  
```csharp
public class Service1 : IService1   
{   
    public void DoWork();   
    public static void Configure(ServiceConfiguration config)   
    {   
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));   
    }   
}  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="2dd44-124">Observe que <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignora < configurações `host` > na marca < `service` > de < `system.serviceModel` >.</span><span class="sxs-lookup"><span data-stu-id="2dd44-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="2dd44-125">Conceitualmente, < `host` > é sobre a configuração do host, não a configuração do serviço e é carregada antes de o método configure ser executado.</span><span class="sxs-lookup"><span data-stu-id="2dd44-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd44-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2dd44-126">See also</span></span>

- [<span data-ttu-id="2dd44-127">Configurando serviços usando arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="2dd44-127">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="2dd44-128">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="2dd44-128">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
- [<span data-ttu-id="2dd44-129">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="2dd44-129">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="2dd44-130">Configuração</span><span class="sxs-lookup"><span data-stu-id="2dd44-130">Configuration</span></span>](./samples/configuration-sample.md)
- [<span data-ttu-id="2dd44-131">Ativação baseada em configuração no IIS e WAS</span><span class="sxs-lookup"><span data-stu-id="2dd44-131">Configuration-Based Activation in IIS and WAS</span></span>](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [<span data-ttu-id="2dd44-132">Configuração e suporte a metadados</span><span class="sxs-lookup"><span data-stu-id="2dd44-132">Configuration and Metadata Support</span></span>](./extending/configuration-and-metadata-support.md)
- [<span data-ttu-id="2dd44-133">Configuração</span><span class="sxs-lookup"><span data-stu-id="2dd44-133">Configuration</span></span>](./diagnostics/exceptions-reference/configuration.md)
- [<span data-ttu-id="2dd44-134">Como especificar uma associação de serviço na configuração</span><span class="sxs-lookup"><span data-stu-id="2dd44-134">How to: Specify a Service Binding in Configuration</span></span>](how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="2dd44-135">Como criar um ponto de extremidade de serviço na configuração</span><span class="sxs-lookup"><span data-stu-id="2dd44-135">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="2dd44-136">Como publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="2dd44-136">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="2dd44-137">Como especificar uma associação de cliente na configuração</span><span class="sxs-lookup"><span data-stu-id="2dd44-137">How to: Specify a Client Binding in Configuration</span></span>](how-to-specify-a-client-binding-in-configuration.md)
