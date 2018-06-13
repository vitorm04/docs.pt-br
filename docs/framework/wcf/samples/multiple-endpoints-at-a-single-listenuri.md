---
title: Vários pontos de extremidade em único ListenUri
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: f3eb2036ffbb7c5e8cae77ebc1a86e07d31626c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506500"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Vários pontos de extremidade em único ListenUri
Este exemplo demonstra um serviço que hospeda vários pontos de extremidade em um único `ListenUri`. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de cálculo.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Conforme demonstrado a [vários pontos de extremidade](../../../../docs/framework/wcf/samples/multiple-endpoints.md) exemplo, um serviço pode hospedar vários pontos de extremidade, cada um com diferentes endereços e possivelmente também ligações diferentes. Este exemplo mostra que é possível hospedar vários pontos de extremidade com o mesmo endereço. Este exemplo também demonstra as diferenças entre os dois tipos de endereços que tem um ponto de extremidade de serviço: `EndpointAddress` e `ListenUri`.  
  
 O `EndpointAddress` é o endereço lógico de um serviço. É o endereço de mensagens SOAP são endereçadas a. O `ListenUri` é o endereço físico do serviço. Ele tem as informações de porta e endereço em que o ponto de extremidade de serviço, na verdade, verifica se há mensagens na máquina atual. Na maioria dos casos, não é necessário para esses endereços para diferem; Quando um `ListenUri` não for especificado explicitamente, o padrão é o URI do `EndpointAddress` do ponto de extremidade. Em alguns casos, é útil para diferenciá-los, como quando configurar um roteador, que pode aceitar mensagens endereçado a um número de diferentes serviços.  
  
## <a name="service"></a>Serviço  
 O serviço neste exemplo tem dois contratos, `ICalculator` e `IEcho`. Além de habituais `IMetadataExchange` ponto de extremidade, há três pontos de extremidade do aplicativo, conforme mostrado no código a seguir.  
  
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
  
 Todos os três pontos de extremidade são hospedados no mesmo `ListenUri` e usar o mesmo `binding` -pontos de extremidade no mesmo `ListenUri` deve ter a mesma associação, porque eles compartilham uma pilha de canal que escuta mensagens nesse endereço físico do máquina. O `address` de cada ponto de extremidade é um URN; embora normalmente endereços representam locais físicos, na verdade o endereço pode ser qualquer tipo de URI, como o endereço é usado para correspondência e fins de filtragem, conforme é mostrado neste exemplo.  
  
 Como todos os três pontos de extremidade compartilham o mesmo `ListenUri`, quando uma mensagem chega, o Windows Communication Foundation (WCF) deve decidir qual ponto de extremidade é destinada a mensagem. Cada ponto de extremidade tem um filtro de mensagem que é composto de duas partes: o filtro de endereço e o filtro de contrato. O filtro de endereço corresponde a `To` da mensagem SOAP para o endereço do ponto de extremidade de serviço. Por exemplo, apenas as mensagens endereçadas `To "Urn:OtherEcho"` são candidatos para o terceiro ponto de extremidade do serviço. O filtro de contrato coincide com as ações associadas com as operações de um contrato específico. Por exemplo, as mensagens com a ação de `IEcho`. `Echo` corresponder aos filtros de contrato de segundo e terceiro pontos de extremidade do serviço, porque ambos os hosts de pontos de extremidade de `IEcho` contrato.  
  
 Assim, a combinação de filtros de endereço e contrato possibilita rotear cada mensagem que chega a esse serviço `ListenUri` ao ponto de extremidade correto. O terceiro ponto de extremidade é diferenciado dos outros dois porque ele aceita mensagens enviadas para um endereço diferente de outros pontos de extremidade. Os pontos de extremidade primeiro e segundo são diferenciados entre si com base em seus contratos (a ação da mensagem de entrada).  
  
## <a name="client"></a>Cliente  
 Assim como pontos de extremidade no servidor tiverem dois endereços diferentes, os pontos de extremidade também tem dois endereços. No servidor e cliente, o endereço lógico é chamado de `EndpointAddress`. Mas, ao passo que o endereço físico é chamado de `ListenUri` no servidor, no cliente, o endereço físico é chamado de `Via`.  
  
 No servidor, por padrão, esses dois endereços são os mesmos. Para especificar um `Via` no cliente que é diferente do endereço do ponto de extremidade, `ClientViaBehavior` é usado:  
  
```  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Como de costume, o endereço proveniente do arquivo de configuração do cliente, que foi gerado pelo Svcutil.exe. O `Via` (que corresponde do `ListenUri` do serviço) não aparecem nos metadados do serviço e, portanto, essas informações precisam ser comunicadas para a cliente fora de banda (assim como o endereço de metadados do serviço).  
  
 O cliente neste exemplo envia mensagens para cada um dos pontos de extremidade do servidor de três aplicativos demonstrar que ele pode se comunicar com (e diferenciar) todos os três pontos de extremidade, mesmo que todos têm o mesmo `Via`.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Para entre computadores, você deve substituir localhost no arquivo Client.cs com o nome da máquina do serviço.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
  
## <a name="see-also"></a>Consulte também
