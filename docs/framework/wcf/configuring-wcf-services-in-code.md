---
title: "Configurando serviços WCF em código"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c05cc5947a36bbe8573c5308cdfbbe3f6c990815
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="1a920-102">Configurando serviços WCF em código</span><span class="sxs-lookup"><span data-stu-id="1a920-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="1a920-103">O [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] permite que os desenvolvedores configurem serviços usando arquivos de configuração ou código.</span><span class="sxs-lookup"><span data-stu-id="1a920-103">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="1a920-104">Os arquivos de configuração são úteis quando um serviço precisa ser configurado depois de ser implantado.</span><span class="sxs-lookup"><span data-stu-id="1a920-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="1a920-105">Ao usar arquivos de configuração, um profissional de TI apenas precisa atualizar o arquivo de configuração, nenhuma recompilação é necessária.</span><span class="sxs-lookup"><span data-stu-id="1a920-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="1a920-106">Os arquivos de configuração, porém, podem ser complexos e difíceis de manter.</span><span class="sxs-lookup"><span data-stu-id="1a920-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="1a920-107">Não há suporte para depurar arquivos de configuração e os elementos de configuração são referenciados por nomes, o que torna os arquivos de configuração de criação sujeitos a erros e difíceis.</span><span class="sxs-lookup"><span data-stu-id="1a920-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="1a920-108">O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] também permite configurar serviços no código.</span><span class="sxs-lookup"><span data-stu-id="1a920-108">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] also allows you to configure services in code.</span></span> <span data-ttu-id="1a920-109">Em versões anteriores do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 e anterior) configurar serviços no código era fácil em cenários auto-hospedados, a classe <xref:System.ServiceModel.ServiceHost> permitia que você configurasse pontos de extremidade e comportamentos antes de chamar o ServiceHost.Open.</span><span class="sxs-lookup"><span data-stu-id="1a920-109">In earlier versions of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="1a920-110">Em cenários de web hospedado, no entanto, você não tem acesso direto para o <xref:System.ServiceModel.ServiceHost> classe.</span><span class="sxs-lookup"><span data-stu-id="1a920-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="1a920-111">Para configurar um serviço Web hospedado, você precisava criar um `System.ServiceModel.ServiceHostFactory` que criou o <xref:System.ServiceModel.Activation.ServiceHostFactory> e executar qualquer configuração necessária.</span><span class="sxs-lookup"><span data-stu-id="1a920-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="1a920-112">A partir do .NET 4.5, o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] fornece um modo mais fácil de configurar serviços auto-hospedados e hospedados na Web em código.</span><span class="sxs-lookup"><span data-stu-id="1a920-112">Starting with .NET 4.5, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="1a920-113">O método de configurar</span><span class="sxs-lookup"><span data-stu-id="1a920-113">The Configure method</span></span>  
 <span data-ttu-id="1a920-114">Basta definir um método estático público chamado `Configure` com a seguinte assinatura na sua classe de implementação de serviço:</span><span class="sxs-lookup"><span data-stu-id="1a920-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="1a920-115">O método configurar usa um <xref:System.ServiceModel.ServiceConfiguration> instância que permite que o desenvolvedor adicionar pontos de extremidade e comportamentos.</span><span class="sxs-lookup"><span data-stu-id="1a920-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="1a920-116">Este método é chamado pelo [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] antes que o host de serviço é aberto.</span><span class="sxs-lookup"><span data-stu-id="1a920-116">This method is called by [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] before the service host is opened.</span></span> <span data-ttu-id="1a920-117">Quando definido, as definições de configuração de serviço especificadas em um arquivo App. config ou Web. config serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="1a920-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="1a920-118">O trecho de código a seguir ilustra como definir o `Configure` método e adicionar um ponto de extremidade de serviço, um comportamento de ponto de extremidade e comportamentos de serviço:</span><span class="sxs-lookup"><span data-stu-id="1a920-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
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
            return string.Format("You entered: {0}", value);  
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
  
 <span data-ttu-id="1a920-119">Para habilitar um protocolo, como HTTP, para um serviço, você pode explicitamente adicionar um ponto de extremidade que usa o protocolo, ou você pode adicionar automaticamente os pontos de extremidade chamando ServiceConfiguration.EnableProtocol(Binding) que adiciona um ponto de extremidade para cada endereço de base compatível com o protocolo e cada contrato de serviço definido.</span><span class="sxs-lookup"><span data-stu-id="1a920-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="1a920-120">O código a seguir ilustra como usar o método ServiceConfiguration.EnableProtocol:</span><span class="sxs-lookup"><span data-stu-id="1a920-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
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
  
 <span data-ttu-id="1a920-121">As configurações de <`protocolMappings`> seção são usados somente se nenhum ponto de extremidade do aplicativo é adicionados à <xref:System.ServiceModel.ServiceConfiguration> programaticamente. Opcionalmente, você pode carregar a configuração do serviço do arquivo de configuração de aplicativo padrão chamando <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> e, em seguida, alterar as configurações.</span><span class="sxs-lookup"><span data-stu-id="1a920-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="1a920-122">O <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> classe também permite que você carregar a configuração de uma configuração centralizada.</span><span class="sxs-lookup"><span data-stu-id="1a920-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="1a920-123">O código a seguir ilustra como implementar isso:</span><span class="sxs-lookup"><span data-stu-id="1a920-123">The following code illustrates how to implement this:</span></span>  
  
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
>  <span data-ttu-id="1a920-124">Observe que <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignora <`host`> configurações dentro do <`service`> marca de <`system.serviceModel`>.</span><span class="sxs-lookup"><span data-stu-id="1a920-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="1a920-125">Conceitualmente, <`host`> é sobre a configuração do host, não configuração do serviço e ele é carregado antes de executa o método de configurar.</span><span class="sxs-lookup"><span data-stu-id="1a920-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a920-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a920-126">See Also</span></span>  
 <span data-ttu-id="1a920-127">[Configuring Services Using Configuration Files](../../../docs/framework/wcf/configuring-services-using-configuration-files.md) (Configurando serviços usando arquivos de configuração)</span><span class="sxs-lookup"><span data-stu-id="1a920-127">[Configuring Services Using Configuration Files](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)</span></span>  
 <span data-ttu-id="1a920-128">[Configuring Client Behaviors](../../../docs/framework/wcf/configuring-client-behaviors.md) (Configurando comportamentos do cliente)</span><span class="sxs-lookup"><span data-stu-id="1a920-128">[Configuring Client Behaviors](../../../docs/framework/wcf/configuring-client-behaviors.md)</span></span>  
 <span data-ttu-id="1a920-129">[Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) (Configuração simplificada)</span><span class="sxs-lookup"><span data-stu-id="1a920-129">[Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
 [<span data-ttu-id="1a920-130">Ativação baseada em configuração</span><span class="sxs-lookup"><span data-stu-id="1a920-130">Configuration-Based Activation</span></span>](../../../docs/framework/wcf/samples/configuration-based-activation.md)  
 [<span data-ttu-id="1a920-131">Configuração</span><span class="sxs-lookup"><span data-stu-id="1a920-131">Configuration</span></span>](../../../docs/framework/wcf/samples/configuration-sample.md)  
 [<span data-ttu-id="1a920-132">Ativação com base em configuração no IIS e WAS</span><span class="sxs-lookup"><span data-stu-id="1a920-132">Configuration-Based Activation in IIS and WAS</span></span>](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 [<span data-ttu-id="1a920-133">Configuração e suporte a metadados</span><span class="sxs-lookup"><span data-stu-id="1a920-133">Configuration and Metadata Support</span></span>](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)  
 [<span data-ttu-id="1a920-134">Configuração</span><span class="sxs-lookup"><span data-stu-id="1a920-134">Configuration</span></span>](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)  
 <span data-ttu-id="1a920-135">[How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md) (Como especificar uma associação de serviço na configuração)</span><span class="sxs-lookup"><span data-stu-id="1a920-135">[How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)</span></span>  
 [<span data-ttu-id="1a920-136">Como: criar um ponto de extremidade de serviço na configuração</span><span class="sxs-lookup"><span data-stu-id="1a920-136">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [<span data-ttu-id="1a920-137">Como: publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="1a920-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="1a920-138">[How to: Specify a Client Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md) (Como especificar uma associação de cliente na configuração)</span><span class="sxs-lookup"><span data-stu-id="1a920-138">[How to: Specify a Client Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)</span></span>
