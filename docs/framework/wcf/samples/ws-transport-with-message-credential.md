---
title: Transporte de WS com credencial de mensagem
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 076d4490f6edc6efa8eeb50ae8baa23d5c4e369a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183140"
---
# <a name="ws-transport-with-message-credential"></a>Transporte de WS com credencial de mensagem
Esta amostra demonstra o uso da segurança de transporte SSL em combinação com a credencial do cliente que está sendo transportada na mensagem. Esta amostra `wsHttpBinding` usa a ligação.  
  
 Por padrão, `wsHttpBinding` a vinculação fornece comunicação HTTP. Quando configurado para segurança de transporte, a vinculação suporta comunicação HTTPS. O HTTPS fornece proteção de confidencialidade e integridade para as mensagens que são transmitidas pelo fio. No entanto, o conjunto de mecanismos de autenticação que podem ser usados para autenticar o cliente ao serviço está limitado ao que o transporte HTTPS suporta. O Windows Communication Foundation (WCF) oferece um `TransportWithMessageCredential` modo de segurança projetado para superar essa limitação. Quando esse modo de segurança é configurado, a segurança de transporte é usada para fornecer confidencialidade e integridade para as mensagens transmitidas e para executar a autenticação do serviço. No entanto, a autenticação do cliente é realizada colocando a credencial do cliente diretamente na mensagem. Isso permite que você use qualquer tipo de credencial que seja suportado pelo modo de segurança de mensagem para a autenticação do cliente, mantendo o benefício de desempenho do modo de segurança de transporte.  
  
 Nesta amostra, `UserName` um tipo de credencial é usado para autenticar o cliente ao serviço.  
  
 Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora. A `wsHttpBinding` vinculação é especificada e configurada nos arquivos de configuração do aplicativo para o cliente e serviço.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 O código do programa na amostra é quase idêntico ao do serviço [Getting Started.](../../../../docs/framework/wcf/samples/getting-started-sample.md) Há uma operação adicional fornecida pelo `GetCallerIdentity`contrato de serviço - . Esta operação retorna o nome da identidade do chamador para o chamador.  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 Você deve criar um certificado e atribuí-lo usando o Assistente de Certificado do Servidor Web antes de construir e executar a amostra. A definição de ponto final e a `TransportWithMessageCredential` definição de vinculação nas configurações do arquivo de configuração permitem o modo de segurança, conforme mostrado na configuração de exemplo a seguir para o cliente.  
  
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
  
 O endereço especificado usa o esquema https://. A configuração de vinculação define o modo de segurança para `TransportWithMessageCredential`. O mesmo modo de segurança deve ser especificado no arquivo Web.config do serviço.  
  
 Como o certificado usado nesta amostra é um certificado de teste criado com o Makecert.exe, um `https://localhost/servicemodelsamples/service.svc`alerta de segurança aparece quando você tenta acessar um endereço https: como , do seu navegador. Para permitir que o cliente WCF trabalhe com um certificado de teste em vigor, algum código adicional foi adicionado ao cliente para suprimir o alerta de segurança. Este código, e a classe de acompanhamento, não é necessário ao usar certificados de produção.  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
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
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Certifique-se de que você tenha realizado as Instruções de Instalação do [Certificado de Servidor do Serviço de Informações da Internet (IIS).](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)  
  
3. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
