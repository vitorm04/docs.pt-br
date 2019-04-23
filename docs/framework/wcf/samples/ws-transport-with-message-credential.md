---
title: Transporte de WS com credencial de mensagem
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 54bd025db4da8ed1d1484b11666a37c2c14a6023
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974575"
---
# <a name="ws-transport-with-message-credential"></a>Transporte de WS com credencial de mensagem
Este exemplo demonstra o uso da segurança de transporte do SSL em combinação com a credencial de cliente que está sendo executada na mensagem. Este exemplo usa o `wsHttpBinding` associação.  
  
 Por padrão, o `wsHttpBinding` associação fornece comunicação HTTP. Quando configurado para segurança de transporte, a associação dá suporte a comunicação HTTPS. HTTPS fornece confidencialidade e proteção de integridade para as mensagens que são transmitidos eletronicamente. No entanto, o conjunto de mecanismos de autenticação que pode ser usado para autenticar o cliente para o serviço é limitado dá suporte ao transporte HTTPS. Windows Communication Foundation (WCF) oferece um `TransportWithMessageCredential` modo de segurança que foi projetado para superar essa limitação. Quando esse modo de segurança está configurado, a segurança de transporte é usada para fornecer confidencialidade e integridade para as mensagens transmitidas e realizar a autenticação de serviço. No entanto, a autenticação do cliente é executada colocando-se a credencial do cliente diretamente na mensagem. Isso permite que você use qualquer tipo de credencial que é compatível com o modo de segurança de mensagem para a autenticação de cliente, mantendo o benefício de desempenho do modo de segurança de transporte.  
  
 Neste exemplo, um `UserName` tipo de credencial é usado para autenticar o cliente para o serviço.  
  
 Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora. O `wsHttpBinding` associação é especificada e configurada nos arquivos de configuração do aplicativo para o cliente e o serviço.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O código do programa de exemplo é quase idêntico do [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) service. Há uma operação adicional fornecida pelo contrato de serviço - `GetCallerIdentity`. Essa operação retorna o nome da identidade do chamador para o chamador.  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 Você deve criar um certificado e atribuí-lo usando o Assistente de certificado do servidor Web antes de criar e executar o exemplo. A definição de ponto de extremidade e a definição de associação na configuração do arquivo de configurações permitem `TransportWithMessageCredential` modo de segurança, conforme mostrado no seguinte exemplo de configuração para o cliente.  
  
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
  
 O endereço especificado usa o esquema de https://. A configuração de associação define o modo de segurança para `TransportWithMessageCredential`. O mesmo modo de segurança deve ser especificado no arquivo de Web. config do serviço.  
  
 Como o certificado usado neste exemplo é um certificado de teste criado com Makecert.exe, um alerta de segurança é exibida quando você tenta acessar um https: endereço, tais como `https://localhost/servicemodelsamples/service.svc`, do seu navegador. Para permitir que o cliente do WCF para trabalhar com um certificado de teste em vigor, o código adicional foi adicionado ao cliente para suprimir o alerta de segurança. Esse código e a classe que acompanha este artigo, não é necessário ao usar certificados de produção.  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
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
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Certifique-se de que você tenha executado o [instruções de instalação do certificado de servidor de serviços de informações da Internet (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
3. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
