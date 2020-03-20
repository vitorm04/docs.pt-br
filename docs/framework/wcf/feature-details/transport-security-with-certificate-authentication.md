---
title: Segurança de transporte com autenticação de certificado
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: ad2f0922afbd94e1699b383cf2fc9762771b637d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184326"
---
# <a name="transport-security-with-certificate-authentication"></a>Segurança de transporte com autenticação de certificado

Este artigo discute o uso de certificados X.509 para autenticação de servidor e cliente ao usar a segurança do transporte. Para obter mais informações sobre os certificados X.509, confira [Certificados de chave pública X.509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates). Os certificados devem ser emitidos por uma autoridade de certificação, que muitas vezes é um emissor terceirizado de certificados. Em um domínio do Windows Server, os Serviços de Certificado de Diretório Ativo podem ser usados para emitir certificados para computadores clientes no domínio. Neste cenário, o serviço está hospedado no Internet Information Services (IIS), que é configurado com Secure Sockets Layer (SSL). O serviço é configurado com um certificado SSL (X.509) para permitir que os clientes verifiquem a identidade do servidor. O cliente também é configurado com um certificado X.509 que permite que o serviço verifique a identidade do cliente. O certificado do servidor deve ser confiável pelo cliente e o certificado do cliente deve ser confiável pelo servidor. A mecânica real de como o serviço e o cliente verificam a identidade uns dos outros está além do escopo deste artigo. Para obter mais informações, consulte [Assinatura Digital](https://en.wikipedia.org/wiki/Digital_signature) na Wikipédia.
  
 Este cenário implementa um padrão de mensagem de solicitação/resposta ilustrado pelo diagrama a seguir.  
  
 ![Transferência segura usando certificados](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")  
  
 Para obter mais informações sobre como usar um certificado com um serviço, consulte [Trabalhando com Certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) e [Como: Configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md). A tabela a seguir descreve as várias características do cenário.  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Modo de segurança|Transporte|  
|Interoperabilidade|Com clientes e serviços de serviços web existentes.|  
|Autenticação (Servidor)<br /><br /> Autenticação (Cliente)|Sim (usando um certificado SSL)<br /><br /> Sim (usando um certificado X.509)|  
|Integridade dos Dados|Sim|  
|Confidencialidade de dados|Sim|  
|Transporte|HTTPS|  
|Associação|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Configure o Serviço  
 Uma vez que o serviço neste cenário está hospedado no IIS, ele é configurado com um arquivo web.config. A web.config a seguir mostra <xref:System.ServiceModel.WSHttpBinding> como configurar a segurança de transporte e as credenciais do cliente X.509.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <protocolMapping>  
      <add scheme="https" binding="wsHttpBinding" />  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttp binding with Transport security mode and clientCredentialType as Certificate -->  
        <binding>  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>
           <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="configure-the-client"></a>Configure o Cliente  
 O cliente pode ser configurado em código ou em um arquivo app.config. O exemplo a seguir mostra como configurar o cliente em código.  
  
```csharp
// Create the binding.  
var myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.
var ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
var cc =  
   new CalculatorClient(myBinding, ea);  
  
// The client must specify a certificate trusted by the server.  
cc.ClientCredentials.ClientCertificate.SetCertificate(  
    StoreLocation.CurrentUser,  
    StoreName.My,  
    X509FindType.FindBySubjectName,  
    "contoso.com");  
  
// Begin using the client.  
Console.WriteLine(cc.Add(100, 1111));  
//...  
cc.Close();  
```  
  
 Alternativamente, você pode configurar o cliente em um arquivo App.config, conforme mostrado no exemplo a seguir:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address=" https://localhost/CalculatorService/service.svc "
                behaviorConfiguration="endpointCredentialBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="contoso.com"  
                               storeLocation="CurrentUser"  
                               storeName="My"  
                               x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as Certificate -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
  
<startup><supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.0"/></startup></configuration>  
```  
  
## <a name="see-also"></a>Confira também

- [Visão geral da segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Modelo de segurança para a malha do aplicativo do Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
