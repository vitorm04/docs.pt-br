---
title: Vários contratos
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: ed59803b867dfe7994aceea010aa656c53927a0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144338"
---
# <a name="multiple-contracts"></a>Vários contratos
A amostra de Contratos Múltiplos demonstra como implementar mais de um contrato em um serviço e como configurar pontos finais para se comunicar com cada um dos contratos implementados. Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md). O serviço foi modificado para definir `ICalculator` dois `ICalculatorSession` contratos, o contrato e o contrato.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 A classe de serviços implementa tanto os `ICalculator` contratos quanto `ICalculatorSession` os contratos. Como um dos contratos requer uma sessão, o serviço usa o <xref:System.ServiceModel.InstanceContextMode.PerSession> modo instância para manter o estado durante a vida útil da sessão.  
  
 A configuração do serviço foi modificada para definir dois pontos finais para expor cada contrato. O `ICalculator` ponto final é exposto no `basicHttpBinding`endereço base usando um . O `ICalculatorSession` ponto final é exposto no endereço `wsHttpBinding` base/sessão usando um com o atributo `bindingConfiguration` definido para `BindingWithSession`, como mostrado na configuração da amostra a seguir.  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 O código do cliente gerado agora inclui `ICalculator` uma classe `ICalculatorSession` cliente tanto para o contrato original quanto para o novo contrato. A configuração e o código do cliente foram modificados para se comunicar com cada contrato no ponto final de serviço apropriado.  
  
 O cliente é um aplicativo de janelas de console (.exe). O serviço é hospedado pelos Serviços de Informação da Internet (IIS).  
  
 A janela do console cliente exibe as operações enviadas para cada um dos pontos finais, primeiro o ponto final básico, seguido pelo ponto final seguro.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
