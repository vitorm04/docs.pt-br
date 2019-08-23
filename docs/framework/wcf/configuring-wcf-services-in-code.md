---
title: Configurando serviços WCF em código
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 699549305ce8ca17480285e33570c01d00c7cb97
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948423"
---
# <a name="configuring-wcf-services-in-code"></a>Configurando serviços WCF em código
Windows Communication Foundation (WCF) permite que os desenvolvedores configurem serviços usando arquivos de configuração ou código.  Os arquivos de configuração são úteis quando um serviço precisa ser configurado depois de ser implantado. Ao usar arquivos de configuração, um profissional de TI apenas precisa atualizar o arquivo de configuração, nenhuma recompilação é necessária. Os arquivos de configuração, porém, podem ser complexos e difíceis de manter. Não há suporte para depurar arquivos de configuração e os elementos de configuração são referenciados por nomes, o que torna os arquivos de configuração de criação sujeitos a erros e difíceis. O WCF também permite que você configure serviços no código. Em versões anteriores do WCF (4,0 e anteriores) a configuração de serviços no código era fácil em cenários de hospedagem interna <xref:System.ServiceModel.ServiceHost> , a classe permitia que você configurasse pontos de extremidade e comportamentos antes de chamar ServiceHost. Open. No entanto, em cenários hospedados na Web, você não tem <xref:System.ServiceModel.ServiceHost> acesso direto à classe. Para configurar um serviço Web hospedado, você precisava criar um `System.ServiceModel.ServiceHostFactory` que criou o <xref:System.ServiceModel.Activation.ServiceHostFactory> e executar qualquer configuração necessária. A partir do .NET 4,5, o WCF fornece uma maneira mais fácil de configurar os serviços hospedados internamente e Web no código.  
  
## <a name="the-configure-method"></a>O método Configure  
 Basta definir um método estático público chamado `Configure` com a assinatura a seguir em sua classe de implementação de serviço:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 O método configure usa uma <xref:System.ServiceModel.ServiceConfiguration> instância que permite ao desenvolvedor adicionar pontos de extremidade e comportamentos. Esse método é chamado pelo WCF antes de o host de serviço ser aberto. Quando definido, quaisquer definições de configuração de serviço especificadas em um arquivo app. config ou Web. config serão ignoradas.  
  
 O trecho de código a seguir ilustra como definir `Configure` o método e adicionar um ponto de extremidade de serviço, um comportamento de ponto de extremidade e comportamentos de serviço:  
  
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
  
 Para habilitar um protocolo como o HTTPS para um serviço, você pode adicionar explicitamente um ponto de extremidade que usa o protocolo ou pode adicionar pontos de extremidades automaticamente chamando EnableProtocol (Binding), que adiciona um ponto de extremidade para cada endereço base compatível com o protocolo e cada contrato de serviço definido. O código a seguir ilustra como usar o método imconfiguration. EnableProtocol:  
  
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
  
 As configurações na seção <`protocolMappings`> só serão usadas se nenhum ponto de extremidade do <xref:System.ServiceModel.ServiceConfiguration> aplicativo for adicionado ao programaticamente. Opcionalmente, você pode carregar a configuração de serviço do arquivo de configuração de aplicativo <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> padrão chamando e, em seguida, alterando as configurações. A <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> classe também permite que você carregue a configuração de uma configuração centralizada. O código a seguir ilustra como implementar isso:  
  
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
> Observe que <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> o ignora <`host`configurações de > na`system.serviceModel`<`service`> marca de < >. Conceitualmente, <`host`> é sobre a configuração do host, não a configuração do serviço e é carregada antes da execução do método configure.  
  
## <a name="see-also"></a>Consulte também

- [Configurando serviços usando arquivos de configuração](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [Configurando comportamentos do cliente](../../../docs/framework/wcf/configuring-client-behaviors.md)
- [Configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md)
- [Configuração](../../../docs/framework/wcf/samples/configuration-sample.md)
- [Ativação baseada em configuração no IIS e WAS](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)
- [Configuração e suporte a metadados](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)
- [Configuração](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)
- [Como: Especificar uma associação de serviço na configuração](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Como: Criar um ponto de extremidade de serviço na configuração](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Como: Publicar metadados para um serviço usando um arquivo de configuração](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Como: Especificar uma associação de cliente na configuração](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
