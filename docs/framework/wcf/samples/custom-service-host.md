---
title: Host de serviço personalizado
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 2aed557d1d045c08aed206660aa7b4b75ffe0e2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145066"
---
# <a name="custom-service-host"></a>Host de serviço personalizado
Esta amostra demonstra como usar um <xref:System.ServiceModel.ServiceHost> derivado personalizado da classe para alterar o comportamento de tempo de execução de um serviço. Essa abordagem fornece uma alternativa reutilizável para configurar um grande número de serviços de forma comum. A amostra também demonstra <xref:System.ServiceModel.Activation.ServiceHostFactory> como usar a classe para usar um ServiceHost personalizado no ambiente de hospedagem IIS (Internet Information Services, serviço de ativação de processos da Internet) ou do Windows Process Activation Service (WAS).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>Sobre o cenário
 Para evitar a divulgação não intencional de metadados de serviços potencialmente sensíveis, a configuração padrão dos serviços do Windows Communication Foundation (WCF) desativa a publicação de metadados. Esse comportamento é seguro por padrão, mas também significa que você não pode usar uma ferramenta de importação de metadados (como svcutil.exe) para gerar o código do cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço esteja explicitamente ativado na configuração.  
  
 Habilitar a publicação de metadados para um grande número de serviços envolve adicionar os mesmos elementos de configuração a cada serviço individual, o que resulta em uma grande quantidade de informações de configuração que são essencialmente as mesmas. Como alternativa à configuração individual de cada serviço, é possível escrever o código imperativo que permite a publicação de metadados uma vez e, em seguida, reutilizar esse código em vários serviços diferentes. Isso é feito criando uma nova <xref:System.ServiceModel.ServiceHost> classe que `ApplyConfiguration`deriva e substitui o método () para adicionar imperativamente o comportamento de publicação de metadados.  
  
> [!IMPORTANT]
> Para obter clareza, esta amostra demonstra como criar um ponto final de publicação de metadados não seguro. Esses pontos finais estão potencialmente disponíveis para consumidores anônimos não autenticados e os cuidados devem ser tomados antes de implantar tais pontos finais para garantir que a divulgação pública dos metadados de um serviço seja apropriada.  
  
## <a name="implementing-a-custom-servicehost"></a>Implementando um ServiceHost personalizado
 A <xref:System.ServiceModel.ServiceHost> classe expõe vários métodos virtuais úteis que os herdeiros podem substituir para alterar o comportamento de tempo de execução de um serviço. Por exemplo, `ApplyConfiguration`o método () lê informações de configuração de <xref:System.ServiceModel.Description.ServiceDescription> serviço do armazenamento de configuração e altera o host de acordo. A implementação padrão lê a configuração do arquivo de configuração do aplicativo. Implementações personalizadas `ApplyConfiguration`podem substituir () <xref:System.ServiceModel.Description.ServiceDescription> alterar ainda mais o código imperativo de uso ou até mesmo substituir totalmente o armazenamento de configuração padrão. Por exemplo, para ler a configuração de ponto final de um serviço a partir de um banco de dados em vez do arquivo de configuração do aplicativo.  
  
 Nesta amostra, queremos criar um ServiceHost personalizado que adiciona o ServiceMetadataBehavior (que permite a publicação de metadados), mesmo que esse comportamento não seja explicitamente adicionado no arquivo de configuração do serviço. Para isso, criamos uma nova classe <xref:System.ServiceModel.ServiceHost> que herda e substitui `ApplyConfiguration`().  
  
```csharp
class SelfDescribingServiceHost : ServiceHost  
{  
    public SelfDescribingServiceHost(Type serviceType, params Uri[] baseAddresses)  
        : base(serviceType, baseAddresses) { }  
  
    //Overriding ApplyConfiguration() allows us to
    //alter the ServiceDescription prior to opening  
    //the service host.
    protected override void ApplyConfiguration()  
    {  
        //First, we call base.ApplyConfiguration()  
        //to read any configuration that was provided for  
        //the service we're hosting. After this call,  
        //this.Description describes the service  
        //as it was configured.  
        base.ApplyConfiguration();
  
        //(rest of implementation elided for clarity)  
    }  
}  
```  
  
 Como não queremos ignorar qualquer configuração que tenha sido fornecida no arquivo de configuração do aplicativo, a primeira coisa que `ApplyConfiguration`nossa substituição faz é chamar a implementação base. Uma vez que este método seja <xref:System.ServiceModel.Description.ServiceMetadataBehavior> concluído, podemos adicionar a descrição da descrição usando o seguinte código imperativo.  
  
```csharp
ServiceMetadataBehavior mexBehavior = this.Description.Behaviors.Find<ServiceMetadataBehavior>();  
if (mexBehavior == null)  
{  
    mexBehavior = new ServiceMetadataBehavior();  
    this.Description.Behaviors.Add(mexBehavior);  
}  
else  
{  
    //Metadata behavior has already been configured,
    //so we do not have any work to do.  
    return;  
}  
```  
  
 A última `ApplyConfiguration`coisa que nossa () substituição deve fazer é adicionar o ponto final de metadados padrão. Por convenção, um ponto final de metadados é criado para cada URI na coleção BaseAddresses do host de serviço.  
  
