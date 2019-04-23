---
title: Configurando serviços WCF em código
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 8a1eeff76b02315143fb7b50ccc41aa18bb9eb0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225697"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="ed289-102">Configurando serviços WCF em código</span><span class="sxs-lookup"><span data-stu-id="ed289-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="ed289-103">Windows Communication Foundation (WCF) permite que os desenvolvedores configurem serviços usando arquivos de configuração ou código.</span><span class="sxs-lookup"><span data-stu-id="ed289-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="ed289-104">Os arquivos de configuração são úteis quando um serviço precisa ser configurado depois de ser implantado.</span><span class="sxs-lookup"><span data-stu-id="ed289-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="ed289-105">Ao usar arquivos de configuração, um profissional de TI apenas precisa atualizar o arquivo de configuração, nenhuma recompilação é necessária.</span><span class="sxs-lookup"><span data-stu-id="ed289-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="ed289-106">Os arquivos de configuração, porém, podem ser complexos e difíceis de manter.</span><span class="sxs-lookup"><span data-stu-id="ed289-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="ed289-107">Não há suporte para depurar arquivos de configuração e os elementos de configuração são referenciados por nomes, o que torna os arquivos de configuração de criação sujeitos a erros e difíceis.</span><span class="sxs-lookup"><span data-stu-id="ed289-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="ed289-108">O WCF também permite configurar serviços no código.</span><span class="sxs-lookup"><span data-stu-id="ed289-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="ed289-109">Em versões anteriores da configuração dos serviços do WCF (4.0 e anterior) no código era fácil em cenários auto-hospedados, o <xref:System.ServiceModel.ServiceHost> classe permitido configurar pontos de extremidade e comportamentos antes de chamar ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="ed289-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="ed289-110">Em cenários de hospedado na web, no entanto, você não tem acesso direto para o <xref:System.ServiceModel.ServiceHost> classe.</span><span class="sxs-lookup"><span data-stu-id="ed289-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="ed289-111">Para configurar um serviço Web hospedado, você precisava criar um `System.ServiceModel.ServiceHostFactory` que criou o <xref:System.ServiceModel.Activation.ServiceHostFactory> e executar qualquer configuração necessária.</span><span class="sxs-lookup"><span data-stu-id="ed289-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="ed289-112">Começando com o .NET 4.5, o WCF fornece uma maneira mais fácil configurar ambos auto-hospedado e hospedado de web services em código.</span><span class="sxs-lookup"><span data-stu-id="ed289-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="ed289-113">O método Configure</span><span class="sxs-lookup"><span data-stu-id="ed289-113">The Configure method</span></span>  
 <span data-ttu-id="ed289-114">Basta definir um método estático público chamado `Configure` com a assinatura a seguir em sua classe de implementação de serviço:</span><span class="sxs-lookup"><span data-stu-id="ed289-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="ed289-115">O método Configure leva um <xref:System.ServiceModel.ServiceConfiguration> instância que permite que o desenvolvedor adicione pontos de extremidade e comportamentos.</span><span class="sxs-lookup"><span data-stu-id="ed289-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="ed289-116">Esse método é chamado pelo WCF, antes do host de serviço é aberto.</span><span class="sxs-lookup"><span data-stu-id="ed289-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="ed289-117">Quando definido, as definições de configuração de serviço especificadas em um arquivo App. config ou Web. config serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="ed289-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="ed289-118">O trecho de código a seguir ilustra como definir o `Configure` método e adicione um ponto de extremidade de serviço, um comportamento de ponto de extremidade e comportamentos de serviço:</span><span class="sxs-lookup"><span data-stu-id="ed289-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
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
  
 <span data-ttu-id="ed289-119">Para habilitar um protocolo como o https para um serviço, você pode explicitamente adicionar um ponto de extremidade que usa o protocolo ou você pode adicionar automaticamente os pontos de extremidade chamando ServiceConfiguration.EnableProtocol(Binding) que adiciona um ponto de extremidade para cada endereço de base é compatível com o protocolo e cada contrato de serviço definido.</span><span class="sxs-lookup"><span data-stu-id="ed289-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="ed289-120">O código a seguir ilustra como usar o método ServiceConfiguration.EnableProtocol:</span><span class="sxs-lookup"><span data-stu-id="ed289-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
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
  
 <span data-ttu-id="ed289-121">As configurações no <`protocolMappings`> seção só serão usados se nenhum ponto de extremidade do aplicativo é adicionados ao <xref:System.ServiceModel.ServiceConfiguration> programaticamente. Opcionalmente, você pode carregar a configuração do serviço do arquivo de configuração de aplicativo padrão chamando <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> e, em seguida, altere as configurações.</span><span class="sxs-lookup"><span data-stu-id="ed289-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="ed289-122">O <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> classe também permite que você carregar a configuração de uma configuração centralizada.</span><span class="sxs-lookup"><span data-stu-id="ed289-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="ed289-123">O código a seguir ilustra como implementar isso:</span><span class="sxs-lookup"><span data-stu-id="ed289-123">The following code illustrates how to implement this:</span></span>  
  
```  
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
>  <span data-ttu-id="ed289-124">Observe que <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignora <`host`> configurações dentro do <`service`> marca de <`system.serviceModel`>.</span><span class="sxs-lookup"><span data-stu-id="ed289-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="ed289-125">Conceitualmente, <`host`> é sobre a configuração do host, não configuração de serviço e ele obtém carregado antes de executa o método Configure.</span><span class="sxs-lookup"><span data-stu-id="ed289-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed289-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed289-126">See also</span></span>

- [<span data-ttu-id="ed289-127">Configurando serviços usando arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="ed289-127">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [<span data-ttu-id="ed289-128">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="ed289-128">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="ed289-129">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="ed289-129">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="ed289-130">Configuração</span><span class="sxs-lookup"><span data-stu-id="ed289-130">Configuration</span></span>](../../../docs/framework/wcf/samples/configuration-sample.md)
- [<span data-ttu-id="ed289-131">Ativação baseada em configuração no IIS e WAS</span><span class="sxs-lookup"><span data-stu-id="ed289-131">Configuration-Based Activation in IIS and WAS</span></span>](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)
- [<span data-ttu-id="ed289-132">Configuração e suporte a metadados</span><span class="sxs-lookup"><span data-stu-id="ed289-132">Configuration and Metadata Support</span></span>](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)
- [<span data-ttu-id="ed289-133">Configuração</span><span class="sxs-lookup"><span data-stu-id="ed289-133">Configuration</span></span>](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)
- [<span data-ttu-id="ed289-134">Como: Especificar uma associação de serviço na configuração</span><span class="sxs-lookup"><span data-stu-id="ed289-134">How to: Specify a Service Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="ed289-135">Como: Criar um ponto de extremidade de serviço na configuração</span><span class="sxs-lookup"><span data-stu-id="ed289-135">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="ed289-136">Como: Publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="ed289-136">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="ed289-137">Como: Especificar uma associação de cliente na configuração</span><span class="sxs-lookup"><span data-stu-id="ed289-137">How to: Specify a Client Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
