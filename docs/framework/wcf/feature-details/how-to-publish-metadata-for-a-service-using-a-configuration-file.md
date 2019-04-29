---
title: 'Como: publicar metadados para um serviço usando um arquivo de configuração'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 367ebeee5c12d809a758f1bee73dfaadda85788d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761449"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Como: publicar metadados para um serviço usando um arquivo de configuração
Esse é um dos dois tópicos que demonstram os metadados de publicação para um serviço do Windows Communication Foundation (WCF). Há duas maneiras para especificar como um serviço deve publicar metadados, usando um arquivo de configuração e código. Este tópico mostra como publicar metadados para um serviço usando um arquivo de configuração.  
  
> [!CAUTION]
>  Este tópico mostra como publicar metadados de maneira não segura. Qualquer cliente pode recuperar os metadados do serviço. Se você precisar de seu serviço para publicar os metadados de uma maneira segura, consulte [ponto de extremidade de metadados seguros personalizado](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Para obter mais informações sobre metadados de publicação no código, consulte [como: Publicar metadados para um serviço usando código](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md). Metadados de publicação permite que os clientes recuperar os metadados usando uma solicitação GET do WS-Transfer ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta. Para certificar-se de que o código está funcionando, crie um serviço WCF básico. Para simplificar, um serviço auto-hospedado básico é fornecido no código a seguir.  
  
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
  
 Esse serviço é um serviço auto-hospedado, o que é configurado usando um arquivo de configuração. O arquivo de configuração a seguir serve como um ponto de partida.  
  
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
  
1. Dentro do arquivo App. config, após o fechamento `</services>` elemento, criar um `<behaviors>` elemento.  

2. Dentro de `<behaviors>` elemento, adicionar um `<serviceBehaviors>` elemento.  

3. Adicionar um `<behavior>` elemento para o `<serviceBehaviors>` elemento e especifique um valor para o `name` atributo do `<behavior>` elemento.  

4. Adicionar um `<serviceMetadata>` elemento para o `<behavior>` elemento. Defina as `httpGetEnabled` de atributo para `true` e o `policyVersion` Policy15 do atributo. `httpGetEnabled` permite que o serviço responder a solicitações de metadados feitas por uma solicitação HTTP GET. `policyVersion` instrui o serviço em conformidade com WS-Policy 1.5 durante a geração de metadados.  

5. Adicionar um `behaviorConfiguration` de atributo para o `<service>` elemento e especifique a `name` atributo do `<behavior>` elemento adicionado na etapa 1, conforme mostrado no exemplo de código a seguir.  
  
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
  
6. Adicione um ou mais `<endpoint>` elementos com o contrato é definido como `IMetadataExchange`, conforme mostrado no exemplo de código a seguir.  
  
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
  
7. Para os pontos de extremidade de metadados adicionados na etapa anterior, defina o `binding` de atributo para um dos seguintes:  
  
    - `mexHttpBinding` para a publicação de HTTP.  
  
    - `mexHttpsBinding` para a publicação de HTTPS.  
  
    - `mexNamedPipeBinding` para a publicação de pipe nomeado.  
  
    - `mexTcpBinding` para a publicação de TCP.  
  
8. Para os pontos de extremidade de metadados adicionados em uma etapa anterior, defina o endereço para:  
  
    - Uma cadeia de caracteres vazia para usar o endereço de base do aplicativo host como o ponto de publicação se o endereço básico é o mesmo que a associação de metadados.  
  
    - Um endereço relativo, se o aplicativo host tem um endereço básico.  
  
    - Um endereço absoluto.  
  
9. Compile e execute o aplicativo de console.  
  
10. Usar o Internet Explorer para navegar até o endereço base do serviço (http://localhost:8001/MetadataSample neste exemplo) e verifique se a publicação de metadados está ligada. Caso contrário, exibe uma mensagem na parte superior da página resultante: "Publicação de metadados para este serviço está desabilitada no momento."  
  
### <a name="to-use-default-endpoints"></a>Para usar pontos de extremidade padrão  
  
1. Para configurar os metadados em um serviço que usa pontos de extremidade padrão, especifique o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> na configuração de arquivo do exemplo anterior, mas não especificar qualquer ponto de extremidade. O arquivo de configuração, em seguida, ficaria assim.  
  
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
  
     Como o serviço tem um <xref:System.ServiceModel.Description.ServiceMetadataBehavior> com o `httpGetEnabled` definido como `true`, o serviço tem metadados de publicação habilitados e porque nenhum ponto de extremidade foram adicionados explicitamente, o tempo de execução adiciona pontos de extremidade padrão. Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md) e [Configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [Como: Hospedar um serviço WCF em um aplicativo gerenciado](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Auto-hospedagem](../../../../docs/framework/wcf/samples/self-host.md)
- [Visão geral da arquitetura de metadados](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Usando metadados](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Como: Publicar metadados para um serviço usando código](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
