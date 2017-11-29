---
title: "Endereçando"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3ac0cb2b9df130820a4b12efd4b845b50ad7c79a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="addressing"></a>Endereçando
O exemplo de endereçamento demonstra vários aspectos e recursos de endereços de ponto de extremidade. O exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). Neste exemplo, o serviço é hospedado automaticamente. O cliente e o serviço são aplicativos de console. O serviço define vários pontos de extremidade usando uma combinação de endereços de ponto de extremidade relativas e absolutas.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O arquivo de configuração de serviço Especifica um endereço base e quatro pontos de extremidade. O endereço base é especificado usando o elemento de adicionar, em serviço/host/baseAddresses conforme demonstrado no exemplo de configuração.  
  
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
  
 A primeira definição de ponto de extremidade mostrada no exemplo de configuração especifica um endereço relativo, o que significa que o endereço do ponto de extremidade é uma combinação do endereço base e o endereço relativo seguindo as regras de composição de URI.  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Nesse caso, o endereço relativo está vazio (""), portanto, o endereço do ponto de extremidade é o mesmo que o endereço base. O endereço do ponto de extremidade real é servicemodelsamples/http://localhost:8000/serviço.  
  
 A segunda definição de ponto de extremidade também especifica um endereço relativo, conforme mostrado no exemplo de configuração.  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 O endereço relativo, "teste", é acrescentada ao endereço base. O endereço do ponto de extremidade real é http://localhost:8000/servicemodelsamples/serviço/teste.  
  
 A definição de ponto de extremidade terceira Especifica um endereço absoluto, conforme mostrado no exemplo de configuração.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 O endereço base não desempenha nenhuma função no endereço. O endereço do ponto de extremidade real é Olá/http://localhost:8001/servicemodelsamples.  
  
 O quarto endereço de ponto de extremidade Especifica um endereço absoluto e um transporte diferente — TCP. O endereço base não desempenha nenhuma função no endereço. O endereço do ponto de extremidade real é net.tcp://localhost: servicemodelsamples/9000/serviço.  
  
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
  
 O cliente acessa apenas um dos pontos de extremidade de quatro serviço, mas todos os quatro são definidos no seu arquivo de configuração. O cliente seleciona um ponto de extremidade quando ele cria o `CalculatorProxy` objeto. Alterando o nome da configuração de `CalculatorEndpoint1` por meio de `CalculatorEndpoint4`, você pode exercer cada ponto de extremidade.  
  
 Quando você executar o exemplo, o serviço enumera o endereço, o nome e o nome do contrato para cada um dos seus pontos de extremidade de associação. O ponto de extremidade do exchange (MEX) de metadados é apenas outro ponto de extremidade do ponto de vista do ServiceHost para que ele é exibido na lista.  
  
```  
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
  
 Quando você executa o cliente, as respostas e solicitações de operação são exibidas em janelas do console de serviço e o cliente. Pressione ENTER em cada janela de console para desligar o serviço e o cliente.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Se você usar o Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
  
## <a name="see-also"></a>Consulte também