```csharp
//Add a metadata endpoint at each base address  
//using the "/mex" addressing convention  
foreach (Uri baseAddress in this.BaseAddresses)  
{  
    if (baseAddress.Scheme == Uri.UriSchemeHttp)  
    {  
        mexBehavior.HttpGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeHttps)  
    {  
        mexBehavior.HttpsGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpsBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetPipe)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexNamedPipeBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetTcp)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexTcpBinding(),  
                                "mex");  
    }  
}  
```  
  
## <a name="using-a-custom-servicehost-in-self-host"></a>Usando um ServiceHost personalizado no self-host  
 Agora que concluímos nossa implementação personalizada do ServiceHost, podemos usá-lo para adicionar comportamento de publicação `SelfDescribingServiceHost`de metadados a qualquer serviço, hospedando esse serviço dentro de uma instância do nosso . O código a seguir mostra como usá-lo no cenário de auto-host.  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 Nosso host personalizado ainda lê a configuração de ponto final do serviço a partir <xref:System.ServiceModel.ServiceHost> do arquivo de configuração do aplicativo, como se tivéssemos usado a classe padrão para hospedar o serviço. No entanto, como adicionamos a lógica para permitir a publicação de metadados dentro do nosso host personalizado, não devemos mais habilitar explicitamente o comportamento de publicação de metadados na configuração. Essa abordagem tem uma vantagem distinta quando você está construindo um aplicativo que contém vários serviços e você deseja permitir a publicação de metadados em cada um deles sem escrever os mesmos elementos de configuração várias vezes.  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>Usando um ServiceHost personalizado no IIS ou WAS  
 O uso de um host de serviço personalizado em cenários de auto-host é simples, porque é o código do aplicativo que é responsável pela criação e abertura da instância de host do serviço. No ambiente de hospedagem IIS ou WAS, no entanto, a infra-estrutura WCF está instanciando o host do seu serviço em resposta às mensagens recebidas. Hosts de serviço personalizados também podem ser usados neste ambiente de hospedagem, mas eles requerem algum código adicional na forma de um ServiceHostFactory. O código a seguir <xref:System.ServiceModel.Activation.ServiceHostFactory> mostra uma derivada de que retorna instâncias do nosso costume `SelfDescribingServiceHost`.  
  
```csharp
public class SelfDescribingServiceHostFactory : ServiceHostFactory  
{  
    protected override ServiceHost CreateServiceHost(Type serviceType,
     Uri[] baseAddresses)  
    {  
        //All the custom factory does is return a new instance  
        //of our custom host class. The bulk of the custom logic should  
        //live in the custom host (as opposed to the factory)
        //for maximum  
        //reuse value outside of the IIS/WAS hosting environment.  
        return new SelfDescribingServiceHost(serviceType,
                                             baseAddresses);  
    }  
}  
```  
  
 Como você pode ver, implementar um ServiceHostFactory personalizado é muito simples. Toda a lógica personalizada reside dentro da implementação do ServiceHost; a fábrica retorna uma instância da classe derivada.  
  
 Para usar uma fábrica personalizada com uma implementação de serviço, devemos adicionar alguns metadados adicionais ao arquivo .svc do serviço.  
  
```xml
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 Aqui adicionamos um `Factory` atributo `@ServiceHost` adicional à diretiva, e passamos o nome do tipo CLR da nossa fábrica personalizada como o valor do atributo. Quando o IIS ou WAS recebe uma mensagem para este serviço, a infra-estrutura de hospedagem `ServiceHostFactory.CreateServiceHost()`WCF cria primeiro uma instância do ServiceHostFactory e, em seguida, instancia o próprio host do serviço, chamando .  
  
## <a name="running-the-sample"></a>Executando o exemplo  
 Embora esta amostra forneça uma implementação de serviço e cliente totalmente funcional, o objetivo da amostra é ilustrar como alterar o comportamento de tempo de execução de um serviço por meio de um host personalizado., faça as seguintes etapas:  
  
### <a name="observe-the-effect-of-the-custom-host"></a>Observe o efeito do host personalizado
  
1. Abra o arquivo Web.config do serviço e observe que não há configuração que habilite metadados explicitamente para o serviço.  
  
2. Abra o arquivo .svc do serviço @ServiceHost e observe que sua diretiva contém um atributo Factory que especifica o nome de um ServiceHostFactory personalizado.  
  
### <a name="set-up-build-and-run-the-sample"></a>Configurar, construir e executar a amostra
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](building-the-samples.md).

3. Depois que a solução for construída, execute Setup.bat para configurar o aplicativo ServiceModelSamples no IIS 7.0. O diretório ServiceModelSamples agora deve aparecer como um aplicativo IIS 7.0.

4. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](running-the-samples.md).

5. Para remover o aplicativo IIS 7.0, execute *Cleanup.bat*.

## <a name="see-also"></a>Confira também

- [Como hospedar um serviço WCF no IIS](../feature-details/how-to-host-a-wcf-service-in-iis.md)
