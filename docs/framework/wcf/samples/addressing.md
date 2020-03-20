---
title: Endereçando
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 4403ac2bf8e0e5193006f6ec19b24a9bcb00bf35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183972"
---
# <a name="addressing"></a>Endereçando
A amostra Endereçamento demonstra vários aspectos e características de endereços de ponto final. A amostra é baseada no ["Getting Started".](../../../../docs/framework/wcf/samples/getting-started-sample.md) Nesta amostra o serviço é auto-hospedado. Tanto o serviço quanto o cliente são aplicativos de console. O serviço define vários pontos finais usando uma combinação de endereços de ponto final relativo e absoluto.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 O arquivo de configuração de serviço especifica um endereço base e quatro pontos finais. O endereço base é especificado usando o elemento add, em service/host/baseAddresses, conforme demonstrado na configuração de amostra a seguir.  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 A primeira definição de ponto final mostrada na configuração da amostra a seguir especifica um endereço relativo, o que significa que o endereço de ponto final é uma combinação do endereço base e do endereço relativo seguindo as regras de composição uri.  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Neste caso, o endereço relativo está vazio (""), de modo que o endereço de ponto final é o mesmo que o endereço base. O endereço final `http://localhost:8000/servicemodelsamples/service`real é .
  
 A definição do segundo ponto final também especifica um endereço relativo, conforme mostrado na configuração da amostra a seguir.  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 O endereço relativo, "teste", é anexado ao endereço base. O endereço final `http://localhost:8000/servicemodelsamples/service/test`real é .
  
 A definição do terceiro ponto final especifica um endereço absoluto, conforme mostrado na configuração da amostra a seguir.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 O endereço base não desempenha nenhum papel no endereço. O endereço final `http://localhost:8001/hello/servicemodelsamples`real é .
  
 O quarto endereço de ponto final especifica um endereço absoluto e um tCP diferente. O endereço base não desempenha nenhum papel no endereço. O endereço final `net.tcp://localhost:9000/servicemodelsamples/service`real é .
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</service>  
```  
  
 O cliente acessa apenas um dos quatro pontos finais do serviço, mas todos os quatro são definidos em seu arquivo de configuração. O cliente seleciona um ponto `CalculatorProxy` final quando cria o objeto. Ao alterar o `CalculatorEndpoint1` nome `CalculatorEndpoint4`de configuração a partir de todo, você pode exercitar cada um dos pontos finais.  
  
 Quando você executa a amostra, o serviço enumera o endereço, o nome de vinculação e o nome do contrato para cada um de seus pontos finais. O ponto final da troca de metadados (MEX) é apenas mais um ponto final da perspectiva do ServiceHost para que ele apareça na lista.  
  
```console  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 Quando você executa o cliente, as solicitações e respostas da operação são exibidas tanto nas janelas do serviço quanto do console do cliente. Pressione ENTER em cada janela do console para desligar o serviço e o cliente.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Se você usar Svcutil.exe para regenerar a configuração desta amostra, certifique-se de modificar o nome do ponto final na configuração do cliente para corresponder ao código do cliente.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
