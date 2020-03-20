---
title: Subsistema de confiança
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: b226eed9218207cde99add61ef1f3eb64b459009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184299"
---
# <a name="trusted-subsystem"></a>Subsistema de confiança
Um cliente acessa um ou mais serviços web que são distribuídos em uma rede. Os serviços web são projetados para que o acesso a recursos adicionais (como bancos de dados ou outros serviços web) seja encapsulado na lógica de negócios do serviço Web. Esses recursos devem ser protegidos contra acesso não autorizado. A ilustração a seguir mostra um processo de subsistema confiável.  
  
 ![Subsistema confiável](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")  
  
 As seguintes etapas descrevem o processo de subsistema confiável como ilustrado:  
  
1. O cliente envia uma solicitação ao subsistema confiável, juntamente com credenciais.  
  
2. O subsistema confiável autentica e autoriza o usuário.  
  
3. O subsistema confiável envia uma mensagem de solicitação para o recurso remoto. Essa solicitação é acompanhada pelas credenciais do subsistema confiável (ou da conta de serviço a qual o processo de subsistema confiável está sendo executado).  
  
4. O recurso back-end autentica e autoriza o subsistema confiável. Em seguida, processa a solicitação e emite uma resposta ao subsistema confiável.  
  
5. O subsistema confiável processa a resposta e emite sua própria resposta ao cliente.  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Modo de segurança|Mensagem|  
|Interoperabilidade|Somente a Windows Communication Foundation (WCF).|  
|Autenticação (serviço)|O serviço de token de segurança autentica e autoriza clientes.|  
|Autenticação (cliente)|O subsistema confiável autentica o cliente e o recurso autentica o serviço confiável do subsistema.|  
|Integridade|Sim|  
|Confidencialidade|Sim|  
|Transporte|HTTP entre cliente e o serviço de subsistema confiável.<br /><br /> Net. TCP entre serviço de subsistema confiável e o recurso (serviço back-end).|  
|Associação|<xref:System.ServiceModel.WSHttpBinding><xref:System.ServiceModel.NetTcpBinding> [e \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|  
  
## <a name="resource-back-end-service"></a>Recurso (serviço back-end)  
  
### <a name="code"></a>Código  
 O código a seguir mostra como criar um ponto final de serviço para o recurso, que usa segurança de transporte sobre o protocolo de transporte TCP.  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a>Configuração  
 A configuração a seguir configura o mesmo ponto final usando a configuração.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.BackendService"  
               behaviorConfiguration="BackendServiceBehavior">  
        <endpoint address="net.tcp://localhost.com:8001/BackendService"  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="BackendServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, BackendService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="trusted-subsystem"></a>Subsistema de confiança  
  
### <a name="code"></a>Código  
 O código a seguir mostra como criar um ponto final de serviço para o subsistema confiável que usa a segurança de mensagens sobre o protocolo HTTP e um nome de usuário e senha para autenticação.  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 O código a seguir mostra um serviço em um subsistema confiável que se comunica com um serviço de back-end usando segurança de transporte através do protocolo de transporte TCP.  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a>Configuração  
 A configuração a seguir configura o mesmo ponto final usando a configuração. Observe as duas ligações: Uma segura o serviço hospedado no subsistema confiável e o outro se comunica entre o subsistema confiável e o serviço de back-end.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.FacadeService"  
               behaviorConfiguration="FacadeServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/FacadeService"/>  
          </baseAddresses>  
        </host>  
        <endpoint address="http://localhost:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <client>  
      <endpoint name=""
                address="net.tcp://contoso.com:8001/BackendService"  
                binding="customBinding"  
                bindingConfiguration="ClientBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
      <customBinding>  
        <binding name="ClientBinding">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="FacadeServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                storeLocation="LocalMachine"  
                                storeName="My"  
                                x509FindType="FindBySubjectName" />  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, FacadeService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Cliente  
  
### <a name="code"></a>Código  
 O código a seguir mostra como criar o cliente que se comunica com o subsistema confiável usando a segurança da mensagem através do protocolo HTTP e um nome de usuário e senha para autenticação.  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a>Configuração  
 O código a seguir configura o cliente para usar a segurança da mensagem sobre o protocolo HTTP e um nome de usuário e senha para autenticação. O nome de usuário e a senha só podem ser especificados usando código (não é configurável).  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <client>  
        <endpoint name=""
                  address="http://www.cohowinery.com:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientUserNameBehavior"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientUserNameBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- [Visão geral da segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Modelo de segurança para a malha do aplicativo do Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
