---
title: Host de serviço personalizado
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: d2eebd502fa02d01ac86cf88f336b72829a6116f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340926"
---
# <a name="custom-service-host"></a>Host de serviço personalizado
Este exemplo demonstra como usar um personalizado derivado do <xref:System.ServiceModel.ServiceHost> classe para alterar o comportamento de tempo de execução de um serviço. Essa abordagem fornece uma alternativa reutilizável para configurar um grande número de serviços de uma maneira comum. O exemplo também demonstra como usar o <xref:System.ServiceModel.Activation.ServiceHostFactory> classe para usar um ServiceHost personalizado no ambiente de hospedagem dos serviços de informações da Internet (IIS) ou o serviço de ativação de processos do Windows (WAS).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>Sobre o cenário  
 Para evitar a divulgação acidental de metadados de serviço potencialmente confidenciais, a configuração padrão para serviços Windows Communication Foundation (WCF) desabilita a publicação de metadados. Esse comportamento é seguro por padrão, mas também significa que você não pode usar metadados importar ferramenta (como Svcutil.exe) para gerar o código de cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço é explicitamente habilitado na configuração.  
  
 Habilitar a publicação de metadados para um grande número de serviços envolve a adição os mesmos elementos de configuração para cada serviço, que resulta em uma grande quantidade de informações de configuração que é essencialmente o mesmo. Como alternativa à configuração de cada serviço individualmente, é possível escrever o código imperativo que permite que os metadados de publicação de uma vez e, em seguida, reutilizar esse código em vários serviços diferentes. Isso é feito criando uma nova classe que deriva de <xref:System.ServiceModel.ServiceHost> e substitui o `ApplyConfiguration`método () para adicionar imperativamente o comportamento de publicação de metadados.  
  
> [!IMPORTANT]
>  Para maior clareza, este exemplo demonstra como criar um ponto de extremidade de publicação de metadados não segura. Esses pontos de extremidade estão potencialmente disponíveis para os consumidores não autenticados anônimos e tome cuidado antes de implantar esses pontos de extremidade para garantir que publicamente divulga metadados de um serviço são apropriado.  
  
## <a name="implementing-a-custom-servicehost"></a>Implementando um ServiceHost personalizado  
 O <xref:System.ServiceModel.ServiceHost> classe expõe vários métodos virtuais útil que os herdeiros podem substituir para alterar o comportamento de tempo de execução de um serviço. Por exemplo, o `ApplyConfiguration`método () lê as informações de configuração de serviço de repositório de configuração e altera o host <xref:System.ServiceModel.Description.ServiceDescription> adequadamente. A implementação padrão lê a configuração do arquivo de configuração do aplicativo. As implementações personalizadas podem substituir `ApplyConfiguration`() para alterar o ainda mais o <xref:System.ServiceModel.Description.ServiceDescription> usando o código obrigatório ou até mesmo substituir o repositório de configuração padrão inteiramente. Por exemplo, para ler a configuração de ponto de extremidade do serviço de um banco de dados em vez do arquivo de configuração do aplicativo.  
  
 Neste exemplo, queremos criar um ServiceHost personalizado que adiciona a ServiceMetadataBehavior, (que permite a publicação de metadados), mesmo se esse comportamento não for explicitamente adicionado no arquivo de configuração do serviço. Para fazer isso, podemos criar uma nova classe que herda de <xref:System.ServiceModel.ServiceHost> e substitui `ApplyConfiguration`().  
  
```  
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
  
 Porque não queremos ignorar qualquer configuração que foi fornecida no arquivo de configuração do aplicativo, a primeira coisa que nosso substituição do `ApplyConfiguration`() faz é chamada a implementação base. Quando esse método for concluído, podemos imperativamente adicionar o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> a descrição usando o seguinte código imperativo.  
  
```  
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
  
 A última coisa que nosso `ApplyConfiguration`substituição () deve fazer é adicionar o ponto de extremidade de metadados padrão. Por convenção, um ponto de extremidade de metadados é criado para cada URI na coleção de BaseAddresses do host de serviço.  
  
