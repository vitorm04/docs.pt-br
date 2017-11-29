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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 134de9fce41ccdcd9c26277c6a52d67823199da3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-wcf-services-in-code"></a>Configurando serviços WCF em código
O [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] permite que os desenvolvedores configurem serviços usando arquivos de configuração ou código.  Os arquivos de configuração são úteis quando um serviço precisa ser configurado depois de ser implantado. Ao usar arquivos de configuração, um profissional de TI apenas precisa atualizar o arquivo de configuração, nenhuma recompilação é necessária. Os arquivos de configuração, porém, podem ser complexos e difíceis de manter. Não há suporte para depurar arquivos de configuração e os elementos de configuração são referenciados por nomes, o que torna os arquivos de configuração de criação sujeitos a erros e difíceis. O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] também permite configurar serviços no código. Em versões anteriores do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 e anterior) configurar serviços no código era fácil em cenários auto-hospedados, a classe <xref:System.ServiceModel.ServiceHost> permitia que você configurasse pontos de extremidade e comportamentos antes de chamar o ServiceHost.Open. Em cenários de web hospedado, no entanto, você não tem acesso direto para o <xref:System.ServiceModel.ServiceHost> classe. Para configurar um serviço Web hospedado, você precisava criar um `System.ServiceModel.ServiceHostFactory` que criou o <xref:System.ServiceModel.Activation.ServiceHostFactory> e executar qualquer configuração necessária. A partir do .NET 4.5, o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] fornece um modo mais fácil de configurar serviços auto-hospedados e hospedados na Web em código.  
  
## <a name="the-configure-method"></a>O método de configurar  
 Basta definir um método estático público chamado `Configure` com a seguinte assinatura na sua classe de implementação de serviço:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 O método configurar usa um <xref:System.ServiceModel.ServiceConfiguration> instância que permite que o desenvolvedor adicionar pontos de extremidade e comportamentos. Este método é chamado pelo [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] antes que o host de serviço é aberto. Quando definido, as definições de configuração de serviço especificadas em um arquivo App. config ou Web. config serão ignoradas.  
  
 O trecho de código a seguir ilustra como definir o `Configure` método e adicionar um ponto de extremidade de serviço, um comportamento de ponto de extremidade e comportamentos de serviço:  
  
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
  
 Para habilitar um protocolo, como HTTP, para um serviço, você pode explicitamente adicionar um ponto de extremidade que usa o protocolo, ou você pode adicionar automaticamente os pontos de extremidade chamando ServiceConfiguration.EnableProtocol(Binding) que adiciona um ponto de extremidade para cada endereço de base compatível com o protocolo e cada contrato de serviço definido. O código a seguir ilustra como usar o método ServiceConfiguration.EnableProtocol:  
  
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
  
 As configurações de <`protocolMappings`> seção são usados somente se nenhum ponto de extremidade do aplicativo é adicionados à <xref:System.ServiceModel.ServiceConfiguration> programaticamente. Opcionalmente, você pode carregar a configuração do serviço do arquivo de configuração de aplicativo padrão chamando <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> e, em seguida, alterar as configurações. O <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> classe também permite que você carregar a configuração de uma configuração centralizada. O código a seguir ilustra como implementar isso:  
  
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
>  Observe que <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignora <`host`> configurações dentro do <`service`> marca de <`system.serviceModel`>. Conceitualmente, <`host`> é sobre a configuração do host, não configuração do serviço e ele é carregado antes de executa o método de configurar.  
  
## <a name="see-also"></a>Consulte também  
 [Configuring Services Using Configuration Files](../../../docs/framework/wcf/configuring-services-using-configuration-files.md) (Configurando serviços usando arquivos de configuração)  
 [Configuring Client Behaviors](../../../docs/framework/wcf/configuring-client-behaviors.md) (Configurando comportamentos do cliente)  
 [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) (Configuração simplificada)  
 [Ativação baseada em configuração](../../../docs/framework/wcf/samples/configuration-based-activation.md)  
 [Configuração](../../../docs/framework/wcf/samples/configuration-sample.md)  
 [Ativação com base em configuração no IIS e WAS](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 [Configuração e suporte a metadados](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)  
 [Configuração](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)  
 [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md) (Como especificar uma associação de serviço na configuração)  
 [Como: criar um ponto de extremidade de serviço na configuração](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [Como: publicar metadados para um serviço usando um arquivo de configuração](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [How to: Specify a Client Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md) (Como especificar uma associação de cliente na configuração)
