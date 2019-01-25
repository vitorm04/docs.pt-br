---
title: Vários pontos de extremidade em único ListenUri
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: fbf636acf5e2cf4ef0f417b6b50a93d3e25c3ea6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643462"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Vários pontos de extremidade em único ListenUri
Este exemplo demonstra um serviço que hospeda vários pontos de extremidade em um único `ListenUri`. Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Conforme demonstrado a [vários pontos de extremidade](../../../../docs/framework/wcf/samples/multiple-endpoints.md) exemplo, um serviço pode hospedar vários pontos de extremidade, cada um com diferentes endereços e possivelmente também ligações diferentes. Este exemplo mostra que é possível hospedar vários pontos de extremidade no mesmo endereço. Este exemplo também demonstra as diferenças entre os dois tipos de endereços que tem um ponto de extremidade de serviço: `EndpointAddress` e `ListenUri`.  
  
 O `EndpointAddress` é o endereço lógico de um serviço. É o endereço de mensagens SOAP são endereçadas a. O `ListenUri` é o endereço físico do serviço. Ele tem as informações de porta e endereço em que o ponto de extremidade de serviço, na verdade, escuta de mensagens no computador atual. Na maioria dos casos, não é necessário para esses endereços forem diferentes; Quando um `ListenUri` não for especificado explicitamente, o padrão é o URI do `EndpointAddress` do ponto de extremidade. Em alguns casos, é útil para diferenciá-los, como quando configurar um roteador, que pode aceitar mensagens endereçadas a vários serviços diferentes.  
  
## <a name="service"></a>Serviço  
 O serviço neste exemplo tem dois contratos, `ICalculator` e `IEcho`. Além do habitual `IMetadataExchange` ponto de extremidade, há três pontos de extremidade do aplicativo, conforme mostrado no código a seguir.  
  
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
  
 Todos os três pontos de extremidade são hospedados no mesmo `ListenUri` e use o mesmo `binding` -pontos de extremidade ao mesmo `ListenUri` deve ter a mesma ligação, porque eles estão compartilhando uma pilha de canal único que escuta para mensagens nesse endereço físico a máquina. O `address` de cada ponto de extremidade é um URN; embora normalmente endereços representam locais físicos, de fato o endereço pode ser qualquer tipo de URI, como o endereço é usado para correspondência e fins de filtragem, conforme demonstrado neste exemplo.  
  
 Como todos os três pontos de extremidade compartilham o mesmo `ListenUri`, quando uma mensagem chega lá, o Windows Communication Foundation (WCF) deve decidir qual ponto de extremidade de mensagem é destinada. Cada ponto de extremidade tem um filtro de mensagem é composto de duas partes: o filtro de endereço e o filtro de contrato. O filtro de endereço corresponde a `To` da mensagem SOAP para o endereço do ponto de extremidade de serviço. Por exemplo, somente mensagens endereçadas `To "Urn:OtherEcho"` são candidatos para o terceiro ponto de extremidade desse serviço. O filtro de contrato corresponde as ações associadas com as operações de um determinado contrato. Por exemplo, mensagens com a ação de `IEcho`. `Echo` coincide com os filtros de contrato de segundo e terceiro pontos de extremidade desse serviço, porque ambos os hosts de pontos de extremidade a `IEcho` contrato.  
  
 Portanto, a combinação de filtros de endereço e contrato torna possível rotear cada mensagem que chega a esse serviço `ListenUri` ao ponto de extremidade correto. O terceiro ponto de extremidade é diferenciado dos outros dois, pois ele aceita mensagens enviadas para um endereço diferente de outros pontos de extremidade. Os pontos de extremidade primeiros e segundo são diferenciados entre si com base em seus contratos (a ação da mensagem de entrada).  
  
## <a name="client"></a>Cliente  
 Assim como os pontos de extremidade no servidor tiverem dois endereços diferentes, os pontos de extremidade também tem dois endereços. No servidor e cliente, o endereço lógico é chamado de `EndpointAddress`. Mas, enquanto o endereço físico é chamado de `ListenUri` no servidor, no cliente, o endereço físico é chamado de `Via`.  
  
 Como no servidor, por padrão, esses dois endereços são os mesmos. Para especificar uma `Via` no cliente que é diferente do endereço do ponto de extremidade, `ClientViaBehavior` é usado:  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Como de costume, o endereço vem do arquivo de configuração de cliente, que foi gerado pelo Svcutil.exe. O `Via` (que corresponde ao `ListenUri` do serviço) não aparece nos metadados do serviço e, portanto, essas informações devem ser comunicadas para a cliente fora de banda (assim como o endereço de metadados do serviço).  
  
 O cliente neste exemplo envia mensagens para cada um dos pontos de extremidade de aplicativo de três do servidor demonstrar que ela pode se comunicar com (e diferenciar) todos os três pontos de extremidade, mesmo que todos eles têm o mesmo `Via`.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Para várias máquinas, você deve substituir o localhost no arquivo Client.cs com o nome da máquina do serviço.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
  
## <a name="see-also"></a>Consulte também
