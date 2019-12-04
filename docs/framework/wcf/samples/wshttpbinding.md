---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 6ea07f206064a389da8af04a4afd292022b8ca44
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714563"
---
# <a name="wshttpbinding"></a>WSHttpBinding
Este exemplo demonstra como implementar um serviço típico e um cliente típico usando Windows Communication Foundation (WCF). Este exemplo consiste em um programa de console do cliente (Client. exe) e uma biblioteca de serviços hospedado pelo Serviços de Informações da Internet (IIS). O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta. O contrato é definido pela interface `ICalculator`, que expõe operações matemáticas (adicionar, subtrair, multiplicar e dividir). O cliente faz solicitações síncronas para uma determinada operação matemática e o serviço responde com o resultado. A atividade do cliente fica visível na janela do console.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
 Este exemplo expõe o contrato de `ICalculator` usando o [> de wsHttpBinding\<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). A configuração dessa associação foi expandida no arquivo Web. config.  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->   
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"   
              transactionFlow="false"   
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"   
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"   
              textEncoding="utf-8"   
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"   
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"   
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 No elemento base `binding`, o valor `maxReceivedMessageSize` permite que você configure o tamanho máximo de uma mensagem de entrada (em bytes). O valor `hostNameComparisonMode` permite que você configure se o nome de host é considerado ao Desmultiplexar mensagens para o serviço. O valor `messageEncoding` permite que você configure se deseja usar a codificação de texto ou MTOM para mensagens. O valor `textEncoding` permite configurar a codificação de caracteres para mensagens. O valor `bypassProxyOnLocal` permite que você configure se deseja usar um proxy HTTP para comunicação local. O valor `transactionFlow` define se a transação atual está fluindo (se uma operação estiver configurada para o fluxo de transações).  
  
 No elemento [\<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) , o valor booliano habilitado define se as sessões confiáveis estão habilitadas. O valor `ordered` define se a ordenação da mensagem é preservada. O valor `inactivityTimeout` define por quanto tempo uma sessão pode ficar ociosa antes de ter falhado.  
  
 No [\<segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), o valor `mode` configura qual modo de segurança deve ser usado. Neste exemplo, a segurança de mensagens está sendo usada, o que é o motivo pelo qual o [\<> de mensagem](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) é especificado dentro do [> de segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).  
  
 Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Instale o ASP.NET 4,0 usando o comando a seguir.  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
