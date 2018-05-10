---
title: Transporte de WS com credencial de mensagem
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 708869f2350f01e75b949f4817fcf8aac35ea018
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="ws-transport-with-message-credential"></a>Transporte de WS com credencial de mensagem
Este exemplo demonstra o uso da segurança de transporte SSL em combinação com a credencial de cliente que está sendo executada na mensagem. Este exemplo usa o `wsHttpBinding` associação.  
  
 Por padrão, o `wsHttpBinding` associação fornece comunicação HTTP. Quando configurado para segurança de transporte, a associação oferece suporte à comunicação de HTTPS. O HTTPS oferece confidencialidade e proteção de integridade para as mensagens que são transmitidas eletronicamente. Porém, o conjunto de mecanismos de autenticação que pode ser usado para autenticar o cliente para o serviço é limitado à dá suporte a transporte HTTPS. Windows Communication Foundation (WCF) oferece um `TransportWithMessageCredential` modo de segurança que foi projetado para superar essa limitação. Quando esse modo de segurança está configurado, a segurança de transporte é usada para fornecer confidencialidade e a integridade das mensagens transmitidas e para executar a autenticação de serviço. No entanto, a autenticação do cliente é executada, colocando a credencial do cliente diretamente na mensagem. Isso permite que você use qualquer tipo de credencial que é compatível com o modo de segurança de mensagem para a autenticação do cliente, mantendo o benefício de desempenho do modo de segurança de transporte.  
  
 Neste exemplo, um `UserName` tipo de credencial é usado para autenticar o cliente para o serviço.  
  
 Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de cálculo. O `wsHttpBinding` associação for especificada e configurada nos arquivos de configuração do aplicativo para o cliente e o serviço.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O código do programa no exemplo é quase idêntico do [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) serviço. Há uma operação adicional fornecida pelo contrato de serviço - `GetCallerIdentity`. Essa operação retorna o nome da identidade do chamador ao chamador.  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 Você deve criar um certificado e atribuí-lo usando o Assistente de certificado de servidor da Web antes de criar e executar o exemplo. A definição de ponto de extremidade e a definição de associação na configuração do arquivo de configurações permitem `TransportWithMessageCredential` modo de segurança, conforme mostrado no seguinte exemplo de configuração para o cliente.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 O endereço especificado usa o esquema de https://. A configuração de associação define o modo de segurança `TransportWithMessageCredential`. O mesmo modo de segurança deve ser especificado no arquivo de Web. config do serviço.  
  
 Como o certificado usado neste exemplo é um certificado de teste criado com o Makecert.exe, um alerta de segurança é exibida quando você tentar acessar um https: endereço, como https://localhost/servicemodelsamples/service.svc, no seu navegador. Para permitir que o cliente do WCF para trabalhar com um certificado de teste no local, um código adicional foi adicionado ao cliente para suprimir o alerta de segurança. Esse código e a classe que o acompanha, não é necessário ao usar certificados de produção.  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:   
YourDomainName\YourAccountName  
   Enter password:   
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Certifique-se de que você executou o [instruções de instalação do certificado de servidor de serviços de informações da Internet (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
3.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também
