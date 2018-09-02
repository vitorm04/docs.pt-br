---
title: Sessão confiável de WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: ec9163eded7f77053b94b7cb0ff0995dca575612
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407801"
---
# <a name="ws-reliable-session"></a>Sessão confiável de WS
Este exemplo demonstra o uso de sessões confiáveis. Sessões confiáveis fornecem suporte para o sistema de mensagens confiável e sessões. Sistema de mensagens confiável tenta novamente a comunicação em caso de falha e permite que as garantias de entrega seja especificado, como em ordem chegada de mensagens. Sessões de mantêm o estado dos clientes entre chamadas. O exemplo implementa sessões para manter o estado do cliente e especifica as garantias de entrega em ordem.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora. Os recursos de sessão confiável estão habilitados e configurados nos arquivos de configuração do aplicativo para o cliente e o serviço.  
  
 Neste exemplo, o serviço está hospedado no Internet Information Services (IIS) e o cliente é um aplicativo de console (.exe).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O exemplo usa o `wsHttpBinding`. A associação é especificada nos arquivos de configuração para o cliente e o serviço. O tipo de associação é especificado no elemento de ponto de extremidade `binding` conforme mostrado no seguinte exemplo de configuração do atributo.  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 O ponto de extremidade contém um `bindingConfiguration` atributo que faz referência a uma configuração de associação chamado "Binding1". A configuração de associação permite que as sessões confiáveis, definindo o `enabled` atributo o [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) para `true`. Garantias de entrega ordenada sessões são controladas pela definição de atributo ordenada `true` ou `false`. O padrão é `true`.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 A classe de implementação de serviço implementa <xref:System.ServiceModel.InstanceContextMode.PerSession> instanciação para manter uma instância de classe separada para cada cliente, conforme mostrado no código de exemplo a seguir.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também
