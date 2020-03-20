---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: c54cbf1fe881ef2ce5dffb0bc0c6dac4049135b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143363"
---
# <a name="wshttpbinding"></a>WSHttpBinding
Esta amostra demonstra como implementar um serviço típico e um cliente típico usando o Windows Communication Foundation (WCF). Esta amostra consiste em um programa de console cliente (client.exe) e uma biblioteca de serviços hospedada pelo Internet Information Services (IIS). O serviço implementa um contrato que define um padrão de comunicação solicitação-resposta. O contrato é `ICalculator` definido pela interface, que expõe as operações matemáticas (adicionar, subtrair, multiplicar e dividir). O cliente faz solicitações síncronas para uma determinada operação matemática e o serviço responde com o resultado. A atividade do cliente é visível na janela do console.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Esta amostra expõe `ICalculator` o contrato usando o [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). A configuração desta vinculação foi expandida no arquivo Web.config.  
  
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
  
 No elemento `binding` base, `maxReceivedMessageSize` o valor permite configurar o tamanho máximo de uma mensagem recebida (em bytes). O `hostNameComparisonMode` valor permite configurar se o nome do host é considerado ao desmultiplelizar mensagens para o serviço. O `messageEncoding` valor permite configurar se deve usar a codificação Texto ou MTOM para mensagens. O `textEncoding` valor permite configurar a codificação de caracteres para mensagens. O `bypassProxyOnLocal` valor permite configurar se deve usar um proxy HTTP para comunicação local. O `transactionFlow` valor configura se a transação atual é fluída (se uma operação está configurada para o fluxo de transações).  
  
 No elemento [ \<>de Sessão confiável,](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) o valor booleano ativado configura se as sessões confiáveis estão habilitadas. O `ordered` valor configura se o pedido de mensagem é preservado. O `inactivityTimeout` valor configura quanto tempo uma sessão pode ficar ociosa antes de ser defeituosa.  
  
 No [ \<>de ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `mode` segurança , o valor configura qual modo de segurança deve ser usado. Nesta amostra, a segurança das mensagens está sendo usada, e [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)é por isso que a [ \<mensagem>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) é especificada dentro do>de segurança .  
  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Instale ASP.NET 4.0 usando o seguinte comando.  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