```  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a>Usando um ServiceHost personalizado na hospedagem interna  
 Agora que concluímos nossa implementação de ServiceHost personalizada, podemos usar isso para adicionar o comportamento de publicação de metadados para qualquer serviço ao hospedar esse serviço dentro de uma instância do nosso `SelfDescribingServiceHost`. O código a seguir mostra como usá-lo no cenário de hospedagem interna.  
  
```  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 Nosso host personalizado ainda lê configuração de ponto de extremidade do serviço de arquivo de configuração do aplicativo, como se tivéssemos usado o padrão <xref:System.ServiceModel.ServiceHost> classe para hospedar o serviço. No entanto, como adicionamos a lógica para habilitar a publicação dentro de nosso host personalizado de metadados, podemos não deve habilitar explicitamente o comportamento de publicação na configuração de metadados. Essa abordagem tem uma vantagem quando você estiver criando um aplicativo que contém vários serviços e você deseja habilitar a publicação de metadados em cada um deles sem precisar escrever os mesmos elementos de configuração diversas vezes.  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>Usando um ServiceHost personalizado no IIS ou WAS  
 Usar um host de serviço personalizado em cenários de hospedagem interna é simples, porque ele é o código do aplicativo que é basicamente responsável criando e abrindo a instância do host de serviço. No IIS ou no ambiente de hospedagem do WAS, no entanto, a infraestrutura do WCF é dinamicamente criando uma instância de host do seu serviço em resposta às mensagens de entrada. Hosts de serviço personalizado também podem ser usados nesse ambiente de hospedagem, mas elas exigem alguns códigos adicionais na forma de um ServiceHostFactory. O código a seguir mostra um derivado de <xref:System.ServiceModel.Activation.ServiceHostFactory> que retorna instâncias do nosso personalizado `SelfDescribingServiceHost`.  
  
```  
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
  
 Como você pode ver, implementar um ServiceHostFactory personalizado é muito simples. Toda a lógica personalizada reside dentro a implementação de ServiceHost; a fábrica retorna uma instância da classe derivada.  
  
 Para usar uma fábrica personalizada com uma implementação de serviço, devemos adicionar alguns metadados adicionais para o arquivo do serviço. svc.  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 Aqui, adicionamos adicional `Factory` de atributo para o `@ServiceHost` diretiva e passadas CLR digite o nome de nossa fábrica personalizada como o valor do atributo. Quando o IIS ou WAS recebe uma mensagem para esse serviço, a infraestrutura de hospedagem do WCF primeiro cria uma instância da ServiceHostFactory e, em seguida, instanciar o host de serviço chamando `ServiceHostFactory.CreateServiceHost()`.  
  
## <a name="running-the-sample"></a>A execução do exemplo  
 Embora este exemplo fornece um cliente totalmente funcional e a implementação do serviço, o ponto do exemplo é ilustrar como alterar o comportamento de tempo de execução de um serviço por meio de um host personalizado., execute as seguintes etapas:  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a>Para observar o efeito do host personalizado  
  
1. Abra o arquivo do serviço Web. config e observe que não há nenhuma configuração habilitando explicitamente os metadados para o serviço.  
  
2. Abra o arquivo do serviço. svc e observe que seu @ServiceHost diretiva contém um atributo de fábrica que especifica o nome de um ServiceHostFactory personalizado.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Depois que a solução foi criada, execute Setup. bat para configurar o aplicativo ServiceModelSamples no [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. O diretório ServiceModelSamples agora deve aparecer como um [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplicativo.  
  
4. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Para remover o [!INCLUDE[iisver](../../../../includes/iisver-md.md)] execução CleanUp do aplicativo.  
  
## <a name="see-also"></a>Consulte também

- [Como: Hospedar um serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
