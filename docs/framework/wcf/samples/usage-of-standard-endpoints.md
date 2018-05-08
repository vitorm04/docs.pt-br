---
title: Uso de pontos de extremidade padrão
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 10f7280383a7fe381b36db76b72f7d67ba39eb40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="usage-of-standard-endpoints"></a>Uso de pontos de extremidade padrão
Este exemplo demonstra como usar pontos de extremidade padrão em arquivos de configuração de serviço. Um ponto de extremidade padrão permite que o usuário simplificar as definições de ponto de extremidade usando uma única propriedade para descrever um endereço, associação e contrato combinação com propriedades adicionais associadas a ele. Este exemplo demonstra como definir e implementar um ponto de extremidade padrão personalizado e como definir propriedades específicas no ponto de extremidade.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Pontos de extremidade de serviço podem ser especificados ao fornecer três parâmetros: endereço, associação e contrato. Outros parâmetros que podem ser fornecidos incluem a configuração de comportamento, cabeçalhos, URI de escuta e assim por diante. Em alguns casos, qualquer ou todos os endereços, associações e contratos têm valores que não é possível alterar. Por esse motivo, é possível usar pontos de extremidade padrão. Alguns exemplos de tais pontos de extremidade incluem pontos de extremidade de troca de metadados e pontos de extremidade de descoberta. Pontos de extremidade padrão também melhoram a usabilidade, permitindo que a configuração de pontos de extremidade de serviço sem ter que fornecer informações de natureza fixa ou para criar seus próprios pontos de extremidade padrão, por exemplo, para aumentar a usabilidade, fornecendo um conjunto razoável de padrão os valores e reduzindo o detalhamento dos arquivos de configuração.  
  
 Este exemplo consiste em dois projetos: o serviço que define os dois pontos de extremidade padrão e o cliente que se comunica com o serviço. A maneira como os pontos de extremidade padrão são definidos para o serviço no arquivo de configuração é mostrado no exemplo a seguir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <endpointExtensions>  
        <add name="customEndpoint" type="Microsoft.Samples.StandardEndpoints.CustomEndpointCollectionElement, service" />  
      </endpointExtensions>  
    </extensions>  
    <services>  
      <service name="Microsoft.Samples.StandardEndpoints.CalculatorService">  
        <endpoint address="http://localhost:8000/Samples/Service.svc/customEndpoint" contract="Microsoft.Samples.StandardEndpoints.ICalculator" kind="customEndpoint" />  
        <endpoint kind="mexEndpoint" />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <standardEndpoints>  
      <customEndpoint>  
        <standardEndpoint property="True" />  
      </customEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
</configuration>  
```  
  
 O primeiro ponto de extremidade definido para o serviço é do tipo `customEndpoint`, cuja definição pode ser vista no `<standardEndpoints>` seção, no qual a propriedade `property` recebe o valor `true`. Esse é o caso de um ponto de extremidade personalizado com uma nova propriedade. O segundo ponto de extremidade corresponde a um ponto de extremidade de metadados, em que os valores de endereço, associação e contrato são fixas.  
  
 Para definir o elemento de ponto de extremidade padrão, uma classe que deriva de `StandardEndpointElement` devem ser criados. Neste exemplo, no caso do `CustomEndpointElement` classe foi definida como mostrado no exemplo a seguir.  
  
```csharp  
public class CustomEndpointElement : StandardEndpointElement  
{  
    public bool Property  
    {  
        get { return (bool)base["property"]; }  
        set { base["property"] = value; }  
    }  
  
    protected override ConfigurationPropertyCollection Properties  
    {  
        get  
        {  
            ConfigurationPropertyCollection properties = base.Properties;  
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));  
            return properties;  
        }  
    }  
  
    protected override Type EndpointType  
    {  
        get { return typeof(CustomEndpoint); }  
    }  
  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)  
    {  
        return new CustomEndpoint();  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
    {  
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;  
        customEndpoint.Property = this.Property;  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
    {  
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;  
        customEndpoint.Property = this.Property;  
    }  
  
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
    {  
    }  
}  
```  
  
 No `CreateServiceEndpoint` função, um `CustomEndpoint` objeto é criado. Sua definição é mostrada no exemplo a seguir.  
  
```  
public class CustomEndpoint : ServiceEndpoint  
    {  
        public CustomEndpoint()  
            : this(string.Empty)  
        {  
        }  
  
        public CustomEndpoint(string address)  
            : this(address, ContractDescription.GetContract(typeof(ICalculator)))  
        {  
        }  
  
        public CustomEndpoint(string address, ContractDescription contract)  
            : base(contract)  
        {  
            this.Binding = new BasicHttpBinding();  
            this.IsSystemEndpoint = false;  
        }  
  
        public bool Property  
        {  
            get;  
            set;  
        }  
    }  
```  
  
 Para executar a comunicação entre cliente e de serviço, uma referência de serviço é criada no cliente para o serviço. Quando o exemplo é compilado e executado, o serviço é executado e o cliente se comunica com ele. Observe que a referência de serviço deve ser atualizada sempre que há alguma alteração no serviço.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo StandardEndpoints.sln.  
  
2.  Habilite vários projetos de inicialização.  
  
    1.  Em **Solution Explorer**, a solução de pontos de extremidade padrão e, em seguida, selecione **propriedades**.  
  
    2.  Em **propriedades comuns**, selecione **projeto de inicialização**e, em seguida, clique em **vários projetos de inicialização**.  
  
    3.  Mover o projeto de serviço para o início da lista, com o **ação** definida como **iniciar**.  
  
    4.  Mova o projeto de cliente quando o projeto de serviço, também com o **ação** definida como **iniciar**.  
  
         Especifica que o projeto de cliente é executado quando o projeto de serviço.  
  
3.  Para executar a solução, pressione F5.  
  
> [!NOTE]
>  Se essas etapas não funcionar, certifique-se de que seu ambiente foi adequadamente configurado, usando as etapas a seguir.  
>   
>  1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
> 2.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
> 3.  Para executar o exemplo em uma única ou várias configurações de computador, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`  
  
## <a name="see-also"></a>Consulte também
