---
title: Vários pontos de extremidade em único ListenUri
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: 8e26cc18ed35c446dda120c678dd7e879c756c0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183478"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Vários pontos de extremidade em único ListenUri
Esta amostra demonstra um serviço que hospeda vários pontos finais em um único `ListenUri`. Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Como demonstrado na amostra [De múltiplos pontos finais,](../../../../docs/framework/wcf/samples/multiple-endpoints.md) um serviço pode hospedar vários pontos finais, cada um com endereços diferentes e possivelmente também ligações diferentes. Esta amostra mostra que é possível hospedar vários pontos finais no mesmo endereço. Esta amostra também demonstra as diferenças entre os dois tipos `EndpointAddress` `ListenUri`de endereços que um ponto final de serviço tem: e .  
  
 O `EndpointAddress` é o endereço lógico de um serviço. É o endereço para o endereço para o que as mensagens SOAP são endereçadas. O `ListenUri` é o endereço físico do serviço. Ele tem as informações de porta e endereço onde o ponto final do serviço realmente ouve mensagens na máquina atual. Na maioria dos casos, não há necessidade de que esses endereços sejam diferentes; quando `ListenUri` a não é explicitamente especificada, ela é `EndpointAddress` padrão para o URI do ponto final. Em alguns casos, é útil distingui-los, como ao configurar um roteador, que pode aceitar mensagens dirigidas a uma série de serviços diferentes.  
  
## <a name="service"></a>Serviço  
 O serviço nesta amostra tem `ICalculator` `IEcho`dois contratos, e . Além do ponto `IMetadataExchange` final habitual, há três pontos finais de aplicação, conforme mostrado no código a seguir.  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 Todos os três pontos finais `ListenUri` são hospedados `binding` da mesma forma `ListenUri` e usam o mesmo - os pontos finais ao mesmo tempo devem ter a mesma vinculação, porque eles estão compartilhando uma única pilha de canais que ouve mensagens nesse endereço físico na máquina. O `address` de cada ponto final é uma URN; embora os endereços representam locais físicos, na verdade o endereço pode ser qualquer tipo de URI, porque o endereço é usado para fins de correspondência e filtragem, como é demonstrado nesta amostra.  
  
 Como todos os três `ListenUri`pontos finais compartilham o mesmo , quando uma mensagem chega lá, a Windows Communication Foundation (WCF) deve decidir para qual ponto final a mensagem está destinada. Cada ponto final tem um filtro de mensagem composto por duas partes: o filtro de endereço e o filtro de contrato. O filtro de `To` endereço corresponde ao da mensagem SOAP ao endereço do ponto final do serviço. Por exemplo, apenas as `To "Urn:OtherEcho"` mensagens endereçadas são candidatas ao terceiro ponto final deste serviço. O filtro de contrato corresponde às Ações associadas às operações de um determinado contrato. Por exemplo, mensagens com `IEcho`a ação de . `Echo`corresponde aos filtros de contrato do segundo e terceiro pontos finais deste `IEcho` serviço, pois ambos os pontos finais hospedam o contrato.  
  
 Assim, a combinação de filtro de endereço e filtro de contrato `ListenUri` torna possível encaminhar cada mensagem que chega a este serviço para o ponto final correto. O terceiro ponto final é diferenciado dos outros dois porque aceita mensagens enviadas para um endereço diferente dos outros pontos finais. O primeiro e o segundo pontos finais são diferenciados um do outro com base em seus contratos (a Ação da mensagem recebida).  
  
## <a name="client"></a>Cliente  
 Assim como os pontos finais no servidor têm dois endereços diferentes, os pontos finais do cliente também têm dois endereços. Tanto no servidor quanto no cliente, `EndpointAddress`o endereço lógico é chamado de . Mas enquanto o endereço `ListenUri` físico é chamado de servidor, no cliente, o endereço físico é chamado de `Via`.  
  
 Como no servidor, por padrão, esses dois endereços são os mesmos. Para especificar um `Via` no cliente diferente do endereço `ClientViaBehavior` do ponto final, é usado:  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Como de costume, o endereço vem do arquivo de configuração do cliente, que foi gerado pelo Svcutil.exe. O `Via` (que corresponde `ListenUri` ao do serviço) não aparece nos metadados do serviço e, portanto, essas informações devem ser comunicadas ao cliente fora da banda (assim como o endereço de metadados do serviço).  
  
 O cliente nesta amostra envia mensagens para cada um dos três pontos finais do aplicativo do servidor, para demonstrar que ele `Via`pode se comunicar com (e diferenciar) todos os três pontos finais, mesmo que todos eles tenham o mesmo .  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Para a máquina cruzada, você deve substituir o host local no arquivo Client.cs com o nome da máquina de serviço.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
