---
title: Como publicar metadados para um serviço usando um arquivo de configuração
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 7ea0a2aa386f747b89f56f21d75a97e4409140a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184876"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Como publicar metadados para um serviço usando um arquivo de configuração
Este é um dos dois tópicos que demonstram a publicação de metadados para um serviço da Windows Communication Foundation (WCF). Existem duas maneiras de especificar como um serviço deve publicar metadados, usando um arquivo de configuração e usando código. Este tópico mostra como publicar metadados para um serviço usando um arquivo de configuração.  
  
> [!CAUTION]
> Este tópico mostra como publicar metadados de forma insegura. Qualquer cliente pode recuperar os metadados do serviço. Se você precisar que seu serviço publique metadados de forma segura, consulte [Ponto final de metadados personalizados](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Para obter mais informações sobre a publicação de metadados em código, consulte [Como publicar metadados para um serviço usando código](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md). A publicação de metadados permite que os clientes recuperem os metadados usando `?wsdl` uma solicitação WS-Transfer GET ou uma solicitação HTTP/GET usando a seqüência de consultas. Para ter certeza de que o código está funcionando, crie um serviço WCF básico. Para simplificar, um serviço básico auto-hospedado é fornecido no código a seguir.  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 Este serviço é um serviço auto-hospedado, que é configurado usando um arquivo de configuração. O arquivo de configuração a seguir serve como ponto de partida.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>Para publicar metadados para um serviço WCF usando um arquivo de configuração de aplicativo  
  
1. Dentro do arquivo App.config, `</services>` após o `<behaviors>` elemento de fechamento, crie um elemento.  

2. Dentro do elemento `<behaviors>`, adicione um elemento `<serviceBehaviors>`.  

3. Adicione `<behavior>` um elemento `<serviceBehaviors>` ao elemento e `name` especifique um valor para o atributo do `<behavior>` elemento.  

4. Adicione `<serviceMetadata>` um elemento `<behavior>` ao elemento. Defina `httpGetEnabled` o `true` atributo e o atributo `policyVersion` à Política15. `httpGetEnabled`permite que o serviço responda a solicitações de metadados feitas por uma solicitação HTTP GET. `policyVersion`diz ao serviço para estar em conformidade com a Política WS 1.5 ao gerar metadados.  

5. Adicione `behaviorConfiguration` um atributo ao `<service>` `name` elemento e `<behavior>` especifique o atributo do elemento adicionado na etapa 1, conforme mostrado no exemplo de código a seguir.  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6. Adicione um `<endpoint>` ou mais elementos `IMetadataExchange`com o contrato definido para , como mostrado no exemplo de código a seguir.  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7. Para os pontos finais de metadados adicionados na etapa anterior, defina o atributo `binding` como um dos seguintes:  
  
    - `mexHttpBinding`para publicação HTTP.  
  
    - `mexHttpsBinding`para publicação HTTPS.  
  
    - `mexNamedPipeBinding`para publicação de tubos nomeados.  
  
    - `mexTcpBinding`para publicação tcp.  
  
8. Para os pontos finais de metadados adicionados em uma etapa anterior, defina o endereço igual a:  
  
    - Uma seqüência de caracteres vazia para usar o endereço base do aplicativo host como ponto de publicação se o endereço base for o mesmo que a vinculação de metadados.  
  
    - Um endereço relativo se o aplicativo host tiver um endereço base.  
  
    - Um endereço absoluto.  
  
9. Crie e execute o aplicativo de console.  
  
10. Use o Internet Explorer para navegar atéhttp://localhost:8001/MetadataSample o endereço base do serviço (nesta amostra) e verificar se a publicação de metadados está ligada. Caso assim, uma mensagem na parte superior da página resultante seja exibida: "A publicação de metadados para este serviço está atualmente desativada".  
  
### <a name="to-use-default-endpoints"></a>Para usar pontos finais padrão  
  
1. Para configurar metadados em um serviço que usa <xref:System.ServiceModel.Description.ServiceMetadataBehavior> pontos finais padrão, especifique o no arquivo de configuração como no exemplo anterior, mas não especifique nenhum ponto final. O arquivo de configuração seria então parecido com isso.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Como o serviço <xref:System.ServiceModel.Description.ServiceMetadataBehavior> tem `httpGetEnabled` um `true`conjunto para , o serviço tem metadados de publicação ativados, e como nenhum ponto final foi explicitamente adicionado, o tempo de execução adiciona os pontos finais padrão. Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md) e [Configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra a implementação de um serviço WCF básico e o arquivo de configuração que publica metadados para o serviço.  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [Como hospedar um serviço do WCF em um aplicativo gerenciado](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Auto-hospedagem](../../../../docs/framework/wcf/samples/self-host.md)
- [Visão geral da arquitetura de metadados](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Utilizando metadados](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Como publicar metadados utilizando código para um serviço](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
