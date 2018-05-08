---
title: Segurança de mensagens do Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7bf731c1accd6eefc97c27af58ba139992ae1866
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="message-security-windows"></a>Segurança de mensagens do Windows
Este exemplo demonstra como configurar um <xref:System.ServiceModel.WSHttpBinding> associação para usar a segurança de nível de mensagem com a autenticação do Windows. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). Neste exemplo, o serviço é hospedado no Internet Information Services (IIS) e o cliente é um aplicativo de console (.exe).  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 A segurança padrão para o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) é a segurança de mensagem usando a autenticação do Windows. Neste exemplo, os arquivos de configuração definido explicitamente o `mode` atributo do [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) para `Message` e `clientCredentialType` atributo `Windows`. Esses valores são os valores padrão para essa associação, mas eles foram explicitamente configurados, como mostrado no seguinte exemplo de configuração para demonstrar o seu uso.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding>  
            <security mode="Message">  
                <message clientCredentialType="Windows"/>  
            </security>  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 A configuração do ponto de extremidade cliente consiste em um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato. A ligação do cliente é configurado com as `securityMode` e `authenticationMode`.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
            "http://localhost/servicemodelsamples/service.svc"   
            binding="wsHttpBinding"   
            bindingConfiguration="Binding1"   
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      <!--The default security for the WSHttpBinding is-->  
      <!--Message security using Windows authentication. -->  
      <!--This configuration explicitly defines the security mode -->  
      <!--as Message and the clientCredentialType as Windows  -->  
      <!--for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 O código de origem do serviço foi modificado para demonstrar como o <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> pode ser usado para acessar a identidade do chamador.  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. O primeiro método chamado - `GetCallerIdentity` -retorna o nome da identidade do chamador ao cliente. Pressione ENTER na janela do console para desligar o cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também
