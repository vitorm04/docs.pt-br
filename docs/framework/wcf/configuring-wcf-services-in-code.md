---
title: Configurando serviços WCF em código
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 4ff49b4e17ae179426cc033a955ecf2c71f2a3e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174804"
---
# <a name="configuring-wcf-services-in-code"></a>Configurando serviços WCF em código
O Windows Communication Foundation (WCF) permite que os desenvolvedores configurem serviços usando arquivos de configuração ou código.  Os arquivos de configuração são úteis quando um serviço precisa ser configurado depois de ser implantado. Ao usar arquivos de configuração, um profissional de TI apenas precisa atualizar o arquivo de configuração, nenhuma recompilação é necessária. Os arquivos de configuração, porém, podem ser complexos e difíceis de manter. Não há suporte para depurar arquivos de configuração e os elementos de configuração são referenciados por nomes, o que torna os arquivos de configuração de criação sujeitos a erros e difíceis. O WCF também permite configurar serviços em código. Em versões anteriores do WCF (4.0 e anterior) a configuração <xref:System.ServiceModel.ServiceHost> de serviços em código era fácil em cenários auto-hospedados, a classe permitia configurar pontos finais e comportamentos antes de chamar ServiceHost.Open. Em cenários hospedados na web, no entanto, você não tem acesso direto à <xref:System.ServiceModel.ServiceHost> classe. Para configurar um serviço Web hospedado, você precisava criar um `System.ServiceModel.ServiceHostFactory` que criou o <xref:System.ServiceModel.Activation.ServiceHostFactory> e executar qualquer configuração necessária. A partir do .NET 4.5, o WCF fornece uma maneira mais fácil de configurar serviços hospedados e hospedados na Web em código.  
  
## <a name="the-configure-method"></a>O método Configure  
 Basta definir um método `Configure` estático público chamado com a seguinte assinatura em sua classe de implementação de serviço:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 O método Configurar <xref:System.ServiceModel.ServiceConfiguration> toma uma instância que permite ao desenvolvedor adicionar pontos finais e comportamentos. Este método é chamado pelo WCF antes que o host de serviço seja aberto. Quando definido, quaisquer configurações de configuração de serviço especificadas em um arquivo app.config ou web.config serão ignoradas.  
  
 O seguinte trecho de código ilustra `Configure` como definir o método e adicionar um ponto final de serviço, um comportamento de ponto final e comportamentos de serviço:  
  
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
  
 Para habilitar um protocolo como https para um serviço, você pode adicionar explicitamente um ponto final que usa o protocolo ou você pode adicionar automaticamente pontos finais chamando ServiceConfiguration.EnableProtocol(Binding) que adiciona um ponto final para cada endereço base compatível com o protocolo e cada contrato de serviço definido. O código a seguir ilustra como usar o método ServiceConfiguration.EnableProtocol:  
  
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
       config.EnableProtocol(new BasicHttpsBinding());
       config.EnableProtocol(new NetTcpBinding());
       config.EnableProtocol(new NetNamedPipeBinding());
       // add an extra BasicHttpBinding endpoint at http:///basic
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");
    }
}
```  
  
 As configurações na `protocolMappings` seção <> só são usadas <xref:System.ServiceModel.ServiceConfiguration> se nenhum ponto final do aplicativo for adicionado à programação. Você pode, opcionalmente, carregar a configuração <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> de serviço do arquivo de configuração de aplicativo padrão ligando e, em seguida, alterar as configurações. A <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> classe também permite que você carregue a configuração a partir de uma configuração centralizada. O código a seguir ilustra como implementar isso:  
  
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
> Observe <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> que ignora <`host` configurações `service`> dentro `system.serviceModel` da <> tag de> <. Conceitualmente, `host` <> é sobre configuração do host, não configuração de serviço, e ele é carregado antes que o método Configure seja executado.  
  
## <a name="see-also"></a>Confira também

- [Configurando serviços usando arquivos de configuração](configuring-services-using-configuration-files.md)
- [Configurando comportamentos do cliente](configuring-client-behaviors.md)
- [Configuração simplificada](simplified-configuration.md)
- [Configuração](./samples/configuration-sample.md)
- [Ativação com base em configuração no ISS e WAS](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [Configuração e suporte de metadados](./extending/configuration-and-metadata-support.md)
- [Configuração](./diagnostics/exceptions-reference/configuration.md)
- [Como especificar uma associação de serviço na configuração](how-to-specify-a-service-binding-in-configuration.md)
- [Como criar um ponto de extremidade de serviço em configuração](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Como publicar metadados para um serviço usando um arquivo de configuração](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Como especificar uma associação de cliente na configuração](how-to-specify-a-client-binding-in-configuration.md)
