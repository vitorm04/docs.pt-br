---
title: "Vários contratos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e5551a3d4fcb515ff6e78c32d0fd7c9e241b4600
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="multiple-contracts"></a>Vários contratos
O exemplo de vários contratos demonstra como implementar mais de um contrato de um serviço e como configurar pontos de extremidade de comunicação com cada um dos contratos implementados. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). O serviço foi modificado para definir dois contratos, o `ICalculator` contrato e o `ICalculatorSession` contrato.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 A classe de serviço implementa ambos o `ICalculator` e `ICalculatorSession` contratos. Como um dos contratos requer uma sessão, o serviço usa o <xref:System.ServiceModel.InstanceContextMode.PerSession> modo de instância para manter o estado durante a vida útil da sessão.  
  
 A configuração do serviço foi modificada para definir dois pontos de extremidade para expor a cada contrato. O `ICalculator` ponto de extremidade é exposto ao endereço base usando um `basicHttpBinding`. O `ICalculatorSession` ponto de extremidade é exposto no baseaddress/sessão usando um `wsHttpBinding` com o `bindingConfiguration` atributo definido como `BindingWithSession`, conforme mostrado no exemplo de configuração.  
  
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
  
 O código de cliente gerada agora inclui uma classe de cliente para original `ICalculator` contrato e o novo `ICalculatorSession` contrato. A configuração do cliente e o código foram modificadas para se comunicar com cada contrato no ponto de extremidade de serviço apropriado.  
  
 O cliente é um aplicativo do windows do console (.exe). O serviço é hospedado por serviços de informações da Internet (IIS).  
  
 A janela do console de cliente exibe as operações enviadas para cada ponto de extremidade, primeiro, o ponto de extremidade básico, seguido pelo ponto de extremidade seguro.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
  
## <a name="see-also"></a>Consulte também
