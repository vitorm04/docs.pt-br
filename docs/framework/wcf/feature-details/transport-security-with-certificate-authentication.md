---
title: Segurança de transporte com autenticação de certificado
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
author: BrucePerlerMS
ms.openlocfilehash: 42de15daef7b18e7422bae836128356f37c1f03d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47421145"
---
# <a name="transport-security-with-certificate-authentication"></a>Segurança de transporte com autenticação de certificado
Este tópico discute usando certificados X.509 para autenticação de cliente e servidor ao usar a segurança de transporte. Para obter mais informações sobre os certificados X.509, confira [Certificados de chave pública X.509](https://msdn.microsoft.com/library/bb540819\(VS.85\).aspx). Certificados devem ser emitidos por uma autoridade de certificação, que é geralmente um emissor de terceiros de certificados. Em um domínio do Windows Server, Active Directory Certificate Services pode ser usado para emitir certificados para computadores cliente no domínio. Para obter mais informações, consulte [serviços de certificados do Windows 2008 R2](https://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409). Nesse cenário, o serviço está hospedado em serviços de informações da Internet (IIS) que é configurado com Secure Sockets Layer (SSL). O serviço está configurado com um certificado SSL (X.509) para permitir que os clientes verificar a identidade do servidor. O cliente também é configurado com um certificado X.509 que permite que o serviço verificar a identidade do cliente. O certificado do servidor deve ser confiável pelo cliente e o certificado do cliente deve ser confiável pelo servidor. A mecânica real de como o serviço e o cliente verifica a identidade um do outro está além do escopo deste tópico. Para obter mais informações, consulte [Assinatura Digital na Wikipédia](https://go.microsoft.com/fwlink/?LinkId=253157).  
  
 Esse cenário implementa um padrão de mensagem de solicitação/resposta, conforme ilustrado pelo diagrama a seguir.  
  
 ![Transferência segura usando certificados](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")  
  
 Para obter mais informações sobre como usar um certificado com um serviço, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) e [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md). A tabela a seguir descreve várias características do cenário.  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Modo de segurança|Transporte|  
|Interoperabilidade|Com serviços e clientes de serviço Web existentes.|  
|Autenticação (servidor)<br /><br /> Autenticação (cliente)|Sim (usando um certificado SSL)<br /><br /> Sim (usando um certificado x. 509)|  
|Integridade de dados|Sim|  
|Confidencialidade de dados|Sim|  
|Transporte|HTTPS|  
|Associação|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Configurar o serviço  
 Uma vez que o serviço nesse cenário é hospedado no IIS, ele é configurado com um arquivo Web. config. O Web. config seguinte mostra como configurar o <xref:System.ServiceModel.WSHttpBinding> usar segurança de transporte e as credenciais do cliente x. 509.  
  
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
  
## <a name="configure-the-client"></a>Configurar o cliente  
 O cliente pode ser configurado no código ou em um arquivo App. config. O exemplo a seguir mostra como configurar o cliente no código.  
  
```vb  
// Create the binding.  
WSHttpBinding myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name   
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.   
EndpointAddress ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator   
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
CalculatorClient cc =  
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
  
 Como alternativa, você pode configurar o cliente em um arquivo App. config, conforme mostrado no exemplo a seguir:  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Modelo de segurança do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
